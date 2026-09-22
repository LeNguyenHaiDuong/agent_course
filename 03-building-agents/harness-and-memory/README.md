# 🛠️ AI HARNESS & MEMORY ARCHITECTURE

Thư mục này dành riêng để ghi chú cho các khóa học và tài liệu nghiên cứu về **AI Harness** (bộ khung ứng dụng bọc ngoài LLM), quản trị Context Window và cơ chế Memory.

---

## 📌 Khái Niệm Cốt Lõi Về Harness

* **AI Harness là gì?** Là toàn bộ lớp phần mềm đứng trung gian giữa người dùng và mô hình ngôn ngữ (LLM Core). Harness chịu trách nhiệm nạp System Prompt, gắn Chat History, tiêm User Memory, quản lý cấp quyền và cung cấp Tools/Connectors.
* **Tài liệu tham chiếu cốt lõi:**
  * [Kiến trúc & Tiến hóa của các hệ thống AI Chat](../ai_chat_systems_and_prompt_engineering.md)
  * [[semantic_search_and_reranking|Tìm kiếm Ngữ nghĩa (Semantic Search) & Tái xếp hạng (Re-ranking)]]: Hạ tầng truy xuất nền tảng cho Semantic Memory và RAG.

---

## 📋 Cấu Trúc Ghi Chú Dự Kiến Cho Khóa Học Mới

```text
03-building-agents/harness-and-memory/
├── README.md                      # Trang mục lục này
├── 01_harness_architecture.md     # Giải phẫu kiến trúc Harness (CLI, Web, IDE)
├── 02_context_management.md       # Quản trị cửa sổ ngữ cảnh, dọn dẹp Drift
├── 03_memory_systems.md           # Bộ nhớ động, Semantic Memory, RAG cục bộ
└── 04_security_and_sandboxing.md  # Phân quyền tệp, sandbox terminal, xác thực
```
