---
title: "Tầng 1: AI Harness & Memory Architecture"
aliases:
  - Harness and Memory MOC
  - AI Harness Overview
tags:
  - agent-course
  - building-agents
  - harness
  - memory
  - moc
type: moc
created: 2026-09-20
updated: 2026-09-27
---

# 🛠️ AI HARNESS & MEMORY ARCHITECTURE

Thư mục này dành riêng để lưu trữ các tài liệu nghiên cứu và thực hành chuyên sâu về **AI Harness** (bộ khung phần mềm điều khiển ứng dụng bọc ngoài LLM Core), nghệ thuật **Quản trị Ngữ cảnh (Context Window Management)** và kiến trúc **Hệ thống Bộ nhớ Đa tầng (Multi-tier Memory Systems)**.

---

## 📌 Khái Niệm Cốt Lõi Về Harness & Memory

* **AI Harness là gì?** Là toàn bộ lớp phần mềm đứng trung gian giữa người dùng và mô hình ngôn ngữ (LLM Core). Harness chịu trách nhiệm nạp System Prompt, gắn Chat History, tiêm User Memory, quản lý cấp quyền và cung cấp Tools/Connectors.
* **Tài liệu tham chiếu dẫn nhập:**
  * [Kiến trúc & Tiến hóa của các hệ thống AI Chat](../00_ai_chat_systems_and_prompt_engineering.md): Tổng quan về 4 tầng tiến hóa từ Prompting đến Loop Engineering.
  * [Tìm kiếm Ngữ nghĩa & Tái xếp hạng](../../01-research-and-foundations/03-semantic-search/01_semantic_search_and_reranking.md): Hạ tầng truy xuất nền tảng cho Semantic Memory và RAG.

---

## 📂 Danh Mục Tài Liệu Chuyên Sâu

* 📖 **[01_harness_architecture.md - Giải Phẫu Kiến Trúc AI Harness, Sandboxing & An Ninh Tác Tử](./01_harness_architecture.md)**:
  * Phân tách ranh giới giữa Lõi tĩnh (LLM Core) và Khung điều khiển có trạng thái (Harness).
  * Giải phẫu 5 phân hệ phần mềm: Ingestion, Context Assembly, LLM Gateway, Tool Dispatcher và Guardrails.
  * Vòng đời trạng thái (Session Lifecycle, Checkpointing & Forking).
  * Phòng chống **Indirect Prompt Injection** qua Content Delimiters và Network Egress Filtering.
  * Kiến trúc **OS Sandboxing** (Docker, gVisor, bubblewrap, Linux namespaces) và làm sạch biến môi trường bí mật.
  * So sánh kiến trúc Harness thực chiến: CLI Agent vs IDE Agent vs Web Chatbot.
  * Code mẫu Python xây dựng Mini-Harness với Tool Dispatcher.

* 📖 **[02_context_management.md - Quản Trị Cửa Sổ Ngữ Cảnh, Bệnh Lý & Cô Lập (Quarantine)](./02_context_management.md)**:
  * Chẩn đoán 3 bệnh lý tử huyệt: **Context Poisoning** (thiên kiến Aarav/Leo, dữ liệu cũ), **Context Decay** (pha loãng token, quên lỗi ban đầu), **Context Starvation** (thiếu dữ liệu).
  * Cuộc cách mạng **Retrieval-Augmented Generation (RAG)**: Triết lý thi mở sách, triệt tiêu ảo giác và cập nhật dữ liệu tươi mới.
  * Kỹ thuật **Context Pruning** (Lọc trùng lặp, Rule-based, Semantic) và **Context Summarization** (Rolling summary).
  * Kiến trúc **Context Quarantine**: Phân vùng phòng ban (Finance vs HR vs Legal), bảo vệ dữ liệu PII/PHI và ngăn chặn lây lan lỗi.
  * Thực nghiệm so sánh: Khung 6 cấu phần **Supercharged Context Engineering** trong viết email chuyên nghiệp.

* 📖 **[03_memory_systems.md - Kiến Trúc Bộ Nhớ Đa Tầng Cho AI Agents](./03_memory_systems.md)**:
  * **Cơ sở tâm lý học nhận thức:** Mô hình Atkinson-Shiffrin, phân loại ký ức Endel Tulving (Episodic vs Semantic vs Procedural), và định luật suy giảm hàm mũ **Ebbinghaus Forgetting Curve** $R(t) = \exp(-t/S)$.
  * **Mô hình 4 phân tầng:** Sliding Working Context, Core Memory (L1 Cache ghim User & Agent Persona), Episodic Stream (dòng sự kiện tự truyện) và Semantic/Graph Store.
  * **Kiến trúc MemGPT / Letta:** Quản trị bộ nhớ ảo kiểu Hệ Điều Hành (OS Virtual Memory Paging), cảnh báo tràn trang ngầm (Silent Interrupts), và 4 công cụ tự quản trị bộ nhớ (`core_memory_replace`, `archival_memory_insert`).
  * **Mô hình Generative Agents (Stanford & Google):** Memory Stream, hàm chấm điểm truy xuất kết hợp 3 trọng số $\text{Score}(m) = \alpha_{\text{rec}} R + \alpha_{\text{imp}} I + \alpha_{\text{rel}} S$, cơ chế phản tỉnh đệ quy (Recursive Reflection) và lập kế hoạch phân cấp.
  * **Temporal Knowledge Graph Memory (Zep, Mem0):** Khắc phục lỗi của Vector-only Memory, đồ thị bi-temporal có tem thời gian hiệu lực `[valid_from, valid_to]` và tự động giải quyết mâu thuẫn (Contradiction Resolution).
  * **Thực hành Code:** Triển khai `HierarchicalCognitiveMemoryEngine` Python hoàn chỉnh với tính điểm Ebbinghaus, Reflection worker tự động và Core Memory tool.

* 📖 **[04_agent_runtime_parameters_and_prompt_caching.md - Tham Số Vận Hành Tác Tử & Tối Ưu Hóa Prompt Caching](./04_agent_runtime_parameters_and_prompt_caching.md)**:
  * **Bản chất kinh tế vòng lặp:** Khủng hoảng Prefill Computation $O(N^2)$, bài toán bùng nổ token tích lũy và giải pháp Prefix Caching (RadixTree).
  * **Giải phẫu Caching:** Phân biệt Hardware KV-Cache vs API-Level Prompt Caching; chu trình Cache Write, Cache Hit (giảm 90% chi phí, TTFT từ 3.5s xuống 0.25s), Cache Miss và chính sách Eviction (LRU/TTL).
  * **Quy tắc Bất biến Tiền tố (Static Prefix Invariance):** Kiến trúc đóng gói System $\to$ Tools Schema $\to$ Few-shot $\to$ Cache Breakpoint $\to$ Dynamic History; 5 bẫy gây rách cache kinh điển và cách phòng hộ.
  * **Giải phẫu toàn tập Siêu tham số suy luận:** Toán học `temperature` ($\tau \to 0$ cho Tool Calling/JSON vs $\tau = 0.6$ cho Planning), `top_p`, `max_tokens` (chống Truncation Disaster), `stop_sequences`, hiểm họa của `presence_penalty` / `frequency_penalty` đối với cú pháp AST/JSON, và `seed` tất định.
  * **Hệ thống đo lường hiệu năng:** TTFT, TPOT, TPS, Cache Hit Rate ($H_{\text{rate}} \ge 85\%$) và Gantt Waterfall một bước nhận thức.
  * **Thực hành Python:** Kịch bản cấu hình Anthropic Ephemeral Breakpoint, OpenAI Deterministic Payload và lớp `ProductionAgentRuntimeEngine` đo lường hiệu năng thời gian thực.

---

## 🔗 Điều Hướng Nhanh
* Trở về mục lục Trụ cột 3: [🛠️ Trụ Cột 3: Building Agents](../README.md)
* Trở về trang chủ Vault: [🏠 Vault Home MOC](../../README.md)
* Xem bản đồ Canvas: [🗺️ Mở Visual Canvas](../../Agent-Course-Overview.canvas)
