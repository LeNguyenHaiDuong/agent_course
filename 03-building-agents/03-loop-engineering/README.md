---
title: "Tầng 3: Loop Engineering & Autonomous Agents"
aliases:
  - Loop Engineering MOC
  - Autonomous Agents Loops Overview
tags:
  - agent-course
  - building-agents
  - loop-engineering
  - autonomy
  - moc
type: moc
created: 2026-09-20
updated: 2026-09-27
---

# 🔄 LOOP ENGINEERING & AUTONOMOUS AGENTS

Thư mục này dành riêng để lưu trữ các tài liệu nghiên cứu và thực hành chuyên sâu về **Loop Engineering** (kỹ thuật điều khiển vòng lặp phản hồi) và các kiến trúc tác tử AI tự trị (Autonomous Agents).

---

## 📌 Khái Niệm Cốt Lõi Về Loop Engineering

* **Loop Engineering là gì?** Là việc thiết kế các vòng lặp phản hồi có kiểm soát (Feedback Loops) cho phép mô hình AI tự prompt chính nó, tự quan sát kết quả hành động và tiếp tục lặp lại cho đến khi đạt được tiêu chí hoàn thành mục tiêu mà không cần con người can thiệp thủ công ở từng bước.
* **Tài liệu tham chiếu dẫn nhập:**
  * [[00_ai_chat_systems_and_prompt_engineering|Kiến trúc & Tiến hóa của các hệ thống AI Chat]]: Tổng quan về Tầng 4 - Loop Engineering trong tiến trình phát triển của AI.

---

## 📂 Danh Mục Tài Liệu Chuyên Sâu

* 📖 **[[01_loop_fundamentals|01_loop_fundamentals.md - Nền Tảng Loop Engineering, Circuit Breakers & Kiểm Thử Tác Tử]]**:
  * **Chu trình vòng lặp:** Bước nhảy từ One-Shot sang Recursive Control Loop, chu trình nhận thức OODA 5 bước.
  * **Kiểm soát an toàn:** 4 Tầng điều kiện dừng bắt buộc (Stopping Criteria), bẫy vòng lặp vô tận (Thrashing) và cơ chế ngắt mạch an toàn (Circuit Breakers).
  * **Máy trạng thái & Code mẫu:** Mô hình State Graph / FSM và triển khai `AutonomousLoopEngine` Python.
  * **Đo lường & Kiểm thử Agent:** Các benchmark quốc tế (SWE-bench, GAIA, WebArena), phương pháp **LLM-as-a-Judge** với Rubric Scoring và hệ thống giám sát vận hành (Tracing với OpenTelemetry/LangSmith).

* 📖 **[[02_react_and_planning|02_react_and_planning.md - Các Mô Hình Vòng Lặp Cốt Lõi: ReAct, Plan-and-Execute & Evaluator-Optimizer]]**:
  * **ReAct (Reason + Act):** Chuỗi Thought $\rightarrow$ Action $\rightarrow$ Observation tương tác thời gian thực với môi trường.
  * **Plan-and-Execute:** Tách biệt Planner (mô hình lớn lập kế hoạch dài hạn) và Step Executor (thực thi vi mô), kỹ thuật Dynamic Replanning giúp tiết kiệm tới 80% token.
  * **Evaluator-Optimizer (Generator-Critic):** Vòng lặp phản biện và tự hoàn thiện code/bài viết dựa trên tiêu chí chấm điểm khắt khe.
  * Bảng so sánh định lượng và ma trận đánh đổi về Token, Latency, Complexity và Fault Recovery.
  * Code mẫu Python mô hình Generator - Critic tự sửa lỗi code.

* 📖 **[[03_multi_agent_teams|03_multi_agent_teams.md - Kiến Trúc Đội Ngũ Đa Tác Tử]]**:
  * Giới hạn nhận thức của tác tử đơn lẻ: Cognitive Overload và Context Poisoning.
  * Nguyên lý phân công lao động nhận thức (Division of Cognitive Labor).
  * 3 Mô hình cộng tác: **Orchestrator-Worker** (Fan-out / Fan-in song song), **Supervisor Hierarchy** (Phân cấp quản trị sâu), và **Swarm Handoffs** (Chuyển giao phi tập trung).
  * Kỹ thuật cách ly ngữ cảnh (**Context Quarantine**) và truyền thông điệp có cấu trúc (**Structured Message Passing**) giữa các Subagents.
  * Code mẫu Python hệ thống Multi-Agent Researcher - Writer.

* 📖 **[[04_ast_self_healing_code_agents|04_ast_self_healing_code_agents.md - Tác Tử Lập Trình Tự Sửa Lỗi Qua Cây Cú Pháp Trừu Tượng (AST)]]**:
  * **Bẫy ảo giác sửa lỗi:** Hiện tượng sụp đổ hồi quy (Cascading Regressions) khi prompt sửa lỗi ngây thơ; tại sao Agent cần nhìn code dưới dạng Cây Cú Pháp Trừu Tượng (AST).
  * **Kiến trúc vòng lặp 4 tầng:** Tầng 1 (AST Syntax Gate $< 1\text{ms}$), Tầng 2 (Static Linter/Mypy), Tầng 3 (Sandboxed Execution & Traceback Extraction), Tầng 4 (Unit Test & Assertion Delta).
  * **Đột phá từ SWE-bench:** Agent-Computer Interface (ACI của SWE-agent), nén Repo Map bằng Tree-sitter + PageRank (Aider), và Verbal Reinforcement Learning (Reflexion).
  * **Thực hành Code:** Triển khai `ASTSelfHealingEngine` Python tự động bắt lỗi cú pháp, cô lập phạm vi hàm lỗi và tự sửa lỗi lặp lại.

* 📖 **[[05_durable_execution_and_stateful_workflows|05_durable_execution_and_stateful_workflows.md - Thực Thi Bền Vững & Stateful Workflows]]**:
  * **Khắc phục sụp đổ tiến trình:** Triết lý Durable Execution ("chạy như thể không bao giờ sập"), giải quyết rủi ro mất trắng ngữ cảnh trong RAM khi tiến trình chạy dài ngày.
  * **Giải phẫu State Graphs & Máy trạng thái:** Định nghĩa toán học trạng thái $\mathcal{S}_t$, hàm Reducer thuần khiết, cạnh có điều kiện (Conditional Edges) và bộ định tuyến nhận thức.
  * **Checkpointing phân tán & Replay Determinism:** Event-sourcing checkpointer, memoization kết quả công cụ (Observation Caching) và bảo đảm tính Idempotency chống lặp tác dụng phụ ngoại vi.
  * **Time-Travel Debugging & Human-in-the-Loop:** Phân nhánh lịch sử (State Forking), tua lại trạng thái để sửa lỗi và điểm ngắt phê duyệt con người bất đồng bộ (`interrupt_before`).
  * **So sánh & Thực hành Python:** Ma trận so sánh Temporal vs. LangGraph vs. Prefect và kịch bản `DurableStateGraph` SQLite mô phỏng sập nguồn & phục hồi tức thì.

---

## 🔗 Điều Hướng Nhanh
* Trở về mục lục Trụ cột 3: [[03-building-agents/README|🛠️ Trụ Cột 3: Building Agents]]
* Trở về trang chủ Vault: [[README|🏠 Vault Home MOC]]
* Xem bản đồ Canvas: [[Agent-Course-Overview.canvas|🗺️ Mở Visual Canvas]]
