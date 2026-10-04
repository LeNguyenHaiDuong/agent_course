---
title: "Kiến Trúc Giao Thức Model Context Protocol (MCP)"
aliases:
  - Model Context Protocol Architecture
  - MCP Fundamentals
  - Anthropic MCP Specification
  - Giao thức MCP
tags:
  - agent-course
  - building-agents
  - mcp
  - tools
type: note
created: 2026-09-27
updated: 2026-09-27
---

# 🔌 KIẾN TRÚC GIAO THỨC MODEL CONTEXT PROTOCOL (MCP)
## Chuẩn Hóa Kết Nối Giữa Mô Hình Ngôn Ngữ, Dữ Liệu Ngoại Vi & Công Cụ Tác Tử

---

## 📑 MỤC LỤC
1. [Bối Cảnh Lịch Sử & Bài Toán Tích Hợp $N \times M$](#1-bối-cảnh-lịch-sử--bài-toán-tích-hợp-n-times-m)
2. [Kiến Trúc Tổng Thể: Tam Giác Tác Tử (Host - Client - Server)](#2-kiến-trúc-tổng-thể-tam-giác-tác-tử-host---client---server)
3. [Ba Cột Trụ Nguyên Thủy (The Three Core Primitives)](#3-ba-cột-trụ-nguyên-thủy-the-three-core-primitives)
4. [Tầng Truyền Tải & Định Dạng Tin Nhắn (Transport & Wire Protocol)](#4-tầng-truyền-tải--định-dạng-tin-nhắn-transport--wire-protocol)
5. [Vòng Đời Phiên Làm Việc & Cơ Chế Thương Thảo (Lifecycle & Negotiation)](#5-vòng-đời-phiên-làm-việc--cơ-chế-thương-thảo-lifecycle--negotiation)
6. [Giải Phẫu Gói Tin Thực Tế (JSON-RPC 2.0 Payloads Deep Dive)](#6-giải-phẫu-gói-tin-thực-tế-json-rpc-20-payloads-deep-dive)
7. [Thực Chiến: Xây Dựng MCP Server Với FastMCP (Python)](#7-thực-chiến-xây-dựng-mcp-server-với-fastmcp-python)
8. [Mô Hình Bảo Mật, Sandboxing & Human-in-the-Loop](#8-mô-hình-bảo-mật-sandboxing--human-in-the-loop)
9. [Bản Đồ Liên Kết Kiến Thức (Knowledge Graph Links)](#9-bản-đồ-liên-kết-kiến-thức-knowledge-graph-links)

---

## 1. BỐI CẢNH LỊCH SỬ & BÀI TOÁN TÍCH HỢP $N \times M$

### 1.1. Cơn Khủng Hoảng Phân Mảnh Trước Tháng 11/2024
Như đã khảo sát trong bài [[ai_chat_systems_and_prompt_engineering|Kiến trúc & Tiến hóa của các hệ thống AI Chat]], bản chất cốt lõi của Large Language Model là **tĩnh (static)** và **bị cô lập (isolated)** trong không gian tham số đóng băng tại thời điểm hoàn tất pre-training. Để LLM có thể thực hiện công việc thực tế, chúng ta phải trang bị cho mô hình khả năng tương tác với thế giới thực thông qua các công cụ ngoài: truy vấn cơ sở dữ liệu SQL, đọc tệp tin cục bộ, gọi Git, tìm kiếm Web, hay gửi tin nhắn Slack.

Tuy nhiên, trong giai đoạn 2023 – giữa 2024, cộng đồng AI rơi vào tình trạng phân mảnh nghiêm trọng được gọi là **Bài toán bế tắc tích hợp $N \times M$ (The $N \times M$ Integration Bottleneck)**:

```mermaid
flowchart LR
    subgraph Clients["N Nền Tảng AI / LLM Hosts"]
        C1["Claude Desktop"]
        C2["Cursor / VSCode IDE"]
        C3["Antigravity / Custom Agent"]
        C4["LangChain / LlamaIndex App"]
    end

    subgraph Tools["M Nguồn Dữ Liệu & Công Cụ"]
        T1["PostgreSQL DB"]
        T2["Local Filesystem"]
        T3["GitHub API"]
        T4["Brave / Google Search"]
        T5["Slack / Discord"]
    end

    C1 -.->|"Custom API code"| T1
    C1 -.->|"Custom Parser"| T2
    C2 -.->|"Extension glue"| T1
    C2 -.->|"Language plugin"| T3
    C3 -.->|"Ad-hoc tool class"| T4
    C4 -.->|"Bespoke wrapper"| T5

    style Clients fill:#f0f4f8,stroke:#3b82f6,stroke-width:2px,color:#000000
    style Tools fill:#fef3c7,stroke:#f59e0b,stroke-width:2px,color:#000000
```

* Nếu có $N$ nền tảng AI Client và $M$ dịch vụ dữ liệu/công cụ, cộng đồng kỹ sư phải viết và duy trì $N \times M$ đoạn mã kết nối (glue code) riêng biệt.
* Mỗi framework (OpenAI Assistant API, LangChain Tool, LlamaIndex Reader, AutoGPT Tool) định nghĩa schema tham số, cơ chế xử lý lỗi, xác thực và chu kỳ sống hoàn toàn khác nhau.
* Khi nhà phát triển cập nhật logic kết nối Postgres, họ phải sửa code ở $N$ thư viện khác nhau.

### 1.2. Sự Ra Đời Của Model Context Protocol (MCP)
Vào ngày **25 tháng 11 năm 2024**, **Anthropic** chính thức công bố và mã nguồn mở **Model Context Protocol (MCP)**. 

> [!important] Triết Lý Cốt Lõi Của MCP
> Tương tự như cách **LSP (Language Server Protocol)** của Microsoft đã giải quyết bài toán $N \times M$ giữa các trình biên tập mã nguồn (VS Code, Neovim, Emacs) và các ngôn ngữ lập trình (Rust, Python, Go), **MCP đóng vai trò như một cổng USB-C phổ quát cho các hệ thống AI**:
> * **Viết một lần, chạy ở mọi nơi:** Một nhà phát triển chỉ cần xây dựng một MCP Server (ví dụ: `postgres-mcp-server`), và server đó lập tức tương thích tự động với mọi MCP Host (Claude Desktop, Antigravity, Cursor, Zed, Cline, v.v.).
> * **Bài toán giảm độ phức tạp:** Chuyển đổi bài toán phức tạp từ tích số $\mathcal{O}(N \times M)$ xuống dạng tổng tuyến tính $\mathcal{O}(N + M)$.

```mermaid
flowchart LR
    subgraph Hosts["N Nền Tảng AI (MCP Hosts)"]
        H1["Claude Desktop"]
        H2["Antigravity / Agent CLI"]
        H3["IDE / Cursor / Zed"]
    end

    MCP_BUS{{"Chuẩn Giao Thức Mở MCP\n(JSON-RPC 2.0 qua stdio / SSE)"}}

    subgraph Servers["M Dịch Vụ (MCP Servers)"]
        S1["PostgreSQL Server"]
        S2["Filesystem Server"]
        S3["GitHub Server"]
        S4["Web Search Server"]
    end

    H1 ===> MCP_BUS
    H2 ===> MCP_BUS
    H3 ===> MCP_BUS

    MCP_BUS ===> S1
    MCP_BUS ===> S2
    MCP_BUS ===> S3
    MCP_BUS ===> S4

    style MCP_BUS fill:#ecfdf5,stroke:#10b981,stroke-width:3px,color:#000000
```

---

## 2. KIẾN TRÚC TỔNG THỂ: TAM GIÁC TÁC TỬ (HOST - CLIENT - SERVER)

Trong cấu trúc MCP, tương tác không diễn ra trực tiếp giữa Model và API ngoài mà thông qua mô hình phân tầng chặt chẽ gồm ba thực thể:

```mermaid
sequenceDiagram
    autonumber
    actor User as Người dùng
    participant Host as MCP Host (App UI + LLM Engine)
    participant Client as MCP Client (Internal Coordinator)
    participant Server as MCP Server (External Process)
    participant Target as External World (DB, OS, API)

    User->>Host: Yêu cầu: "Liệt kê 5 đơn hàng mới nhất trong DB"
    Host->>Client: Yêu cầu lấy danh sách công cụ hiện có
    Client->>Server: tools/list (JSON-RPC Request)
    Server-->>Client: Trả về danh sách Tool Schema (JSON-RPC Response)
    Client-->>Host: Nạp Tool Schemas vào Context Window
    Host->>Host: LLM suy luận và phát sinh Tool Call (Function Calling)
    Host->>User: (Human-in-the-Loop) Xin cấp quyền thực thi query DB?
    User-->>Host: Đồng ý (Approve)
    Host->>Client: Điều phối lệnh gọi Tool
    Client->>Server: tools/call (tên: "query_sql", params: "SELECT...")
    Server->>Target: Thực thi câu lệnh SQL trực tiếp
    Target-->>Server: Dữ liệu bảng kết quả
    Server-->>Client: tool_result (Dữ liệu dạng text / JSON)
    Client-->>Host: Đưa kết quả vào Context Window
    Host->>Host: LLM đọc kết quả và sinh câu trả lời tự nhiên
    Host-->>User: "Dưới đây là danh sách 5 đơn hàng mới nhất: ..."
```

### 2.1. Phân Định Trách Nhiệm Từng Thành Phần
1. **MCP Host (Ứng Dụng Chủ):**
   * Là ứng dụng cấp cao tương tác trực tiếp với người dùng và nắm giữ kết nối với LLM (ví dụ: Claude Desktop, Antigravity IDE, Cline).
   * Chịu trách nhiệm bảo mật cấp cao nhất: Quản lý quyền hạn người dùng (Human-in-the-loop authorization), hiển thị giao diện đồ họa, lưu trữ lịch sử trò chuyện.
   * Host có thể khởi tạo đồng thời **nhiều MCP Clients**.
2. **MCP Client (Điều Phối Viên Nội Bộ):**
   * Là thành phần nằm bên trong Host, duy trì kết nối **1-kèm-1 (1:1 connection)** độc quyền với một MCP Server cụ thể.
   * Thực hiện chuyển đổi giao thức: Gửi các yêu cầu JSON-RPC 2.0 (Discovery, Execution) và nhận phản hồi từ Server.
   * Lắng nghe các thông báo (Notifications) thời gian thực từ Server (ví dụ khi danh sách tài nguyên thay đổi).
3. **MCP Server (Máy Chủ Năng Lực):**
   * Là một tiến trình (process) độc lập, gọn nhẹ, chạy trên máy cục bộ hoặc máy chủ từ xa.
   * Chuyên biệt hóa: Một server chỉ nên đảm nhận một phạm vi nhiệm vụ (ví dụ: `filesystem-server`, `brave-search-server`, `git-server`).
   * Phơi bày 3 loại năng lực nguyên thủy ra ngoài: **Tools**, **Resources**, và **Prompts**.

---

## 3. BA CỘT TRỤ NGUYÊN THỦY (THE THREE CORE PRIMITIVES)

Toàn bộ năng lực mà một MCP Server cung cấp cho AI được chuẩn hóa vào đúng 3 cấu phần nguyên thủy (Primitives):

```mermaid
classDiagram
    class MCP_Server {
        +Tools: Executable Functions
        +Resources: Passive Data Sources
        +Prompts: Guided Workflows
    }
    class Tools {
        +name: string
        +description: string
        +inputSchema: JSONSchema
        +execute(args): Result
    }
    class Resources {
        +uri: UniformResourceIdentifier
        +name: string
        +mimeType: string
        +read(): Content
    }
    class Prompts {
        +name: string
        +description: string
        +arguments: ArgumentList
        +getMessages(): MessageArray
    }
    MCP_Server *-- Tools
    MCP_Server *-- Resources
    MCP_Server *-- Prompts
```

### 3.1. Tools (Công Cụ Thực Thi - Active Functions)
* **Bản chất:** Là các hàm có thể thực thi do LLM chủ động quyết định gọi. Tools được thiết kế để tạo ra các **hiệu ứng phụ (side effects)** lên thế giới thực: ghi tệp tin, xóa dữ liệu, gửi email, gọi API thanh toán, chạy script.
* **Cơ chế hoạt động:**
  1. Server đăng ký với Client qua phương thức `tools/list`, cung cấp tên, mô tả chi tiết và `inputSchema` chuẩn JSON Schema.
  2. Client nạp schema này vào Context Window của LLM.
  3. Khi LLM quyết định cần gọi công cụ, nó sinh ra một JSON payload chứa tên hàm và tham số.
  4. Client chuyển tiếp lệnh gọi tới Server thông qua phương thức `tools/call`.
  5. Server thực thi hàm nội bộ và trả về kết quả cấu trúc `content: [{type: "text", text: ...}]`.

### 3.2. Resources (Tài Nguyên Dữ Liệu - Passive Context)
* **Bản chất:** Là dữ liệu thụ động chỉ đọc (Read-Only) được Server phơi bày để Host có thể nạp trực tiếp vào ngữ cảnh của LLM. Tương tự như việc tải một tài liệu PDF hay mở một tệp văn bản.
* **Định danh bằng URI (Uniform Resource Identifier):**
  * Tệp cục bộ: `file:///home/user/project/schema.sql`
  * Bản ghi cơ sở dữ liệu: `postgres://db.production/customers/1092`
  * Logs hệ thống thời gian thực: `system-logs://cluster-alpha/nginx/error`
* **Resource Templates:** Hỗ trợ cú pháp tham số hóa URI theo RFC 6570:
  * Ví dụ: `github://repos/{owner}/{repo}/issues/{issue_number}`
* **Cơ chế Đăng Ký (Subscriptions):** Client có thể đăng ký theo dõi một Resource (`resources/subscribe`). Khi tệp tin hoặc dữ liệu thay đổi trên đĩa, Server tự động phát thông báo `notifications/resources/updated` để Client cập nhật tức thì vào bộ nhớ AI.

### 3.3. Prompts (Khuôn Mẫu Tương Tác - Guided Workflows)
* **Bản chất:** Các mẫu câu lệnh và kịch bản tương tác có cấu trúc do Server định nghĩa sẵn, giúp người dùng hoặc Host dễ dàng kích hoạt các quy trình công việc phức tạp.
* **Ứng dụng:**
  * Slash commands (ví dụ: `/debug-error`, `/git-commit-review`, `/analyze-sql-slow-query`).
  * Tích hợp sẵn vai trò (Roles) và chuỗi suy luận (Chain-of-Thought) chuẩn mực theo các kỹ thuật khảo sát trong [[advanced_prompt_engineering_techniques|Kỹ thuật Prompt Nâng cao]].

### 3.4. Bảng So Sánh Chi Tiết 3 Primitives Của MCP

| Đặc tính so sánh | Tools (Công cụ) | Resources (Tài nguyên) | Prompts (Khuôn mẫu) |
| :--- | :--- | :--- | :--- |
| **Mục đích chính** | Thực hiện hành động & tương tác với thế giới ngoài | Cung cấp dữ liệu ngữ cảnh làm nền tảng | Định hướng hành vi & tạo khung quy trình |
| **Chủ thể kích hoạt** | Do **LLM** tự động quyết định gọi | Do **Người dùng** chọn hoặc Client nạp tự động | Do **Người dùng** kích hoạt (Slash Command) |
| **Tác động phụ (Side effects)**| **Có** (Ghi đĩa, gọi API, cập nhật DB) | **Không** (Chỉ đọc nội dung dữ liệu) | **Không** (Chỉ sinh văn bản hướng dẫn) |
| **Định dạng phơi bày** | JSON Schema tham số hàm | Chuẩn URI Scheme (`scheme://path`) | Danh sách tham số đầu vào (Arguments) |
| **Yêu cầu phê duyệt** | Thường yêu cầu xác thực người dùng | Thường cho phép đọc trực tiếp | Không cần phê duyệt |

---

## 4. TẦNG TRUYỀN TẢI & ĐỊNH DẠNG TIN NHẮN (TRANSPORT & WIRE PROTOCOL)

Giao thức MCP được xây dựng hoàn toàn dựa trên tiêu chuẩn **JSON-RPC 2.0 (RFC 7159)**, cho phép đóng gói các thông điệp có cấu trúc chặt chẽ, đa nền tảng và dễ dàng debug.

### 4.1. Cấu Trúc Khung Tin Nhắn JSON-RPC 2.0

Mọi tin nhắn lưu thông giữa Client và Server bắt buộc phải tuân theo một trong 4 cấu trúc định dạng sau:

#### A. Yêu Cầu (Request) - Cần Phản Hồi
```json
{
  "jsonrpc": "2.0",
  "id": 101,
  "method": "tools/call",
  "params": {
    "name": "read_file",
    "arguments": {
      "path": "/var/log/syslog"
    }
  }
}
```

#### B. Phản Hồi Thành Công (Successful Response)
```json
{
  "jsonrpc": "2.0",
  "id": 101,
  "result": {
    "content": [
      {
        "type": "text",
        "text": "Oct 24 10:00:01 kernel: CPU0: Temperature normal"
      }
    ],
    "isError": false
  }
}
```

#### C. Thông Báo Một Chiều (Notification) - Không Cần Phản Hồi, Không Có Trường `id`
```json
{
  "jsonrpc": "2.0",
  "method": "notifications/resources/updated",
  "params": {
    "uri": "file:///var/log/syslog"
  }
}
```

#### D. Lỗi Chuẩn Hóa (Error Response)
```json
{
  "jsonrpc": "2.0",
  "id": 101,
  "error": {
    "code": -32602,
    "message": "Invalid params: 'path' argument must be an absolute path"
  }
}
```

> [!note] Bảng Mã Lỗi Chuẩn Trong MCP (JSON-RPC Standard Error Codes)
> * `-32700`: Parse error (Gói JSON gửi lên bị lỗi cú pháp)
> * `-32600`: Invalid Request (Cấu trúc gói tin không đúng chuẩn JSON-RPC)
> * `-32601`: Method not found (Phương thức được gọi không tồn tại trên Server)
> * `-32602`: Invalid params (Tham số truyền vào không khớp với `inputSchema`)
> * `-32603`: Internal error (Lỗi phát sinh nội bộ trong mã nguồn của Server)

---

### 4.2. Hai Tầng Truyền Tải Tiêu Chuẩn (Standard Transports)

Đặc tả MCP định nghĩa hai cơ chế truyền tải dữ liệu cốt lõi:

```mermaid
flowchart TD
    subgraph LocalTransport["1. Standard Input/Output (stdio Transport)"]
        H_local["Host Process\n(Client)"]
        subgraph Subprocess["Tiến Trình Con Được Khởi Tạo Cục Bộ"]
            S_local["MCP Server Process\n(Node.js / Python / Binary)"]
        end
        H_local -->|"Ghi dòng JSON-RPC\\n"| InPipe["Standard Input (stdin)"] --> S_local
        S_local -->|"Ghi dòng JSON-RPC\\n"| OutPipe["Standard Output (stdout)"] --> H_local
        S_local -.->|"Nhật ký gỡ lỗi (Logs thô)"| ErrPipe["Standard Error (stderr)"] -.-> H_local
    end

    subgraph RemoteTransport["2. Server-Sent Events over HTTP (SSE Transport)"]
        H_remote["Remote Client\n(Browser / Desktop Host)"]
        S_remote["Remote MCP Server\n(Cloud Container / VPS)"]
        H_remote -->|"1. GET /sse (Mở kết nối duy trì stream)"| S_remote
        S_remote -->>|"2. SSE Stream: endpoint event & messages"| H_remote
        H_remote -->|"3. POST /message?sessionId=xyz (JSON-RPC Body)"| S_remote
    end
```

#### So Sánh Chuyên Sâu stdio vs SSE

| Tiêu chí | `stdio` Transport | `SSE` over HTTP Transport |
| :--- | :--- | :--- |
| **Vị trí triển khai** | Cục bộ trên cùng một máy (Local machine) | Máy chủ từ xa, hạ tầng đám mây (Cloud, K8s) |
| **Cách thức giao tiếp** | File Descriptors chuẩn của HĐH (`stdin`, `stdout`) | Giao thức HTTP/1.1 hoặc HTTP/2 |
| **Độ trễ (Latency)** | Cực thấp ($\approx 0.1\text{ ms}$, Zero-network overhead) | Phụ thuộc độ trễ mạng Internet ($20 - 200\text{ ms}$) |
| **Bảo mật mạng** | Cách ly hoàn toàn, không mở cổng mạng (No open ports) | Bắt buộc phải cấu hình TLS (HTTPS), Auth Token, CORS |
| **Quản lý tiến trình** | Host tự spawn và tự kill tiến trình con | Server chạy độc lập dưới dạng daemon/container |
| **Kênh ghi log** | Dùng `stderr` để in log debug mà không làm hỏng JSON | Dùng giao thức MCP Logging notifications (`logging/setLevel`) |

---

## 5. VÒNG ĐỜI PHIÊN LÀM VIỆC & CƠ CHẾ THƯƠNG THẢO (LIFECYCLE & NEGOTIATION)

Một phiên làm việc MCP hoàn chỉnh trải qua 3 giai đoạn chặt chẽ:

```mermaid
sequenceDiagram
    autonumber
    participant C as MCP Client
    participant S as MCP Server

    rect rgb(238, 242, 255)
    Note over C,S: GIAI ĐOẠN 1: KHỞI TẠO VÀ THƯƠNG THẢO NĂNG LỰC
    C->>S: Request: initialize (protocolVersion, capabilities, clientInfo)
    S-->>C: Response: (protocolVersion, capabilities, serverInfo)
    C->>S: Notification: notifications/initialized
    end

    rect rgb(240, 253, 244)
    Note over C,S: GIAI ĐOẠN 2: THỰC THI & PHÁT HIỆN ĐỘNG (OPERATION)
    C->>S: Request: tools/list
    S-->>C: Response: Danh sách Tools & Schemas
    C->>S: Request: resources/list
    S-->>C: Response: Danh sách Resources & URI Patterns
    C->>S: Request: tools/call (name, arguments)
    S-->>C: Response: Kết quả thực thi
    Note over S: Server có cập nhật công cụ mới
    S-->>C: Notification: notifications/tools/list_changed
    C->>S: Request: tools/list (Cập nhật lại danh sách)
    S-->>C: Response: Danh sách công cụ mới
    end

    rect rgb(254, 242, 242)
    Note over C,S: GIAI ĐOẠN 3: ĐÓNG PHIÊN LÀM VIỆC
    C->>S: Đóng luồng stdin (stdio) hoặc hủy kết nối SSE
    S->>S: Giải phóng tài nguyên, đóng DB connection, Exit 0
    end
```

### 5.1. Cơ Chế Bắt Tay Ban Đầu (The Handshake)
1. **Client gửi yêu cầu `initialize`:**
   * Thông báo phiên bản giao thức đang hỗ trợ (ví dụ: `2024-11-05`).
   * Khai báo khả năng của Client (Capabilities): Có hỗ trợ Roots list không? Có hỗ trợ Sampling không?
2. **Server phản hồi thông tin `initialize`:**
   * Trả về phiên bản tương thích cao nhất.
   * Khai báo danh mục năng lực hỗ trợ: `tools`, `resources`, `prompts`, `logging`.
3. **Client xác nhận bằng `notifications/initialized`:**
   * Khi thông báo này được gửi đi, cả hai bên chính thức bước vào trạng thái hoạt động bình thường. Server không được phép gửi bất kỳ yêu cầu nghiệp vụ nào trước mốc này.

### 5.2. Kỹ Thuật Đảo Ngược Suy Luận (Reverse Sampling)
Một tính năng mang tính đột phá của MCP là **Sampling**:
* Thông thường, chỉ có Host yêu cầu Server xử lý.
* Nhưng với Sampling, **MCP Server có thể chủ động yêu cầu Host gọi ngược lại LLM** (`sampling/createMessage`).
* **Ví dụ ứng dụng:** Một MCP Server chuyên phân tích mã nguồn có thể tự gửi một đoạn code phức tạp lên LLM thông qua Host để nhờ tóm tắt, trước khi trả về kết quả cuối cùng cho Client. Điều này cho phép xây dựng các Agent tự hành lồng nhau (Nested Agentic Workflows) mà Server không cần phải tự cấu hình API Key riêng của OpenAI hay Anthropic.

---

## 6. GIẢI PHẪU GÓI TIN THỰC TẾ (JSON-RPC 2.0 PAYLOADS DEEP DIVE)

Hãy cùng "soi kính hiển vi" vào các gói tin truyền qua đường ống `stdio` giữa Antigravity/Claude Desktop và một Server:

### 6.1. Bắt Tay Khởi Tạo (Handshake)

**1. Client $\rightarrow$ Server (`initialize`):**
```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "method": "initialize",
  "params": {
    "protocolVersion": "2024-11-05",
    "capabilities": {
      "roots": { "listChanged": true },
      "sampling": {}
    },
    "clientInfo": {
      "name": "AntigravityHost",
      "version": "2.4.0"
    }
  }
}
```

**2. Server $\rightarrow$ Client (`result`):**
```json
{
  "jsonrpc": "2.0",
  "id": 1,
  "result": {
    "protocolVersion": "2024-11-05",
    "capabilities": {
      "tools": { "listChanged": true },
      "resources": { "subscribe": true, "listChanged": true }
    },
    "serverInfo": {
      "name": "DatabaseCommander",
      "version": "1.0.0"
    }
  }
}
```

---

### 6.2. Liệt Kê và Gọi Công Cụ (`tools/list` & `tools/call`)

**1. Khảo sát công cụ (`tools/list`):**
```json
{
  "jsonrpc": "2.0",
  "id": 2,
  "method": "tools/list"
}
```

**2. Server trả về Schema định nghĩa:**
```json
{
  "jsonrpc": "2.0",
  "id": 2,
  "result": {
    "tools": [
      {
        "name": "execute_sql_query",
        "description": "Thực thi câu truy vấn SQL SELECT an toàn trên database analytics và trả về kết quả dạng bảng.",
        "inputSchema": {
          "type": "object",
          "properties": {
            "query": {
              "type": "string",
              "description": "Câu lệnh SQL hợp lệ. Chỉ cho phép các lệnh SELECT."
            },
            "limit": {
              "type": "integer",
              "default": 10,
              "description": "Số lượng bản ghi tối đa trả về."
            }
          },
          "required": ["query"]
        }
      }
    ]
  }
}
```

**3. Client kích hoạt thực thi (`tools/call`):**
```json
{
  "jsonrpc": "2.0",
  "id": 3,
  "method": "tools/call",
  "params": {
    "name": "execute_sql_query",
    "arguments": {
      "query": "SELECT user_id, email, signup_date FROM users ORDER BY signup_date DESC",
      "limit": 2
    }
  }
}
```

**4. Server gửi kết quả (`result`):**
```json
{
  "jsonrpc": "2.0",
  "id": 3,
  "result": {
    "content": [
      {
        "type": "text",
        "text": "[{\"user_id\": 849, \"email\": \"alice@example.com\", \"signup_date\": \"2026-09-26\"}, {\"user_id\": 850, \"email\": \"bob@example.com\", \"signup_date\": \"2026-09-27\"}]"
      }
    ],
    "isError": false
  }
}
```

---

## 7. THỰC CHIẾN: XÂY DỰNG MCP SERVER VỚI FASTMCP (PYTHON)

Để đưa lý thuyết vào thực tiễn, chúng ta sử dụng thư viện chính thức của Anthropic `mcp` với mô-đun cao cấp `FastMCP` trong Python.

### 7.1. Cài Đặt Thư Viện
```bash
pip install "mcp[cli]"
```

### 7.2. Viết Mã Nguồn Server (`vault_helper_server.py`)

File này cung cấp cả **Tool** (tính toán thống kê), **Resource** (đọc tệp ghi chú Obsidian) và **Prompt** (mẫu đánh giá bài viết):

```python
"""
Vault Helper MCP Server
Ví dụ triển khai MCP Server chuẩn hóa cho khóa học Agent Course.
"""
import os
from mcp.server.fastmcp import FastMCP

# 1. Khởi tạo MCP Server với tên định danh
mcp = FastMCP("VaultHelperServer")

WORKSPACE_DIR = "/home/duongle/agent_course"

# ==============================================================================
# CỘT TRỤ 1: TOOLS (Hành động có tham số và logic tính toán)
# ==============================================================================
@mcp.tool()
def count_vault_words(pillar_folder: str) -> str:
    """
    Đếm tổng số từ của tất cả các bài viết trong một trụ cột cụ thể.
    
    Args:
        pillar_folder: Tên thư mục trụ cột (ví dụ: '01-research-and-foundations')
    """
    target_path = os.path.join(WORKSPACE_DIR, pillar_folder)
    if not os.path.exists(target_path):
        return f"Lỗi: Thư mục '{pillar_folder}' không tồn tại trong workspace."
    
    total_words = 0
    file_count = 0
    for root, _, files in os.walk(target_path):
        for f in files:
            if f.endswith(".md"):
                file_count += 1
                with open(os.path.join(root, f), "r", encoding="utf-8") as fp:
                    content = fp.read()
                    total_words += len(content.split())
                    
    return f"Trụ cột '{pillar_folder}': Tổng cộng {file_count} tệp markdown, {total_words:,} từ."

# ==============================================================================
# CỘT TRỤ 2: RESOURCES (Dữ liệu tĩnh định danh qua URI Scheme)
# ==============================================================================
@mcp.resource("vault://overview/curriculum")
def get_curriculum_structure() -> str:
    """Trả về sơ đồ lộ trình học tập 3 trụ cột của Agent Course."""
    return """
    === LỘ TRÌNH AGENT COURSE ===
    1. Trụ Cột 1: Research & Foundations (Neural Networks, LLM Internals, Semantic Search)
    2. Trụ Cột 2: Prompt & Context Engineering (CoT, ToT, DSP, Token Budgeting)
    3. Trụ Cột 3: Building Agents (Harness, MCP, Loop Engineering, ReAct)
    """

# ==============================================================================
# CỘT TRỤ 3: PROMPTS (Mẫu câu lệnh định hướng quy trình)
# ==============================================================================
@mcp.prompt()
def review_markdown_lesson(topic_name: str) -> str:
    """Mẫu hướng dẫn AI đánh giá chất lượng học thuật của một bài học mới."""
    return f"""
    Bạn là một Giáo sư Khoa học Máy tính hàng đầu chuyên về Autonomous AI Agents.
    Hãy kiểm tra kỹ lưỡng nội dung bài viết về đề tài: '{topic_name}'.
    
    Tiêu chí đánh giá bắt buộc:
    1. Tính chính xác toán học (LaTeX) và sơ đồ kiến trúc (Mermaid).
    2. Tuân thủ chuẩn Obsidian Flavored Markdown (Wikilinks, Callouts, YAML Frontmatter).
    3. Phân tích sâu các ca biên (edge cases) và cơ chế bảo mật trong thực tế.
    """

if __name__ == "__main__":
    # Mặc định FastMCP chạy qua stdio Transport
    mcp.run(transport="stdio")
```

### 7.3. Cấu Hình Tích Hợp Vào MCP Host (Claude Desktop / Antigravity)

Để Client nhận diện Server vừa viết, ta chỉ cần thêm cấu hình JSON vào tệp `claude_desktop_config.json`:

```json
{
  "mcpServers": {
    "vault-helper": {
      "command": "python",
      "args": [
        "/home/duongle/agent_course/03-building-agents/02-tools-and-mcp/vault_helper_server.py"
      ],
      "env": {
        "PYTHONUNBUFFERED": "1"
      }
    }
  }
}
```

Ngay khi khởi động ứng dụng, Host sẽ ngầm khởi chạy tiến trình Python con, thực hiện handshake `initialize`, và các icon Tool/Resource sẽ lập tức xuất hiện sẵn sàng cho LLM kích hoạt.

### 7.4. Hệ Sinh Thái MCP Server Sẵn Có & Cấu Hình Đa Server Thực Chiến

Thay vì phải tự viết mọi thứ, cộng đồng Anthropic và mã nguồn mở đã cung cấp sẵn một hệ sinh thái các MCP Server tiêu chuẩn:

| MCP Server | Giao Thức & Runtime | Năng Lực Cung Cấp Cho Agent | Biến Môi Trường Cần Thiết |
| :--- | :--- | :--- | :--- |
| **Filesystem** | Node.js (`npx`) qua `stdio` | Đọc, ghi, liệt kê tệp, quản lý thư mục trong phạm vi cho phép | Các đường dẫn thư mục được whitelist |
| **GitHub** | Node.js (`npx`) qua `stdio` | Tạo Pull Request, đọc Issue, tìm kiếm code, fork repository | `GITHUB_PERSONAL_ACCESS_TOKEN` |
| **PostgreSQL** | Node.js (`npx`) qua `stdio` | Đọc Schema CSDL, chạy truy vấn SQL SELECT an toàn | `POSTGRES_CONNECTION_STRING` |
| **SQLite** | Python (`uvx`) qua `stdio` | Truy vấn cơ sở dữ liệu SQLite cục bộ | Đường dẫn file `.db` |
| **Brave Search** | Node.js (`npx`) qua `stdio` | Tìm kiếm Web theo thời gian thực để cập nhật dữ liệu tươi | `BRAVE_API_KEY` |
| **Memory** | Node.js (`npx`) qua `stdio` | Quản trị Knowledge Graph bền vững cho cá nhân hóa | Lưu trữ file JSON cục bộ |

#### Cấu Hình Kết Nối Đa Server (Multi-Server Production Setup):
Bạn có thể ghép nối đồng thời nhiều MCP Server vào một tệp cấu hình duy nhất để biến Agent thành một trợ lý toàn năng:

```json
{
  "mcpServers": {
    "filesystem": {
      "command": "npx",
      "args": [
        "-y",
        "@modelcontextprotocol/server-filesystem",
        "/home/duongle/agent_course"
      ]
    },
    "github": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"],
      "env": {
        "GITHUB_PERSONAL_ACCESS_TOKEN": "ghp_xxxxxxxxxxxxxxxxxxxx"
      }
    },
    "postgres": {
      "command": "npx",
      "args": [
        "-y",
        "@modelcontextprotocol/server-postgres",
        "postgresql://postgres:secret@localhost:5432/analytics_db"
      ]
    },
    "brave-search": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-brave-search"],
      "env": {
        "BRAVE_API_KEY": "BSA_xxxxxxxxxxxxxxxxxxxx"
      }
    }
  }
}
```

> [!tip] Best Practices Vận Hành MCP Trong Production
> 1. **Kiểm soát Timeout:** Luôn cấu hình timeout (mặc định 60 giây) cho các cuộc gọi `tools/call` để tránh tình trạng một tiến trình con bị treo làm đóng băng toàn bộ giao diện Host.
> 2. **Tự Động Khôi Phục Tiến Trình (Auto-restart):** Host cần bắt sự kiện `process.on('exit')` của tiến trình stdio để tự khởi động lại server nếu bị crash.
> 3. **Giới Hạn Tần Suất (Rate Limiting):** Đối với các server gọi API trả phí bên ngoài (như Brave Search hoặc GitHub API), cần thiết lập bộ đếm token/request để tránh bị khóa tài khoản hoặc phát sinh chi phí đột biến.

---

## 8. MÔ HÌNH BẢO MẬT, SANDBOXING & HUMAN-IN-THE-LOOP

Khi trao cho mô hình ngôn ngữ khả năng thực thi lệnh thông qua MCP, chúng ta cũng mở ra các bề mặt tấn công mới (Attack Surfaces). Một kiến trúc MCP an toàn bắt buộc phải áp dụng các nguyên tắc sau:

```mermaid
flowchart TD
    subgraph SecurityShield["Mô Hình Bảo Mật 3 Lớp Của MCP"]
        L1["Lớp 1: Kiểm Soát Ranh Giới (Roots & URI Whitelisting)"]
        L2["Lớp 2: Con Người Trong Vòng Lặp (Human-in-the-Loop Approval)"]
        L3["Lớp 3: Cô Lập Tiến Trình & Môi Trường (OS Sandboxing)"]
    end

    UntrustedLLM["Yêu cầu thực thi từ LLM"] --> L1
    L1 -->|"Hợp lệ theo Root"| L2
    L2 -->|"Người dùng xác nhận OK"| L3
    L3 -->|"Thực thi an toàn"| OS["Hệ Thống Tệp / Mạng / CSDL"]

    style SecurityShield fill:#fffbeb,stroke:#d97706,stroke-width:2px,color:#000000
```

### 8.1. Kiểm Soát Ranh Giới (Roots Boundary Control)
* Giao thức MCP tích hợp phương thức `roots/list`. Host sẽ gửi cho Server danh sách đường dẫn thư mục gốc mà Server **được phép** truy cập (ví dụ: chỉ được phép đọc ghi trong `/home/user/workspace/`).
* Server có trách nhiệm tự kiểm tra và từ chối các hành vi Directory Traversal (như `../../etc/passwd`).

### 8.2. Human-in-the-Loop (Phê Duyệt Tác Vụ Nhạy Cảm)
* Các hành động đọc dữ liệu thụ động (Resources) có thể được tự động hóa.
* **Tất cả các công cụ có hiệu ứng phụ (Destructive Tools)** như xóa tệp, thực thi shell command, sửa đổi cấu hình hạ tầng **phải được Host chặn lại** để hiển thị hộp thoại xác nhận cho người dùng (Prompt to Approve).

### 8.3. Bảo Vệ Bí Mật Môi Trường (Environment Secrets Isolation)
* Không bao giờ truyền trực tiếp API Keys hoặc Database Passwords trong nội dung của LLM Prompt.
* Khóa bí mật phải được tiêm trực tiếp vào biến môi trường (`env`) của tiến trình MCP Server khi Host khởi tạo tiến trình con.

---

## 9. BẢN ĐỒ LIÊN KẾT KIẾN THỨC (KNOWLEDGE GRAPH LINKS)

Tài liệu này là viên gạch nền móng đầu tiên của Tầng 2 trong Trụ cột 3. Hãy tiếp tục nghiên cứu các mối liên kết chặt chẽ trong Vault:

* 🔙 **Nền tảng tiền đề:**
  * [[ai_chat_systems_and_prompt_engineering|Kiến Trúc & Tiến Hóa Của Các Hệ Thống AI Chat]]: Tìm hiểu về tầng Harness và tại sao LLM cần công cụ ngoài.
  * [[advanced_prompt_engineering_techniques|Kỹ Thuật Prompt Nâng Cao]]: Cách tối ưu hóa prompt templates và chuỗi suy luận trong MCP Prompts.
  * [[semantic_search_and_reranking|Tìm Kiếm Ngữ Nghĩa & Tái Xếp Hạng]]: Công nghệ truy xuất tài nguyên phía sau các MCP Resource Servers phức tạp.
* 🔜 **Bài học thực hành kế tiếp trong Trụ cột 3:**
  * [[02_constrained_decoding_and_structured_outputs|Constrained Decoding & Structured Outputs]]: Bảo đảm cú pháp Tool Calling ở tầng Logit Masking.
  * [[01_loop_fundamentals|Nền Tảng Loop Engineering]]: Cách kết hợp MCP Tools vào các vòng lặp tự trị **ReAct** và **Plan-and-Execute**.
* 🏠 **Điều hướng:**
  * Trở về trang mục lục Trụ cột 3: [[03-building-agents/README|🛠️ Trụ Cột 3: Building Agents]]
  * Trở về trang chủ Vault: [[README|🏠 Vault Home MOC]]
  * Mở bản đồ trực quan: [[Agent-Course-Overview.canvas|🗺️ Visual Canvas]]
