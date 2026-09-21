# 🔌 MODEL CONTEXT PROTOCOL (MCP) & TOOLS

Thư mục này dành riêng để lưu trữ ghi chú, hướng dẫn cài đặt và các ví dụ thực hành về **Model Context Protocol (MCP)** - giao thức chuẩn mở do Anthropic khởi xướng để kết nối AI với các công cụ và nguồn dữ liệu bên ngoài.

---

## 📌 Khái Niệm Cốt Lõi Về MCP

* **MCP là gì?** Là một giao thức tiêu chuẩn (tương tự như HTTP cho web hay LSP cho code editors) cho phép các LLM Client (như Claude Desktop, Antigravity, Cursor, Cline) kết nối một cách nhất quán tới các MCP Servers bất kỳ (Database, Filesystem, GitHub, Slack, API bên ngoài).
* **3 Cột Trụ Của MCP:**
  1. **Tools:** Các hàm/chức năng mà AI có thể gọi để thực thi hành động (chạy lệnh, gọi API, ghi file).
  2. **Resources:** Dữ liệu thụ động mà AI có thể đọc (tệp văn bản, schema CSDL, tài liệu API).
  3. **Prompts:** Các mẫu câu lệnh được định nghĩa trước bởi server để người dùng hoặc client kích hoạt luồng xử lý.

---

## 📋 Cấu Trúc Ghi Chú Dự Kiến Cho Khóa Học Mới

```text
03-building-agents/tools-and-mcp/
├── README.md                 # Trang mục lục này
├── 01_mcp_architecture.md    # Giao thức MCP (Host, Client, Server, Transport: stdio / SSE)
├── 02_using_mcp_servers.md   # Cấu hình và sử dụng các MCP Server phổ biến
├── 03_building_mcp_server.md # Hướng dẫn viết MCP Server tùy chỉnh (Python / TypeScript SDK)
└── 04_mcp_best_practices.md  # Quản lý bảo mật, timeout, error handling trong MCP
```
