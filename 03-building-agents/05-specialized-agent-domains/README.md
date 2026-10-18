---
title: "Mô-đun 05: Specialized Agent Domains"
aliases:
  - Specialized Agent Domains MOC
  - Code and GUI Agents Overview
tags:
  - agent-course
  - building-agents
  - code-intelligence
  - multimodal-gui
  - browser-agents
  - moc
type: moc
created: 2026-10-18
updated: 2026-10-18
---

# 🎯 MÔ-ĐUN 05: SPECIALIZED AGENT DOMAINS

Thư mục này dành riêng để nghiên cứu và thực hành chuyên sâu về các miền ứng dụng tác tử kỹ thuật cao (Specialized Domains): từ **Trí thông minh Repository & Đồ thị mã nguồn (Code Graphs)**, **Bộ nhớ đa phiên & Delta Caching**, cho đến các tác tử tương tác giao diện trực quan (**Multimodal GUI / Computer Use**) và tự động hóa trình duyệt web (**Browser Agents & AXTree**).

---

## 📌 Khái Niệm Cốt Lõi Về Các Miền Tác Tử Chuyên Biệt

* **Vượt ra ngoài Chatbot thông thường:** Các tác tử trong mô-đun này không chỉ xử lý ngôn ngữ tự nhiên mà phải làm việc với các hệ thống phức tạp: Cây cú pháp trừu tượng (AST), Đồ thị cuộc gọi (Call Graphs), Hệ thống băm Git Merkle, Tọa độ màn hình hệ điều hành $(x, y)$, và Cây trợ năng trình duyệt (Accessibility Tree).
* **Định vị & Grounding:** Khả năng ánh xạ suy luận trừu tượng của LLM thành các hành động chính xác trên thế giới phần mềm thực.

---

## 📂 Danh Mục Tài Liệu Theo Thứ Tự Đọc

* 📖 **[01_code_graphs_and_repository_intelligence.md - Đồ Thị Mã Nguồn, AST & Trí Thông Minh Repository Toàn Cục](./01_code_graphs_and_repository_intelligence.md)**:
  * Sự sụp đổ của Vector RAG ngây thơ khi áp dụng vào Codebases lớn: Mất mát cấu trúc phân cấp, không hiểu phạm vi (Scope) và đứt gãy luồng phụ thuộc.
  * Phân tích cú pháp với **Tree-sitter**: Khái niệm Cây cú pháp cụ thể (CST) vs Cây cú pháp trừu tượng (AST).
  * Chuẩn **SCIP (Source Code Intelligence Protocol)** và LSIF: Indexing biểu tượng code đa ngôn ngữ.
  * Xây dựng Đồ thị tri thức mã nguồn (**Code Knowledge Graph**): Call Graph, Class Inheritance, Data Flow.
  * Thuật toán **PageRank trên Code Graph** (kỹ thuật của Aider): Xếp hạng tầm quan trọng của các file và hàm để dựng Repo Map nén $< 2,000$ tokens.
  * Thực hành Python: Triển khai engine phân tích phụ thuộc mã nguồn và sinh Repo Map tự động.

* 📖 **[02_cross_session_memory_and_delta_caching.md - Bộ Nhớ Đa Phiên, Git Delta Caching & Tái Cấu Trúc Ngữ Cảnh](./02_cross_session_memory_and_delta_caching.md)**:
  * Bản chất bài toán Session Boundary: Đứt gãy ngữ cảnh khi khởi động session mới.
  * Kiến trúc **Memory Banks** dạng Markdown (`activeContext.md`, `progress.md`, `techContext.md`, `systemPatterns.md`) và file quy ước (`.cursorrules`, `CLAUDE.md`).
  * Cơ chế **Git Merkle Tree Delta Caching**: Sử dụng mã băm cây Git để phát hiện chính xác các file bị sửa đổi ($\Delta F$), tái sử dụng 97% cache AST và embeddings cũ.
  * Kỹ thuật **Session Compaction**: Nén lịch sử hội thoại dài thành các Semantic Checkpoints có cấu trúc, lưu trữ `failed_hypotheses` để ngăn lặp lại sai lầm.
  * Thực hành Python: Triển khai `CrossSessionMemoryManager` tự động sync Git delta và nạp prompt khởi tạo tinh gọn $< 1,500$ tokens.

* 📖 **[03_multimodal_gui_and_computer_use.md - Tác Tử Đa Phương Thức Điều Khiển GUI & Máy Tính](./03_multimodal_gui_and_computer_use.md)**:
  * Sự chuyển dịch từ API-driven Agent sang Visual-driven OS Agent.
  * Chu trình nhận thức thị giác: Viewport Screenshot $\to$ Visual Grounding $\to$ Coordinate Translation $\to$ OS Mouse/Keyboard Dispatch.
  * Kỹ thuật đánh dấu **Set-of-Mark (SoM)** và **Visual Prompting**: Nhận diện icon, button không có nhãn văn bản.
  * Benchmark quốc tế: **OSWorld**, **Mind2Web**, **ScreenSpot** và phân tích độ trễ/chi phí.
  * Vấn đề an toàn & Vòng lặp phản hồi: Chống hành vi phá hoại hệ thống (System Destructive Actions), điểm ngắt khẩn cấp (Emergency Kill Switches).
  * Thực hành Python: Xây dựng mini Computer-Use controller tương tác với desktop qua PyAutoGUI / xdotool.

* 📖 **[04_browser_automation_and_web_agents.md - Tác Tử Web, Tự Động Hóa Trình Duyệt & Tương Tác DOM](./04_browser_automation_and_web_agents.md)**:
  * Phân tầng kiến trúc Web Agent: Tách biệt giữa Raw DOM khổng lồ (150k tokens) và Tầng nhận thức tinh gọn.
  * Giải pháp **Accessibility Tree (AXTree)**: Trích xuất vai trò ngữ nghĩa (Role, Name, State) qua CDP, cắt giảm hơn 90% chi phí token so với Raw HTML.
  * **Set-of-Mark Web Grounding**: Tiêm JavaScript gắn nhãn định danh `[data-agent-id]` trực tiếp lên giao diện trình duyệt để LLM click chính xác 100%.
  * Xử lý tính bất định: Dynamic SPA Hydration, MutationObserver, và kỹ thuật ngụy trang Stealth vượt qua rào cản phòng vệ anti-bot (Cloudflare, CAPTCHA).
  * Thực hành Python: Triển khai `PlaywrightWebAgent` tích hợp quét AXTree, SoM overlay và thực thi hành động bất đồng bộ.

* 📖 **[05_symbolic_ai_and_formal_verification.md - Symbolic AI & Ghép Nối LLM Với Bộ Giải Z3 SMT & Lean 4](./05_symbolic_ai_and_formal_verification.md)**:
  * Bản chất xung đột: Xác suất thống kê của LLM (dễ ảo giác) vs. Tính đúng đắn hình thức tuyệt đối (Deductive Verification).
  * Kiến trúc **Neuro-Symbolic** và vòng lặp phản hồi **CEGIS (Counterexample-Guided Inductive Synthesis)**: LLM sinh đặc tả hình thức, Bộ giải SMT kiểm tra và sinh phản ví dụ để Agent tự sửa lỗi.
  * Bộ giải **Z3 SMT Solver**: Các lý thuyết First-Order (Bit-Vectors chống tràn số, Linear Arithmetic, Arrays) áp dụng vào bài toán lập lịch và bảo mật Smart Contracts.
  * Chứng minh hình thức **Lean 4**: Đẳng cấu Curry-Howard ("Chương trình là Chứng minh"), Lean Kernel xác thực thuật toán phần mềm với độ tin cậy $100\%$.
  * Thực hành Python: Triển khai `CloudResourceOptimizationAgent` kết hợp `z3-solver` giải quyết bài toán phân bổ hạ tầng đa ràng buộc.

* 📖 **[06_on_device_and_edge_agents.md - On-Device & Edge Small Agents](./06_on_device_and_edge_agents.md)**:
  * Động lực Edge-First: Bảo mật dữ liệu riêng tư (Zero Cloud Egress), hoạt động ngoại tuyến không cần internet và $0 chi phí token biên.
  * Các dòng SLMs tối ưu cho tác tử: SmolLM2 (1.7B), Qwen-2.5-Coder (1.5B/7B), Phi-3.5-mini (3.8B), LLaMA-3.2 (1B/3B).
  * Ngăn xếp phần cứng: WebGPU trong trình duyệt (WebLLM/Transformers.js), llama.cpp tối ưu hóa Apple Metal/Vulkan, và chip NPU.
  * Kiến trúc định tuyến lai (Hybrid Local-First Escalation): Xử lý 80% tác vụ nhạy cảm tại biên, leo thang 20% bài toán phức tạp lên Cloud.
  * Thực hành Python: Xây dựng `OnDeviceEdgeAgent` gọi các công cụ phần cứng máy khách an toàn.

---

## 🔗 Điều Hướng Nhanh
* Quay lại Mô-đun trước: [📊 Mô-đun 04: Observability, Evals & Cost Optimization](../04-observability-evals-and-cost/README.md)
* Chuyển sang Mô-đun kế tiếp: [🛡️ Mô-đun 06: Governance, Security & Enterprise Delivery](../06-governance-and-enterprise-delivery/README.md)
* Trở về mục lục Trụ cột 3: [🛠️ Trụ Cột 3: Building Agents](../README.md)
* Trở về trang chủ Vault: [🏠 Vault Home MOC](../../README.md)
