---
title: "Mô-đun 02: Model Context Protocol (MCP) & Tools"
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
updated: 2026-10-18
---

# 🔌 MÔ-ĐUN 02: MODEL CONTEXT PROTOCOL (MCP) & TOOLS

Thư mục này dành riêng để lưu trữ ghi chú, tài liệu kiến trúc và hướng dẫn thực hành toàn diện về **Model Context Protocol (MCP)** - giao thức chuẩn mở do Anthropic khởi xướng để kết nối AI với các công cụ và nguồn dữ liệu bên ngoài, cùng các kỹ thuật điều khiển cấu trúc đầu ra (**Constrained Decoding**).

---

## 📌 Khái Niệm Cốt Lõi Về MCP & Tool Calling

* **MCP là gì?** Là một giao thức tiêu chuẩn (tương tự như HTTP cho web hay LSP cho code editors) cho phép các LLM Client (như Claude Desktop, Antigravity, Cursor, Cline) kết nối một cách nhất quán tới các MCP Servers bất kỳ (Database, Filesystem, GitHub, Slack, API bên ngoài).
* **3 Cột Trụ Của MCP:**
  1. **Tools:** Các hàm/chức năng mà AI có thể gọi để thực thi hành động (chạy lệnh, gọi API, ghi file).
  2. **Resources:** Dữ liệu thụ động mà AI có thể đọc (tệp văn bản, schema CSDL, tài liệu API).
  3. **Prompts:** Các mẫu câu lệnh được định nghĩa trước bởi server để người dùng hoặc client kích hoạt luồng xử lý.

---

## 📂 Danh Mục Tài Liệu Theo Thứ Tự Đọc

* 📖 **[01_mcp_architecture.md - Cẩm Nang Toàn Diện Giao Thức Model Context Protocol (MCP)](./01_mcp_architecture.md)**:
  * **Kiến trúc & Lý thuyết:** Bài toán phân mảnh $N \times M$, mô hình tam giác Host - Client - Server, 3 cấu phần nguyên thủy (Tools, Resources, Prompts).
  * **Tầng truyền tải & Wire Protocol:** So sánh chi tiết `stdio` (cục bộ) vs `SSE` (từ xa qua HTTP), giải phẫu gói tin JSON-RPC 2.0 (Request, Response, Error codes).
  * **Vòng đời & Thương thảo:** Handshake `initialize`, Ping/keep-alive, thông báo động `list_changed` và cơ chế Reverse Sampling (`sampling/createMessage`).
  * **Thực hành viết MCP Server:** Hướng dẫn code Python hoàn chỉnh sử dụng thư viện chính thức `mcp` và `FastMCP`.
  * **Hệ sinh thái & Cấu hình Đa Server:** Hướng dẫn tích hợp đồng thời Filesystem, GitHub, PostgreSQL, SQLite, Brave Search trong `claude_desktop_config.json`.
  * **Bảo mật & Vận hành:** Mô hình 3 lớp (Roots Whitelist, Human-in-the-Loop, OS Sandboxing), quản lý Timeout và Auto-restart.

* 📖 **[02_constrained_decoding_and_structured_outputs.md - Constrained Decoding & Grammar-Guided Structured Outputs](./02_constrained_decoding_and_structured_outputs.md)**:
  * **Khủng hoảng gãy vỡ Structured Output:** Tại sao Prompting và Post-Validation Retry là giải pháp thất bại; xác suất lỗi lũy tiến trong Agent Pipeline đa bước.
  * **Cơ chế Logit Masking:** Toán học tầng Unembedding $\mathbf{W}_U$ và Softmax; áp đặt mặt nạ nhị phân $\mathbf{M}_t$ tại bước sinh token để cưỡng chế $100\%$ hợp lệ ngữ pháp.
  * **Trường phái FSM vs CFG:** Chuyển dịch Regex sang Finite State Machine (Outlines) và Context-Free Grammars sang Pushdown Automata (llama.cpp GBNF).
  * **Tăng tốc Jump-Forward Decoding:** Cơ chế "nhảy cóc" của SGLang tự động chèn token tĩnh, tăng tốc sinh JSON gấp $2\times - 5\times$.
  * **Thực hành Code:** Xây dựng Banking Tool Dispatcher với Outlines và Pydantic schema loại trừ $100\%$ lỗi kiểu.

* 📖 **[03_dynamic_tool_retrieval_and_tool_rag.md - Dynamic Tool Retrieval & Tool-RAG](./03_dynamic_tool_retrieval_and_tool_rag.md)**:
  * **Nút thắt Tool Storm & Quá tải Context:** Tại sao nhồi 500+ schemas làm tăng chi phí và gây ảo giác chọn nhầm tool.
  * **Kiến trúc Two-Stage Tool-RAG:** Biểu diễn ngữ nghĩa Tool Card (Summary, Parameters, Few-shot queries), chỉ mục Hybrid (Dense Vector + BM25) kết hợp Reciprocal Rank Fusion (RRF).
  * **Hierarchical Tool Namespaces:** Định tuyến 2 cấp (Domain Classifier $\to$ Fine-grained Retriever), phân quyền RBAC tại cổng nạp công cụ.
  * **Thực hành Code:** Xây dựng `DynamicToolRetrieverEngine` bằng Python trích xuất Top-3 Tools nạp động cho LLM.

* 📖 **[04_sandboxed_tool_execution_wasm_and_microvm.md - Sandboxed Tool Execution: Wasm & MicroVMs](./04_sandboxed_tool_execution_wasm_and_microvm.md)**:
  * **Hiểm họa chạy mã không kiểm soát:** Rò rỉ dữ liệu qua Indirect Prompt Injection, vòng lặp vô tận cạn kiệt tài nguyên máy chủ.
  * **4 tầng cô lập:** Process Subprocess $\to$ Linux Containers $\to$ MicroVMs (AWS Firecracker) $\to$ WebAssembly (Wasm/WASI).
  * **Bảo mật Capability-Based:** Từ chối mặc định (Default Deny), cấp quyền tường minh từng tệp/socket.
  * **Giới hạn tài nguyên nghiêm ngặt:** Khống chế CPU Watchdog, Hard Cap RAM, và tự tiêu hủy sau khi hoàn thành (Ephemerality).
  * **Thực hành Code:** Bộ khung `LightweightToolSandbox` bằng Python ngăn chặn mã độc hệ thống và tấn công DoS.

---

## 🔗 Liên Kết Mở Rộng
* Ứng dụng MCP trong Fullstack: [04_fullstack_agent_mern_architecture.md](../06-governance-and-enterprise-delivery/04_fullstack_agent_mern_architecture.md) (kết nối `@modelcontextprotocol/sdk` trong backend Node.js / Express).

---

## 🔗 Điều Hướng Nhanh
* Quay lại Mô-đun trước: [🛠️ Mô-đun 01: AI Harness & Memory Architecture](../01-harness-and-memory/README.md)
* Chuyển sang Mô-đun kế tiếp: [🔄 Mô-đun 03: Loop & Multi-Agent Engineering](../03-loop-and-multi-agent-engineering/README.md)
* Trở về mục lục Trụ cột 3: [🛠️ Trụ Cột 3: Building Agents](../README.md)
* Trở về trang chủ Vault: [🏠 Vault Home MOC](../../README.md)
