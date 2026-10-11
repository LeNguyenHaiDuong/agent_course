---
title: "Tầng 2: Model Context Protocol (MCP) & Tools"
aliases:
  - Tools and MCP MOC
  - MCP Overview
tags:
  - agent-course
  - building-agents
  - mcp
  - tools
  - moc
type: moc
created: 2026-09-20
updated: 2026-09-27
---

# 🔌 MODEL CONTEXT PROTOCOL (MCP) & TOOLS

Thư mục này dành riêng để lưu trữ ghi chú, tài liệu kiến trúc và hướng dẫn thực hành toàn diện về **Model Context Protocol (MCP)** - giao thức chuẩn mở do Anthropic khởi xướng để kết nối AI với các công cụ và nguồn dữ liệu bên ngoài.

---

## 📌 Khái Niệm Cốt Lõi Về MCP

* **MCP là gì?** Là một giao thức tiêu chuẩn (tương tự như HTTP cho web hay LSP cho code editors) cho phép các LLM Client (như Claude Desktop, Antigravity, Cursor, Cline) kết nối một cách nhất quán tới các MCP Servers bất kỳ (Database, Filesystem, GitHub, Slack, API bên ngoài).
* **3 Cột Trụ Của MCP:**
  1. **Tools:** Các hàm/chức năng mà AI có thể gọi để thực thi hành động (chạy lệnh, gọi API, ghi file).
  2. **Resources:** Dữ liệu thụ động mà AI có thể đọc (tệp văn bản, schema CSDL, tài liệu API).
  3. **Prompts:** Các mẫu câu lệnh được định nghĩa trước bởi server để người dùng hoặc client kích hoạt luồng xử lý.

---

## 📂 Danh Mục Tài Liệu Chuyên Sâu

* 📖 **[[01_mcp_architecture|01_mcp_architecture.md - Cẩm Nang Toàn Diện Giao Thức Model Context Protocol (MCP)]]**:
  * **Kiến trúc & Lý thuyết:** Bài toán phân mảnh $N \times M$, mô hình tam giác Host - Client - Server, 3 cấu phần nguyên thủy (Tools, Resources, Prompts).
  * **Tầng truyền tải & Wire Protocol:** So sánh chi tiết `stdio` (cục bộ) vs `SSE` (từ xa qua HTTP), giải phẫu gói tin JSON-RPC 2.0 (Request, Response, Error codes).
  * **Vòng đời & Thương thảo:** Handshake `initialize`, Ping/keep-alive, thông báo động `list_changed` và cơ chế Reverse Sampling (`sampling/createMessage`).
  * **Thực hành viết MCP Server:** Hướng dẫn code Python hoàn chỉnh sử dụng thư viện chính thức `mcp` và `FastMCP`.
  * **Hệ sinh thái & Cấu hình Đa Server:** Hướng dẫn tích hợp đồng thời Filesystem, GitHub, PostgreSQL, SQLite, Brave Search trong `claude_desktop_config.json`.
  * **Bảo mật & Vận hành:** Mô hình 3 lớp (Roots Whitelist, Human-in-the-Loop, OS Sandboxing), quản lý Timeout và Auto-restart.

* 📖 **[[02_constrained_decoding_and_structured_outputs|02_constrained_decoding_and_structured_outputs.md - Constrained Decoding & Grammar-Guided Structured Outputs]]**:
  * **Khủng hoảng gãy vỡ Structured Output:** Tại sao Prompting và Post-Validation Retry là giải pháp thất bại; xác suất lỗi lũy tiến trong Agent Pipeline đa bước.
  * **Cơ chế Logit Masking:** Toán học tầng Unembedding $\mathbf{W}_U$ và Softmax; áp đặt mặt nạ nhị phân $\mathbf{M}_t$ tại bước sinh token để cưỡng chế $100\%$ hợp lệ ngữ pháp.
  * **Trường phái FSM vs CFG:** Chuyển dịch Regex sang Finite State Machine (Outlines) và Context-Free Grammars sang Pushdown Automata (llama.cpp GBNF).
  * **Tăng tốc Jump-Forward Decoding:** Cơ chế "nhảy cóc" của SGLang tự động chèn token tĩnh, tăng tốc sinh JSON gấp $2\times - 5\times$.
  * **Thực hành Code:** Xây dựng Banking Tool Dispatcher với Outlines và Pydantic schema loại trừ $100\%$ lỗi kiểu.

* 📖 [**07_fullstack_agent_mern_architecture.md - Kiến Trúc Ứng Dụng Tác Tử Toàn Diện Với MERN Stack**](../07_fullstack_agent_mern_architecture.md):
  * **TypeScript MCP Client:** Hướng dẫn kết nối `@modelcontextprotocol/sdk` trong backend Node.js / Express để gọi MCP Servers qua `stdio` và `SSE`.
  * **Fullstack Integration:** Tích hợp MCP Tools với MongoDB Atlas Vector Search và giao diện React Streaming ReAct UI có xác nhận Human-in-the-Loop.

---

## 🔗 Điều Hướng Nhanh
* Trở về mục lục Trụ cột 3: [[03-building-agents/README|🛠️ Trụ Cột 3: Building Agents]]
* Trở về trang chủ Vault: [[README|🏠 Vault Home MOC]]
* Xem bản đồ Canvas: [[Agent-Course-Overview.canvas|🗺️ Mở Visual Canvas]]
