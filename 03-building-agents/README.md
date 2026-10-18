---
title: "Trụ Cột 3: Building Agents"
aliases:
  - Building Agents MOC
  - Autonomous Agents Architecture
tags:
  - agent-course
  - building-agents
  - moc
type: moc
created: 2026-09-20
updated: 2026-09-21
---

# 🛠️ TRỤ CỘT 3: BUILDING AGENTS (KỸ THUẬT XÂY DỰNG TÁC TỬ TỰ HÀNH)

Trụ cột này là đích đến tối thượng của khóa học: **Biến một mô hình ngôn ngữ tĩnh (Static One-Shot LLM) thành một Hệ thống Tác tử Tự trị (Autonomous Agentic System)** có khả năng quan sát môi trường, suy luận nhiều bước, tự gọi công cụ và tự sửa lỗi để hoàn thành các mục tiêu phức tạp.

---

## 🗺️ Bản Đồ Cấu Trúc Trụ Cột 3

```text
03-building-agents/
├── README.md                                    # (Tài liệu này) Giới thiệu tổng quan Trụ cột 3
├── 00_ai_chat_systems_and_prompt_engineering.md # 🏛️ Bài 00 (Nhập môn): Dẫn nhập kiến trúc Harness, Memory & 4 tầng tiến hóa
│
├── 01-harness-and-memory/                       # 🗄️ Tầng 1: Bộ khung điều khiển, Bộ nhớ & Caching
│   ├── README.md                                # System Instructions, Context Drift, Dynamic Memory
│   ├── 01_harness_architecture.md               # Giải phẫu kiến trúc Harness & Session Lifecycle
│   ├── 02_context_management.md                 # Quản trị cửa sổ ngữ cảnh, bệnh lý & cô lập
│   ├── 03_memory_systems.md                     # Kiến trúc bộ nhớ nhận thức đa tầng (MemGPT/Zep)
│   └── 04_agent_runtime_parameters_and_prompt_caching.md # Siêu tham số suy luận, TTFT & Prompt Caching
│
├── 02-tools-and-mcp/                            # 🔌 Tầng 2: Giao thức kết nối công cụ & thế giới thực
│   ├── README.md                                # Model Context Protocol (MCP), Function Calling, Tools
│   ├── 01_mcp_architecture.md                   # Kiến trúc giao thức MCP & FastMCP Python
│   └── 02_constrained_decoding_and_structured_outputs.md # Bảo đảm cú pháp Logit qua FSM/CFG & Jump-Forward
│
├── 03-loop-engineering/                        # 🔄 Tầng 3: Vòng lặp tự trị & Đội ngũ đa tác tử
│   ├── README.md                                # ReAct, Plan-and-Execute, Evaluator-Optimizer, Subagents
│   ├── 01_loop_fundamentals.md                  # Nền tảng vòng lặp tự trị & Circuit Breakers
│   ├── 02_react_and_planning.md                 # Các mô hình vòng lặp cốt lõi
│   ├── 03_multi_agent_teams.md                  # Kiến trúc đội ngũ đa tác tử & Phân rã ngữ cảnh
│   ├── 04_ast_self_healing_code_agents.md       # Tác tử lập trình tự sửa lỗi qua Cây cú pháp AST & ACI
│   └── 05_durable_execution_and_stateful_workflows.md # Máy trạng thái bền vững, Checkpointing & Time-Travel Debugging
│
├── 04-observability-and-evals/                 # 📊 Tầng 4: Giám sát vết, Đánh giá chất lượng & Quản trị
│   ├── README.md                                # Distributed Tracing (Langfuse/OpenTelemetry), Ragas, LLM-as-a-Judge
│   └── 01_agent_evals_and_tracing.md            # Đo lường định lượng, Tracing phân tán & CI/CD Evals
│
├── 05-multimodal-gui-agents/                   # 🖥️ Tầng 5: Tác tử đa phương thức & Computer-Use
│   ├── README.md                                # Tổng quan tương tác màn hình, pixels & OS Automation
│   └── 01_multimodal_gui_and_computer_use.md    # Visual UI Grounding (Set-of-Mark/OmniParser) & OSWorld
│
├── 06_how_to_build_enterprise_ai_agents.md      # 🏗️ Bài 06 (Tổng kết): CẨM NANG TOÀN TẬP kiến trúc khối, 6 phòng ban & Production
├── 07_fullstack_agent_mern_architecture.md      # 🌐 Bài 07 (Thực chiến Full-stack): Kiến trúc MERN Stack, Atlas Vector Search & React Generative UI
├── 08_code_graphs_and_repository_intelligence.md # 🕸️ Bài 08 (Code Intelligence): Code Property Graph, SCIP Indexing, Graph-RAG & Quản trị ngữ cảnh liên phiên
└── 09_hitl_and_hotl_human_agent_interaction.md  # 🛡️ Bài 09 (Quản trị An toàn): Human-in-the-Loop (HITL), Human-on-the-Loop (HOTL) & Durable State Machine
```

---

## 📂 Danh Mục Các Thành Phần Kiến Trúc (Theo Tiến Trình Học)

### 🏛️ Bài 00: Tài Liệu Kiến Trúc Nền Tảng (Đọc Mở Đầu - Foundational Primer)
* 📖 [00_ai_chat_systems_and_prompt_engineering - Kiến trúc & Tiến hóa của các hệ thống AI Chat](./00_ai_chat_systems_and_prompt_engineering.md):
  * Phân tích bản chất One-Shot và tính tĩnh (Static) của LLM Core.
  * Giải phẫu một AI Software Harness (System Instructions, Chat History, Memory, SKILLS & Tools).
  * 3 cấu phần của hệ thống Memory (User Profile, Dynamic Memory, Semantic Retrieval).
  * 4 cấp độ tiến hóa từ Prompting đến Agentic Loop Engineering.

---

### 1. [01-harness-and-memory - AI Harness & Memory Architecture](./01-harness-and-memory/README.md)
* **Trọng tâm:** Bộ khung phần mềm quản lý tương tác giữa người dùng và LLM Core.
* **Tài liệu chi tiết:**
  * [Giải Phẫu Kiến Trúc AI Harness](./01-harness-and-memory/01_harness_architecture.md): Phân tách Lõi tĩnh vs Khung có trạng thái, 5 phân hệ phần mềm và Session Lifecycle.
  * [Quản Trị Cửa Sổ Ngữ Cảnh: Bệnh Lý, Tỉa Nhánh, Tóm Tắt & Cô Lập](./01-harness-and-memory/02_context_management.md): Chẩn đoán 3 bệnh lý (Context Poisoning, Context Decay, Context Starvation), giải pháp RAG, Context Pruning, Summarization và kiến trúc Context Quarantine.
  * [Kiến Trúc Bộ Nhớ Đa Tầng Cho AI Agents](./01-harness-and-memory/03_memory_systems.md): Mô hình 3 phân tầng Short-term, Working Memory (Scratchpad), Long-term Memory (Vector DB/Profile) và cơ chế Dynamic Memory Consolidation.
  * [Tham Số Vận Hành Tác Tử & Tối Ưu Hóa Prompt Caching](./01-harness-and-memory/04_agent_runtime_parameters_and_prompt_caching.md): Bản chất Prefill $O(N^2)$, cơ chế Prefix Caching (RadixTree) giảm 90% chi phí và TTFT từ 3.5s xuống 0.25s, quy tắc bất biến tiền tố (Static Prefix Invariance), giải phẫu siêu tham số (`temperature`, `top_p`, `max_tokens`, `stop`, cấm `penalties` trong Agent) và kịch bản đo lường hiệu năng thời gian thực.
* **Nhiệm vụ:**
  * Quản trị cửa sổ ngữ cảnh (Context Window Hygiene, chống Context Drift khi code/debug dài).
  * Cơ chế bộ nhớ động (Dynamic Memory Extraction) và truy vấn lịch sử qua Semantic Search.
  * Phân quyền thực thi và cô lập môi trường (Sandboxing).

### 2. [02-tools-and-mcp - Model Context Protocol (MCP) & Tool Integration](./02-tools-and-mcp/README.md)
* **Trọng tâm:** Giao thức chuẩn mở của Anthropic kết nối LLM với thế giới thực và kỹ thuật bảo đảm cú pháp cuộc gọi công cụ.
* **Tài liệu chi tiết:**
  * [Kiến Trúc Giao Thức Model Context Protocol (MCP)](./02-tools-and-mcp/01_mcp_architecture.md): Khảo sát bài toán $N \times M$, tam giác Host-Client-Server, 3 cấu phần nguyên thủy (Tools, Resources, Prompts), cơ chế truyền tải stdio/SSE, giải phẫu JSON-RPC 2.0 và code mẫu FastMCP Python.
  * [Constrained Decoding & Grammar-Guided Structured Outputs](./02-tools-and-mcp/02_constrained_decoding_and_structured_outputs.md): Toán học tầng Unembedding $\mathbf{W}_U$, mặt nạ nhị phân Logit Masking triệt tiêu $100\%$ lỗi cú pháp JSON/Tool Schema, Finite State Machines (Outlines), Pushdown Automata (llama.cpp GBNF) và tăng tốc Jump-Forward Decoding (SGLang).
* **Nhiệm vụ:**
  * Mô hình Client-Host-Server trong MCP.
  * Xây dựng và tích hợp MCP Tools (chạy lệnh, gọi API, thao tác tệp tin) và Resources (truy xuất database, tài liệu).
  * Bảo đảm tính đúng đắn kiểu dữ liệu (Type-Safety) cấp độ Logit khi Agent xuất tham số gọi hàm.

### 3. [03-loop-engineering - Loop Engineering & Autonomous Workflows](./03-loop-engineering/README.md)
* **Trọng tâm:** Thiết kế các vòng lặp phản hồi (Feedback Loops) tự động hóa và tác tử tự sửa lỗi.
* **Tài liệu chi tiết:**
  * [Nền Tảng Loop Engineering: Vòng Lặp Tự Trị, Điều Kiện Dừng & Circuit Breakers](./03-loop-engineering/01_loop_fundamentals.md): Từ One-shot sang Recursive Execution, chu trình OODA 5 bước, 4 tầng Stopping Criteria và bộ ngắt mạch chống lặp vô tận.
  * [Các Mô Hình Vòng Lặp Cốt Lõi (ReAct, Plan-and-Execute, Evaluator-Optimizer)](./03-loop-engineering/02_react_and_planning.md): So sánh định lượng và ma trận đánh đổi giữa ReAct phản xạ nhanh, Plan-and-Execute tiết kiệm token, và Evaluator-Optimizer tự sửa sai.
  * [Kiến Trúc Đội Ngũ Đa Tác Tử (Multi-Agent Systems)](./03-loop-engineering/03_multi_agent_teams.md): Phân công lao động nhận thức qua mô hình Orchestrator-Worker, Supervisor Hierarchy, Swarm Handoffs và kỹ thuật Context Quarantine giữa các Subagents.
  * [Tác Tử Lập Trình Tự Sửa Lỗi Qua Cây Cú Pháp Trừu Tượng (AST)](./03-loop-engineering/04_ast_self_healing_code_agents.md): Phòng chống Cascading Regressions, 4 tầng kiểm định (AST Syntax Gate $< 1\text{ms}$, Static Typing, Sandboxed Traceback, Test Verification), ACI Interface (SWE-agent), Repo Map (Aider) và Verbal RL (Reflexion).
  * [Thực Thi Bền Vững & Stateful Workflows](./03-loop-engineering/05_durable_execution_and_stateful_workflows.md): Triết lý Durable Execution ("chạy như thể không bao giờ sập"), máy trạng thái State Graphs $\mathcal{S}_t$, Event-sourcing Checkpointers, Replay Determinism & Observation Caching chống lặp tác dụng phụ ngoại vi, Time-Travel Debugging và Human-in-the-Loop Interrupts (`interrupt_before`).
* **Nhiệm vụ:**
  * Vòng lặp **ReAct (Reason + Act)**: Suy luận $\rightarrow$ Hành động $\rightarrow$ Quan sát.
  * Luồng **Plan-and-Execute**: Lập kế hoạch tổng thể $\rightarrow$ Thực thi từng bước con $\rightarrow$ Cập nhật kế hoạch.
  * Luồng **Evaluator-Optimizer & AST Self-Healing**: Đánh giá $\rightarrow$ Phản biện $\rightarrow$ Tự sửa lỗi mã nguồn.
  * Phối hợp đa tác tử (Multi-agent teams, Subagent delegation).

### 4. [04-observability-and-evals - Agent Observability, Evals & Governance](./04-observability-and-evals/README.md)
* **Trọng tâm:** Đo lường định lượng, giám sát phân tán và thẩm định tự động chất lượng Agent trên môi trường Production.
* **Tài liệu chi tiết:**
  * [Hệ Thống Giám Sát, Đo Lường & Đánh Giá Tác Tử AI](./04-observability-and-evals/01_agent_evals_and_tracing.md): Chuẩn OpenTelemetry GenAI Semantic Conventions, Cây vết (Trace Tree), tích hợp Langfuse Tracing, bộ chỉ số Ragas Triad, giải phẫu 4 thiên vị LLM-as-a-Judge, kỹ thuật G-Eval xác suất Softmax, benchmark SWE-bench/GAIA và phương pháp sinh tập kiểm thử tổng hợp (Synthetic Testset).
* **Nhiệm vụ:**
  * Phá bỏ rào cản "Vibe-checking", thiết lập quy trình kiểm thử hồi quy CI/CD tự động.
  * Theo dõi chi phí token, độ trễ từng bước và phát hiện trôi dạt ngữ nghĩa (Semantic Drift).
  * Đo lường độ chính xác tham số công cụ (Tool Calling Accuracy) và tỷ lệ hoàn thành tác vụ (TCR).

### 5. [05-multimodal-gui-agents - Multimodal GUI Agents & Computer-Use](./05-multimodal-gui-agents/README.md)
* **Trọng tâm:** Tác tử đa phương thức nhìn màn hình (Pixels) và điều khiển hệ điều hành thông qua chuột và bàn phím ảo.
* **Tài liệu chi tiết:**
  * [Kỷ Nguyên Tác Tử Tương Tác Trực Quan Màn Hình & Hệ Điều Hành](./05-multimodal-gui-agents/01_multimodal_gui_and_computer_use.md): Nghịch lý "Vật chất tối của API", Visual UI Grounding, Set-of-Mark (SoM) Prompting, OmniParser, Không gian tọa độ chuẩn hóa $[0, 1000] \times [0, 1000]$, Không gian hành động nguyên thủy (Atomic Action Space), phòng chống Render Latency, Frame Differencing tiết kiệm 85% token và đánh giá benchmark OSWorld.
* **Nhiệm vụ:**
  * Tự động hóa các phần mềm desktop và web portal không có API.
  * Tương tác tự nhiên qua mắt nhìn (Visual Patches) và tay bấm (OS Input Controller).

---

### 🏗️ Bài 06: Cẩm Nang Kiến Trúc Tổng Thể & Thích Ứng Doanh Nghiệp (Đọc Tổng Hợp - Capstone Blueprint)
* 📖 [06_how_to_build_enterprise_ai_agents - Cẩm Nang Toàn Tập Xây Dựng AI Agent Doanh Nghiệp (Enterprise AI Agent Blueprint)](./06_how_to_build_enterprise_ai_agents.md):
  * **Sơ đồ khối 6 tầng (Block Diagram):** Ingress Gateway, Agent Harness Core, Memory Systems, MCP Tooling, Execution Sandboxes, Observability & Evals.
  * **Bộ sưu tập AI Agent Design Patterns:** Router/Classifier, ReAct, Plan-and-Execute, Evaluator-Optimizer, Supervisor-Worker & Swarm Handoff.
  * **Thích ứng chuyên sâu cho 6 phòng ban:** Sales & BD, Nhân sự (HR), Tài chính & Kế toán (3-Way Matching), Pháp chế (Playbook rà soát hợp đồng), Chăm sóc khách hàng & IT Helpdesk (Self-healing), Kỹ thuật phần mềm (SWE-bench paradigm).
  * **5 Thất bại hệ thống & Chiến lược phòng vệ:** Execution Hallucination (Pydantic/Constrained Decoding), Infinite Loops & Tool Storms (Circuit Breakers), State Drift (Context Hygiene), RBAC/ACL Breaches (Identity Propagation), Indirect Prompt Injection (Context Quarantine & Dual-LLM).
  * **Quy trình 6 giai đoạn đưa Agent từ Prototype lên Production.**

---

### 🌐 Bài 07: Kiến Trúc Ứng Dụng Tác Tử Toàn Diện Với MERN Stack (Full-Stack Agent Blueprint)
* 📖 [**07_fullstack_agent_mern_architecture.md - Kiến Trúc Ứng Dụng Tác Tử Toàn Diện Với MERN Stack**](07_fullstack_agent_mern_architecture.md):
  * **Sự chuyển dịch kiến trúc:** Từ Web 2.0 CRUD sang Modern Agentic MERN (MongoDB Atlas Vector Search + Express Ingress Gateway + React Generative UI + Node.js MCP Orchestrator).
  * **MongoDB Atlas kép:** HNSW Vector Indexing, Hybrid Search kết hợp $BM25$ và Dense Vectors qua Reciprocal Rank Fusion (RRF), Checkpoint Store lưu trữ máy trạng thái bền vững (`langgraph-checkpoint-mongodb`).
  * **Express & Node.js MCP Runtime:** Thiết kế Server-Sent Events (SSE) streaming cho ReAct Thought Traces, tích hợp TypeScript MCP Client (`@modelcontextprotocol/sdk`) và bộ ngắt mạch Circuit Breaker.
  * **React Generative UI:** Scratchpad Visualizer, Human-in-the-Loop Confirmation Modals chặn tác vụ nhạy cảm, render UI Component động theo JSON output.
  * **Mã nguồn thực chiến mẫu:** TypeScript Mongoose Vector Schema, Express SSE Controller, và React Chat Workspace.

---

### 🕸️ Bài 08: Code Graphs & Repository Intelligence (Trí Tuệ Kho Mã Nguồn & Ngữ Cảnh Liên Phiên)
* 📖 [**08_code_graphs_and_repository_intelligence.md - Code Graphs, SCIP Indexing & Cross-Session Project Memory**](08_code_graphs_and_repository_intelligence.md):
  * **Khoảng cách cú pháp - ngữ nghĩa:** Tại sao Vector RAG truyền thống thất bại thảm hại trước codebase và gây ra hiện tượng Lost in the Middle.
  * **Giải phẫu Code Property Graph (CPG):** Hợp nhất 3 chiều không gian: Cây cú pháp AST (Tree-sitter), Đồ thị luồng điều khiển CFG và Đồ thị phụ thuộc dữ liệu DFG/PDG (Def-Use chains).
  * **Giao thức chuẩn doanh nghiệp SCIP & LSIF:** Định danh symbol chính xác $100\%$ không ảo giác, phân giải tham chiếu chéo tệp (Go to Definition, Find all References).
  * **Graph-RAG cho Codebase:** Thuật toán lan truyền lân cận $k$-bước (K-Hop Neighborhood Expansion) và phân tích vùng ảnh hưởng (Blast Radius / Impact Analysis) ngăn chặn gãy đổ dây chuyền khi refactor.
  * **Bộ 5 chiến lược ngữ cảnh dự án liên phiên (Cross-Session Memory):** Mô hình Memory Bank (`CLAUDE.md`, `AGENTS.md`, `activeContext.md`), On-disk Incremental Delta Index Caching, Session Compaction, Architectural Decision Records (ADRs) và Bi-temporal Knowledge Graphs.
  * **Mã nguồn thực chiến:** Mini Code Graph bằng Python (`networkx` + `ast`) kết hợp bộ quản trị session memory bền vững trên đĩa.

---

### 🛡️ Bài 09: Human-in-the-Loop (HITL) & Human-on-the-Loop (HOTL) (Quản Trị Rủi Ro & Tương Tác Người - Máy)
* 📖 [**09_hitl_and_hotl_human_agent_interaction.md - HITL, HOTL & Quản Trị Rủi Ro Cấp Doanh Nghiệp**](09_hitl_and_hotl_human_agent_interaction.md):
  * **Phổ tự trị (The Autonomy Spectrum):** Định nghĩa kỹ thuật 3 cấp độ: HITL (Chốt chặn đồng bộ), HOTL (Giám sát bất đồng bộ) và HOOTL (Tự trị tuyệt đối).
  * **Ma trận rủi ro vs tự tin (Risk vs. Confidence Matrix):** Công thức định lượng Task Risk Index và Agent Confidence Score; quy tắc leo thang tự động (Dynamic Escalation Protocol).
  * **4 Architecture Patterns:** Interrupt-Resume với Durable State Machine (Hydration/Dehydration giải phóng tài nguyên server), Parameter Overriding (sửa tham số trực tiếp trước khi chạy), Progressive Autonomy (tự trị tăng dần theo niềm tin), Steerability & Mid-flight Course Correction.
  * **Tối ưu trải nghiệm người dùng & phòng chống Approval Fatigue:** Context Distillation (Impact Cards, Diff View), Batch Approval với giao dịch nguyên tử, và kiểm soát kép (Two-Person Rule).
  * **Mã nguồn thực chiến:** Hệ thống Python hoàn chỉnh gồm `RiskEvaluator`, `DurableAgentHarness`, cổng duyệt HITL bất đồng bộ, và chốt dừng khẩn cấp `EmergencyKillSwitch` cho HOTL.

---

## 🔗 Điều Hướng Nhanh
* Trở về trang chủ: [🏠 Vault Home MOC](../README.md)
* Xem bản đồ Canvas: [🗺️ Mở Visual Canvas](../Agent-Course-Overview.canvas)
