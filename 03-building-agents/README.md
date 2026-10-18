---
title: "03-building-agents: Kỹ Thuật Xây Dựng Tác Tử Tự Hành (Building Autonomous Agents)"
tags:
  - agent-course
  - autonomous-agents
  - loop-engineering
  - tools-and-mcp
  - harness-and-memory
  - code-intelligence
  - token-economics
  - multi-agent-consensus
  - governance
  - enterprise-ai
type: moc
created: 2026-09-27
updated: 2026-10-18
---

# 🛠️ TRỤ CỘT 3: BUILDING AGENTS (KỸ THUẬT XÂY DỰNG TÁC TỬ TỰ HÀNH)

Trụ cột này là đích đến tối thượng của khóa học: **Biến một mô hình ngôn ngữ tĩnh (Static One-Shot LLM) thành một Hệ thống Tác tử Tự trị (Autonomous Agentic System)** có khả năng quan sát môi trường, suy luận nhiều bước, tự gọi công cụ, phối hợp bầy đàn và tự sửa lỗi để hoàn thành các mục tiêu phức tạp trong thực tế sản xuất.

Toàn bộ các chủ đề trong Trụ cột 3 được tổ chức thành **10 phân hệ chuyên sâu (01 đến 10)**, sắp xếp chuẩn xác theo **Thứ Tự Đọc & Tiến Trình Tiếp Thu (Pedagogical Reading Order)**: từ tế bào thần kinh điều khiển, kết nối công cụ, vòng lặp nhận thức, đo lường, trí tuệ mã nguồn, kinh tế token, tranh biện bầy đàn, quản trị con người đến bàn giao ứng dụng doanh nghiệp hoàn chỉnh.

---

## 🗺️ Bản Đồ Cấu Trúc Trụ Cột 3 (10 Phân Hệ Module Hóa)

```text
03-building-agents/
├── README.md                                    # (Tài liệu này) Giới thiệu tổng quan & lộ trình học Trụ cột 3
│
├── 01-harness-and-memory/                       # 🗄️ Module 01: Bộ khung điều khiển, Bộ nhớ nhận thức & Caching
│   ├── README.md                                # System Instructions, Context Drift, Dynamic Memory
│   ├── 00_ai_chat_systems_and_prompt_engineering.md # Dẫn nhập kiến trúc Harness, Memory & 4 tầng tiến hóa
│   ├── 01_harness_architecture.md               # Giải phẫu kiến trúc Harness & Session Lifecycle
│   ├── 02_context_management.md                 # Quản trị cửa sổ ngữ cảnh, bệnh lý & cô lập
│   ├── 03_memory_systems.md                     # Kiến trúc bộ nhớ nhận thức đa tầng (MemGPT/Zep)
│   └── 04_agent_runtime_parameters_and_prompt_caching.md # Siêu tham số suy luận, TTFT & Prompt Caching
│
├── 02-tools-and-mcp/                            # 🔌 Module 02: Giao thức kết nối công cụ & thế giới thực
│   ├── README.md                                # Model Context Protocol (MCP), Function Calling, Tools
│   ├── 01_mcp_architecture.md                   # Kiến trúc giao thức MCP & FastMCP Python
│   └── 02_constrained_decoding_and_structured_outputs.md # Bảo đảm cú pháp Logit qua FSM/CFG & Jump-Forward
│
├── 03-loop-engineering/                        # 🔄 Module 03: Vòng lặp nhận thức & Đội ngũ đa tác tử
│   ├── README.md                                # ReAct, Plan-and-Execute, Evaluator-Optimizer, Subagents
│   ├── 01_loop_fundamentals.md                  # Nền tảng vòng lặp tự trị & Circuit Breakers
│   ├── 02_react_and_planning.md                 # Các mô hình vòng lặp cốt lõi (ReAct vs Plan-and-Execute)
│   ├── 03_multi_agent_teams.md                  # Kiến trúc đội ngũ đa tác tử & Phân rã ngữ cảnh
│   ├── 04_ast_self_healing_code_agents.md       # Tác tử lập trình tự sửa lỗi qua Cây cú pháp AST & ACI
│   └── 05_durable_execution_and_stateful_workflows.md # Máy trạng thái bền vững, Checkpointing & Time-Travel Debugging
│
├── 04-observability-and-evals/                 # 📊 Module 04: Giám sát vết, Đánh giá chất lượng & Benchmarking
│   ├── README.md                                # OpenTelemetry GenAI Conventions, Langfuse Tracing, SWE-bench
│   └── 01_agent_evals_and_tracing.md            # Đo lường định lượng, Tracing phân tán & CI/CD Evals
│
├── 05-multimodal-gui-agents/                   # 🖥️ Module 05: Tác tử đa phương thức & Computer-Use
│   ├── README.md                                # Tương tác màn hình, pixels & Tự động hóa hệ điều hành
│   └── 01_multimodal_gui_and_computer_use.md    # Visual UI Grounding (Set-of-Mark/OmniParser) & OSWorld
│
├── 06-code-intelligence/                       # 🕸️ Module 06: Trí tuệ kho mã nguồn & Ngữ cảnh liên phiên
│   ├── README.md                                # Code Property Graphs (CPG), Symbol Indexing, Graph-RAG
│   └── 01_code_graphs_and_repository_intelligence.md # SCIP Indexing, Blast Radius & Memory Bank (CLAUDE.md)
│
├── 07-cost-and-token-economics/                # 💰 Module 07: Tối ưu hóa chi phí & Kinh tế Token
│   ├── README.md                                # Quản trị ngân sách vòng lặp, Model Cascading & Pruning
│   └── 01_token_economics_and_cost_optimization.md # FrugalGPT Router, Prefix Caching & Budget Circuit Breakers
│
├── 08-multi-agent-consensus/                   # 🏛️ Module 08: Tranh biện, Bỏ phiếu & Đồng thuận Đa Tác tử
│   ├── README.md                                # Social Choice Theory, Phá vỡ thiên kiến xác nhận đơn lẻ
│   └── 01_multi_agent_debate_and_consensus.md   # Peer-to-Peer Debate, Borda Count & Định lý Condorcet
│
├── 09-governance-and-hitl/                     # 🛡️ Module 09: Quản trị an toàn & Tương tác Người - Máy
│   ├── README.md                                # Phổ tự trị HITL/HOTL/HOOTL, Ngắt mạch khẩn cấp
│   └── 01_hitl_and_hotl_human_agent_interaction.md # Ma trận Task Risk Index, Durable Checkpoint & Kill Switch
│
└── 10-enterprise-and-production/               # 🚀 Module 10: Đóng gói sản phẩm & Triển khai doanh nghiệp
    ├── README.md                                # Capstone Production: Kiến trúc 6 phòng ban & MERN Stack
    ├── 01_how_to_build_enterprise_ai_agents.md  # Cẩm nang toàn tập xây dựng AI Agent doanh nghiệp
    └── 02_fullstack_agent_mern_architecture.md  # Ứng dụng Full-stack MERN: SSE Streaming & Generative UI
```

---

## 📂 Danh Mục Phân Tích Chi Tiết 10 Module Theo Thứ Tự Đọc

### 1. [01-harness-and-memory - AI Harness & Memory Architecture](./01-harness-and-memory/README.md)
* **Trọng tâm:** Bộ khung phần mềm quản lý tương tác giữa người dùng và LLM Core.
* **Tài liệu chi tiết:**
  * [Dẫn nhập kiến trúc AI Chat & 4 tầng tiến hóa](./01-harness-and-memory/00_ai_chat_systems_and_prompt_engineering.md): Khái niệm dẫn nhập về AI Harness, bộ nhớ nhận thức và 4 bước chuyển từ Prompting lên Agentic Loops.
  * [Giải Phẫu Kiến Trúc AI Harness](./01-harness-and-memory/01_harness_architecture.md): Phân tách Lõi tĩnh vs Khung có trạng thái, 5 phân hệ phần mềm và Session Lifecycle.
  * [Quản Trị Cửa Sổ Ngữ Cảnh: Bệnh Lý, Tỉa Nhánh, Tóm Tắt & Cô Lập](./01-harness-and-memory/02_context_management.md): Chẩn đoán 3 bệnh lý (Context Poisoning, Context Decay, Context Starvation), giải pháp RAG, Context Pruning, Summarization và kiến trúc Context Quarantine.
  * [Kiến Trúc Bộ Nhớ Đa Tầng Cho AI Agents](./01-harness-and-memory/03_memory_systems.md): Mô hình 3 phân tầng Short-term, Working Memory (Scratchpad), Long-term Memory (Vector DB/Profile) và cơ chế Dynamic Memory Consolidation.
  * [Tham Số Vận Hành Tác Tử & Tối Ưu Hóa Prompt Caching](./01-harness-and-memory/04_agent_runtime_parameters_and_prompt_caching.md): Bản chất Prefill $\mathcal{O}(N^2)$, cơ chế Prefix Caching (RadixTree) giảm 90% chi phí và TTFT từ 3.5s xuống 0.25s, quy tắc bất biến tiền tố (Static Prefix Invariance), giải phẫu siêu tham số (`temperature`, `top_p`, `max_tokens`, `stop`, cấm `penalties` trong Agent).

---

### 2. [02-tools-and-mcp - Tools, Protocol & Constrained Decoding](./02-tools-and-mcp/README.md)
* **Trọng tâm:** Kết nối tác tử với thế giới thực qua giao thức mở và bảo đảm cú pháp $100\%$.
* **Tài liệu chi tiết:**
  * [Kiến Trúc Giao Thức Model Context Protocol (MCP)](./02-tools-and-mcp/01_mcp_architecture.md): Giải quyết bài toán phân mảnh $M \times N$, 3 primitives cốt lõi (Resources, Prompts, Tools), kiến trúc Client-Host-Server và FastMCP Python SDK.
  * [Constrained Decoding & Cưỡng Chế Cú Pháp Đầu Ra Bằng Ngữ Pháp](./02-tools-and-mcp/02_constrained_decoding_and_structured_outputs.md): Ma trận Unembedding $\mathbf{W}_U$, mặt nạ Logit Masking triệt tiêu ảo giác JSON, biên dịch Regex sang FSM (Outlines), Pushdown Automata (GBNF) và tăng tốc Jump-Forward Decoding (SGLang).

---

### 3. [03-loop-engineering - Vòng Lặp Nhận Thức & Đa Tác Tử](./03-loop-engineering/README.md)
* **Trọng tâm:** Biến LLM từ bộ máy trả lời một lần thành động cơ tự hành liên tục.
* **Tài liệu chi tiết:**
  * [Nền Tảng Vòng Lặp Tự Trị & Circuit Breakers](./03-loop-engineering/01_loop_fundamentals.md): Từ One-shot sang Recursive Execution, 4 tầng Stopping Criteria và bộ ngắt mạch chống lặp vô tận.
  * [Các Mô Hình Vòng Lặp Cốt Lõi (ReAct, Plan-and-Execute, Evaluator-Optimizer)](./03-loop-engineering/02_react_and_planning.md): So sánh định lượng và ma trận đánh đổi giữa ReAct, Plan-and-Execute, và Evaluator-Optimizer.
  * [Kiến Trúc Đội Ngũ Đa Tác Tử (Multi-Agent Systems)](./03-loop-engineering/03_multi_agent_teams.md): Phân công lao động nhận thức qua mô hình Orchestrator-Worker, Supervisor Hierarchy, Swarm Handoffs và kỹ thuật Context Quarantine.
  * [Tác Tử Lập Trình Tự Sửa Lỗi Qua Cây Cú Pháp Trừu Tượng (AST)](./03-loop-engineering/04_ast_self_healing_code_agents.md): Phòng chống Cascading Regressions, 4 tầng kiểm định (AST Syntax Gate $< 1\text{ms}$, Static Typing, Sandboxed Traceback, Test Verification), ACI Interface (SWE-agent), Repo Map (Aider).
  * [Thực Thi Bền Vững & Stateful Workflows](./03-loop-engineering/05_durable_execution_and_stateful_workflows.md): Triết lý Durable Execution ("chạy như thể không bao giờ sập"), máy trạng thái State Graphs $\mathcal{S}_t$, Event-sourcing Checkpointers, Replay Determinism & Observation Caching chống lặp tác dụng phụ ngoại vi, Time-Travel Debugging.

---

### 4. [04-observability-and-evals - Giám Sát Vết & Đo Lường Chất Lượng](./04-observability-and-evals/README.md)
* **Trọng tâm:** Đo lường định lượng, Tracing phân tán và thẩm định tự động chất lượng Agent trên Production.
* **Tài liệu chi tiết:**
  * [Hệ Thống Giám Sát, Đo Lường & Đánh Giá Tác Tử AI](./04-observability-and-evals/01_agent_evals_and_tracing.md): Chuẩn OpenTelemetry GenAI Semantic Conventions, Cây vết (Trace Tree), tích hợp Langfuse Tracing, bộ chỉ số Ragas Triad, giải phẫu 4 thiên vị LLM-as-a-Judge, kỹ thuật G-Eval xác suất Softmax và benchmark SWE-bench/GAIA.

---

### 5. [05-multimodal-gui-agents - Tác Tử Tương Tác Màn Hình & Hệ Điều Hành](./05-multimodal-gui-agents/README.md)
* **Trọng tâm:** Tác tử đa phương thức nhìn màn hình (Pixels) và điều khiển hệ điều hành thông qua chuột và bàn phím ảo.
* **Tài liệu chi tiết:**
  * [Kỷ Nguyên Tác Tử Tương Tác Trực Quan Màn Hình & Hệ Điều Hành](./05-multimodal-gui-agents/01_multimodal_gui_and_computer_use.md): Nghịch lý "Vật chất tối của API", Visual UI Grounding, Set-of-Mark (SoM) Prompting, OmniParser, Tọa độ chuẩn hóa $[0, 1000] \times [0, 1000]$, Không gian hành động nguyên thủy (Atomic Action Space), phòng chống Render Latency, Frame Differencing tiết kiệm 85% token và đánh giá benchmark OSWorld.

---

### 6. [06-code-intelligence - Trí Tuệ Kho Mã Nguồn & Ngữ Cảnh Liên Phiên](./06-code-intelligence/README.md)
* **Trọng tâm:** Hiểu sâu mã nguồn toàn dự án bằng đồ thị cú pháp - ngữ nghĩa và duy trì trí nhớ dự án vĩnh cửu.
* **Tài liệu chi tiết:**
  * [Code Graphs, SCIP Indexing & Cross-Session Project Memory](./06-code-intelligence/01_code_graphs_and_repository_intelligence.md):
    * Khoảng cách cú pháp - ngữ nghĩa: Tại sao Vector RAG truyền thống thất bại trước codebase.
    * Giải phẫu Code Property Graph (CPG): Hợp nhất AST, CFG và DFG/PDG (Def-Use chains).
    * Giao thức định danh Symbol công nghiệp SCIP & LSIF: Phân giải tham chiếu chéo tệp với độ chính xác $100\%$.
    * Graph-RAG cho Codebase & K-Hop Blast Radius Analysis: Khoanh vùng rủi ro phụ thuộc khi refactor.
    * Bộ 5 chiến lược ngữ cảnh liên phiên: Memory Bank (`CLAUDE.md`, `activeContext.md`), Incremental Delta Index Caching, Session Compaction, ADRs và Bi-temporal Knowledge Graphs.

---

### 7. [07-cost-and-token-economics - Tối Ưu Hóa Chi Phí & Kinh Tế Token](./07-cost-and-token-economics/README.md)
* **Trọng tâm:** Kiểm soát chi phí và ngăn chặn bùng nổ ngân sách trong các vòng lặp dài hơi.
* **Tài liệu chi tiết:**
  * [Token Economics & Cost Optimization](./07-cost-and-token-economics/01_token_economics_and_cost_optimization.md):
    * Giải phẫu chi phí vòng lặp: Hiệu ứng cấp số nhân $\mathcal{O}(N^2)$ của context tích lũy dồn toa.
    * Mô hình định tuyến đa tầng (Model Cascading & Routing): FrugalGPT, phân tầng Tier 1 Fast SLMs $\to$ Tier 2 Frontier $\to$ Tier 3 Reasoning.
    * Nén ngữ cảnh & Cắt tỉa quan sát (Observation Distillation): Loại bỏ rác HTML/CSS ngay tại biên công cụ, tiết kiệm $85\%$ tokens.
    * Tối ưu hóa GPU Prefix Prompt Caching: Thiết kế prompt đạt Cache Hit $>85\%$, giảm $80\%$ chi phí và độ trễ.
    * Budget Circuit Breakers: Thiết lập Soft Limit (chế độ tiết kiệm) và Hard Limit ngắt cứng khi chạm trần ngân sách.

---

### 8. [08-multi-agent-consensus - Tranh Biện, Bỏ Phiếu & Đồng Thuận Đa Tác Tử](./08-multi-agent-consensus/README.md)
* **Trọng tâm:** Phá vỡ bẫy ảo giác và thiên kiến xác nhận đơn lẻ bằng trí tuệ tập thể.
* **Tài liệu chi tiết:**
  * [Multi-Agent Debate & Consensus](./08-multi-agent-consensus/01_multi_agent_debate_and_consensus.md):
    * Hạn chế của Single-Agent & Định lý Condorcet's Jury Theorem: Tại sao trí tuệ đám đông nâng độ chính xác từ $70\%$ lên $>92\%$.
    * Các mô hình tranh biện (Debate Topologies): Peer-to-Peer Round-Robin và Adversarial Courtroom (Advocate vs Prosecutor vs Neutral Judge).
    * Các giao thức đồng thuận lý thuyết lựa chọn xã hội: Borda Count (xếp hạng tính điểm), Majority Voting, Condorcet Pairwise, và Logprob-Weighted Confidence.
    * Thuật toán hội tụ ngữ nghĩa (Semantic Convergence) và điều kiện dừng tranh luận sớm.

---

### 9. [09-governance-and-hitl - Quản Trị Rủi Ro & Tương Tác Người - Máy](./09-governance-and-hitl/README.md)
* **Trọng tâm:** Thiết lập chốt chặn an toàn và kiểm soát rủi ro cấp doanh nghiệp.
* **Tài liệu chi tiết:**
  * [Human-in-the-Loop (HITL) & Human-on-the-Loop (HOTL)](./09-governance-and-hitl/01_hitl_and_hotl_human_agent_interaction.md):
    * Phổ tự trị (The Autonomy Spectrum): HITL (Chốt chặn đồng bộ), HOTL (Giám sát bất đồng bộ) và HOOTL (Tự trị tuyệt đối).
    * Ma trận rủi ro vs tự tin (Risk vs Confidence Matrix): Định lượng Task Risk Index và Agent Confidence Score, cơ chế leo thang tự động (Dynamic Escalation).
    * Kiến trúc kỹ thuật: Interrupt-Resume với máy trạng thái bền vững (Durable Execution), Parameter Overriding (sửa tham số trực tiếp trên UI), Progressive Autonomy.
    * Chống hội chứng Approval Fatigue qua Context Distillation (Impact Cards, Diff View) và Two-Person Rule.

---

### 10. [10-enterprise-and-production - Kiến Trúc Triển Khai Doanh Nghiệp & Full-Stack MERN](./10-enterprise-and-production/README.md)
* **Trọng tâm:** Bản thiết kế tổng hợp và mã nguồn hoàn chỉnh đưa AI Agent ra thị trường.
* **Tài liệu chi tiết:**
  * [Cẩm Nang Toàn Tập Xây Dựng AI Agent Doanh Nghiệp](./10-enterprise-and-production/01_how_to_build_enterprise_ai_agents.md): Sơ đồ khối 6 tầng, thích ứng chuyên sâu 6 phòng ban (Sales, HR, Finance, Legal, CS/IT, Engineering), 5 thất bại hệ thống kinh điển & chiến lược phòng vệ, quy trình 6 giai đoạn đưa Agent từ Prototype lên Production.
  * [Kiến Trúc Ứng Dụng Tác Tử Toàn Diện Với MERN Stack](./10-enterprise-and-production/02_fullstack_agent_mern_architecture.md): Modern Agentic MERN (MongoDB Atlas Vector Search HNSW + Hybrid Search RRF + Node.js MCP Runtime + Express SSE Stream + React Generative UI & Human-in-the-Loop Confirmation Modals).

---

## 🔗 Điều Hướng Nhanh
* Trở về trang chủ: [🏠 Vault Home MOC](../README.md)
* Xem bản đồ Canvas: [🗺️ Mở Visual Canvas](../Agent-Course-Overview.canvas)
