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

Toàn bộ các chủ đề trong Trụ cột 3 được tổ chức thành **6 Mô-đun Sư Phạm Thống Nhất (01 đến 06)** với tổng cộng **27 chuyên đề kỹ thuật chuyên sâu**, sắp xếp chuẩn xác theo **Thứ Tự Đọc & Tiến Trình Tiếp Thu (Pedagogical Reading Order)**: từ tế bào thần kinh điều khiển, kết nối công cụ, vòng lặp nhận thức & bầy đàn, đo lường & chi phí, các miền chuyên biệt, đến an ninh và bàn giao ứng dụng doanh nghiệp hoàn chỉnh.

---

## 🗺️ Bản Đồ Cấu Trúc Trụ Cột 3 (6 Mô-đun Sư Phạm & 27 Chuyên Đề)

```text
03-building-agents/
├── README.md                                         # (Tài liệu này) Giới thiệu tổng quan & lộ trình học Trụ cột 3
│
├── 01-harness-and-memory/                            # 🗄️ Mô-đun 01: Bộ khung điều khiển, Bộ nhớ nhận thức & Caching (5 bài)
│   ├── README.md                                     # MOC điều hướng Mô-đun 01
│   ├── 01_ai_chat_systems_and_prompt_engineering.md  # Tiến hóa hệ thống Chat, Harness & 4 tầng nhận thức
│   ├── 02_harness_architecture.md                    # Giải phẫu kiến trúc Harness & Session Lifecycle
│   ├── 03_context_management.md                      # Quản trị cửa sổ ngữ cảnh, bệnh lý & cô lập
│   ├── 04_memory_systems.md                          # Kiến trúc bộ nhớ nhận thức đa tầng (MemGPT/Zep)
│   └── 05_agent_runtime_parameters_and_prompt_caching.md # Siêu tham số suy luận, TTFT & Prompt Caching
│
├── 02-tools-and-mcp/                                 # 🔌 Mô-đun 02: Giao thức kết nối công cụ & Structured Outputs (4 bài)
│   ├── README.md                                     # MOC điều hướng Mô-đun 02
│   ├── 01_mcp_architecture.md                        # Kiến trúc giao thức Model Context Protocol (MCP) & FastMCP
│   ├── 02_constrained_decoding_and_structured_outputs.md # Cưỡng chế cú pháp Logit Masking (Outlines/GBNF/Jump-Forward)
│   ├── 03_dynamic_tool_retrieval_and_tool_rag.md     # Khai phá công cụ động Tool-RAG & Phân cấp Namespace
│   └── 04_sandboxed_tool_execution_wasm_and_microvm.md # Cách ly thực thi công cụ Wasm & MicroVM Firecracker
│
├── 03-loop-and-multi-agent-engineering/              # 🔄 Mô-đun 03: Vòng lặp nhận thức, Bầy đàn & Thực thi bền vững (9 bài)
│   ├── README.md                                     # MOC điều hướng Mô-đun 03
│   ├── 01_loop_fundamentals.md                       # Nền tảng vòng lặp tự trị, OODA & Circuit Breakers
│   ├── 02_react_and_planning.md                      # ReAct, Plan-and-Execute, Evaluator-Optimizer
│   ├── 03_multi_agent_teams.md                       # Kiến trúc đội ngũ đa tác tử (Orchestrator, Supervisor, Swarm)
│   ├── 04_multi_agent_debate_and_consensus.md        # Tranh biện đa tác tử, Borda Count & Cơ chế đồng thuận
│   ├── 05_ast_self_healing_code_agents.md            # Tác tử lập trình tự sửa lỗi qua Cây cú pháp trừu tượng AST
│   ├── 06_durable_execution_and_stateful_workflows.md # Máy trạng thái bền vững, Checkpointing & Time-Travel Debugging
│   ├── 07_state_merkle_trees_and_time_travel_debugging.md # Cây Merkle DAG bất biến & Quản trị phân nhánh phiên
│   ├── 08_mixture_of_agents_and_layered_routing.md   # Hợp tác nhận thức đa mô hình phân tầng Mixture-of-Agents (MoA)
│   └── 09_mcts_and_tree_search_reasoning_loops.md    # Tìm kiếm cây Monte Carlo (MCTS) cho tác tử tự hành
│
├── 04-observability-evals-and-cost/                  # 📊 Mô-đun 04: Quan sát, Đánh giá chất lượng & Tối ưu hóa chi phí (6 bài)
│   ├── README.md                                     # MOC điều hướng Mô-đun 04
│   ├── 01_agent_evals_and_tracing.md                 # Hạ tầng OpenTelemetry Tracing, Span Trees & Ragas Triad
│   ├── 02_synthetic_benchmarks_and_llm_as_judge.md   # Dữ liệu tổng hợp Evol-Instruct, LLM Judge Biases & CI/CD Evals
│   ├── 03_token_economics_and_cost_optimization.md  # Kinh tế học Token, Model Cascading & Budget Circuit Breakers
│   ├── 04_prompt_compression_and_cache_engineering.md # Nén ngữ cảnh LLMLingua, PagedAttention GPU & RadixTree
│   ├── 05_speculative_decoding_and_inference_acceleration.md # Speculative Decoding, Draft-Target Sampling & vLLM
│   └── 06_semantic_caching_and_vector_cache.md       # Bộ nhớ đệm ngữ nghĩa Semantic Cache & Phản hồi Zero-Token
│
├── 05-specialized-agent-domains/                     # 🎯 Mô-đun 05: Các miền tác tử kỹ thuật cao chuyên biệt (6 bài)
│   ├── README.md                                     # MOC điều hướng Mô-đun 05
│   ├── 01_code_graphs_and_repository_intelligence.md # Đồ thị mã nguồn SCIP, CPG, Repo Map PageRank
│   ├── 02_cross_session_memory_and_delta_caching.md  # Bộ nhớ đa phiên, Memory Bank Markdown & Git Merkle Delta
│   ├── 03_multimodal_gui_and_computer_use.md         # Tác tử trực quan Computer-Use, Set-of-Mark & OSWorld
│   ├── 04_browser_automation_and_web_agents.md       # Tác tử Web, Nén Accessibility Tree (AXTree) & Playwright
│   ├── 05_symbolic_ai_and_formal_verification.md     # Neuro-Symbolic, CEGIS Loop, Z3 SMT Solver & Lean 4
│   └── 06_on_device_and_edge_agents.md               # Tác tử cục bộ On-Device SLMs, WebGPU & NPU Acceleration
│
└── 06-governance-and-enterprise-delivery/            # 🛡️ Mô-đun 06: Quản trị, An ninh bảo mật & Triển khai doanh nghiệp (6 bài)
    ├── README.md                                     # MOC điều hướng Mô-đun 06
    ├── 01_hitl_and_hotl_human_agent_interaction.md   # Quản trị tương tác Human-in-the-Loop & Human-on-the-Loop
    ├── 02_agent_security_red_teaming_and_guardrails.md # Bảo mật tác tử, Dual-LLM Isolation & Sandbox Kernel
    ├── 03_how_to_build_enterprise_ai_agents.md       # Cẩm nang toàn diện xây dựng hệ thống AI Agent doanh nghiệp
    ├── 04_fullstack_agent_mern_architecture.md       # Ứng dụng Full-stack MERN, SSE Streaming ReAct UI & MCP Client
    ├── 05_adversarial_fuzzing_and_automated_agent_red_teaming.md # Kiểm thử thâm nhập tự động, PAIR/TAP Fuzzing & ADR Score
    └── 06_cryptographic_audit_trails_and_compliance.md # Sổ cái kiểm toán mật mã bất biến & Tuân thủ EU AI Act / SOC 2
```

---

## 📂 Danh Mục Phân Tích Chi Tiết 6 Mô-đun Theo Thứ Tự Đọc

### 1. [01-harness-and-memory - AI Harness & Memory Architecture](./01-harness-and-memory/README.md)
* **Trọng tâm:** Bộ khung phần mềm quản lý tương tác giữa người dùng và LLM Core, vòng đời phiên và hệ thống bộ nhớ đa tầng.
* **Tài liệu chi tiết:**
  * [01_ai_chat_systems_and_prompt_engineering.md](./01-harness-and-memory/01_ai_chat_systems_and_prompt_engineering.md): Khái niệm dẫn nhập về AI Harness, bộ nhớ nhận thức và 4 bước chuyển từ Prompting lên Agentic Loops.
  * [02_harness_architecture.md](./01-harness-and-memory/02_harness_architecture.md): Phân tách Lõi tĩnh vs Khung có trạng thái, 5 phân hệ phần mềm và Session Lifecycle.
  * [03_context_management.md](./01-harness-and-memory/03_context_management.md): Chẩn đoán 3 bệnh lý (Context Poisoning, Context Decay, Context Starvation), giải pháp RAG, Context Pruning, Summarization và kiến trúc Context Quarantine.
  * [04_memory_systems.md](./01-harness-and-memory/04_memory_systems.md): Mô hình 4 phân tầng Short-term, Working Memory (Scratchpad), Long-term Memory (Vector DB/Profile), MemGPT OS Virtual Memory Paging, và Bi-temporal Knowledge Graphs.
  * [05_agent_runtime_parameters_and_prompt_caching.md](./01-harness-and-memory/05_agent_runtime_parameters_and_prompt_caching.md): Bản chất Prefill $\mathcal{O}(N^2)$, cơ chế Prefix Caching (RadixTree) giảm 90% chi phí và TTFT từ 3.5s xuống 0.25s, quy tắc bất biến tiền tố (Static Prefix Invariance), giải phẫu siêu tham số (`temperature`, `top_p`, `max_tokens`, `stop`, cấm `penalties` trong Agent).

---

### 2. [02-tools-and-mcp - Tools, Protocol & Constrained Decoding](./02-tools-and-mcp/README.md)
* **Trọng tâm:** Kết nối tác tử với thế giới thực qua giao thức chuẩn mở, cách ly bảo mật và bảo đảm cú pháp JSON/Code $100\%$.
* **Tài liệu chi tiết:**
  * [01_mcp_architecture.md](./02-tools-and-mcp/01_mcp_architecture.md): Giải quyết bài toán phân mảnh $M \times N$, 3 primitives cốt lõi (Resources, Prompts, Tools), kiến trúc Client-Host-Server và FastMCP Python SDK.
  * [02_constrained_decoding_and_structured_outputs.md](./02-tools-and-mcp/02_constrained_decoding_and_structured_outputs.md): Ma trận Unembedding $\mathbf{W}_U$, mặt nạ Logit Masking triệt tiêu ảo giác JSON, biên dịch Regex sang FSM (Outlines), Pushdown Automata (GBNF) và tăng tốc Jump-Forward Decoding (SGLang).
  * [03_dynamic_tool_retrieval_and_tool_rag.md](./02-tools-and-mcp/03_dynamic_tool_retrieval_and_tool_rag.md): Mở rộng hệ thống lên hàng nghìn công cụ, Two-Stage Tool-RAG, Hybrid Retrieval (BM25 + Dense RRF), và phân cấp Hierarchical Tool Namespaces.
  * [04_sandboxed_tool_execution_wasm_and_microvm.md](./02-tools-and-mcp/04_sandboxed_tool_execution_wasm_and_microvm.md): Cách ly thực thi công cụ nguy hiểm bằng WebAssembly (Wasm/WASI) và MicroVMs (Firecracker), Capability-based Security và Watchdog Timer.

---

### 3. [03-loop-and-multi-agent-engineering - Vòng Lặp Nhận Thức, Bầy Đàn & Thực Thi Bền Vững](./03-loop-and-multi-agent-engineering/README.md)
* **Trọng tâm:** Biến LLM từ bộ máy trả lời một lần thành động cơ tự hành liên tục, phối hợp đa tác tử và chịu lỗi phân tán.
* **Tài liệu chi tiết:**
  * [01_loop_fundamentals.md](./03-loop-and-multi-agent-engineering/01_loop_fundamentals.md): Từ One-shot sang Recursive Execution, chu trình OODA 5 bước, 4 tầng Stopping Criteria và bộ ngắt mạch chống lặp vô tận.
  * [02_react_and_planning.md](./03-loop-and-multi-agent-engineering/02_react_and_planning.md): So sánh định lượng và ma trận đánh đổi giữa ReAct, Plan-and-Execute, và Evaluator-Optimizer.
  * [03_multi_agent_teams.md](./03-loop-and-multi-agent-engineering/03_multi_agent_teams.md): Phân công lao động nhận thức qua mô hình Orchestrator-Worker, Supervisor Hierarchy, Swarm Handoffs và kỹ thuật Context Quarantine.
  * [04_multi_agent_debate_and_consensus.md](./03-loop-and-multi-agent-engineering/04_multi_agent_debate_and_consensus.md): Lý thuyết trò chơi trong tranh biện AI, phá vỡ thiên kiến xác nhận đơn lẻ, Majority Voting, Elo-weighted Consensus và Delphi Method.
  * [05_ast_self_healing_code_agents.md](./03-loop-and-multi-agent-engineering/05_ast_self_healing_code_agents.md): Phòng chống Cascading Regressions, 4 tầng kiểm định (AST Syntax Gate $< 1\text{ms}$, Static Typing, Sandboxed Traceback, Test Verification), ACI Interface (SWE-agent), Repo Map (Aider).
  * [06_durable_execution_and_stateful_workflows.md](./03-loop-and-multi-agent-engineering/06_durable_execution_and_stateful_workflows.md): Triết lý Durable Execution ("chạy như thể không bao giờ sập"), máy trạng thái State Graphs $\mathcal{S}_t$, Event-sourcing Checkpointers, Replay Determinism & Observation Caching, Time-Travel Debugging.
  * [07_state_merkle_trees_and_time_travel_debugging.md](./03-loop-and-multi-agent-engineering/07_state_merkle_trees_and_time_travel_debugging.md): Quản trị trạng thái bất biến dạng Merkle DAG, mã băm mật mã SHA-256, chia sẻ cấu trúc vi phân tiết kiệm 95% lưu trữ, và phân nhánh Git-like (`fork_branch`).
  * [08_mixture_of_agents_and_layered_routing.md](./03-loop-and-multi-agent-engineering/08_mixture_of_agents_and_layered_routing.md): Hiện tượng hợp tác nhận thức (Collaborativeness), kiến trúc Layered DAG Proposers-Refiners-Synthesizer, và Asymmetric Cost Funnel.
  * [09_mcts_and_tree_search_reasoning_loops.md](./03-loop-and-multi-agent-engineering/09_mcts_and_tree_search_reasoning_loops.md): Vòng lặp tìm kiếm cây Monte Carlo (MCTS) cho tác tử tự hành, công thức chọn PUCT và mô phỏng đánh giá Rollout/PRM.

---

### 4. [04-observability-evals-and-cost - Quan Sát, Đánh Giá Chất Lượng & Chi Phí](./04-observability-evals-and-cost/README.md)
* **Trọng tâm:** Đo lường định lượng, Tracing phân tán, thẩm định tự động chất lượng Agent và tối ưu hóa ngân sách & tốc độ suy luận.
* **Tài liệu chi tiết:**
  * [01_agent_evals_and_tracing.md](./04-observability-evals-and-cost/01_agent_evals_and_tracing.md): Chuẩn OpenTelemetry GenAI Semantic Conventions, Cây vết (Trace Tree), tích hợp Langfuse Tracing, bộ chỉ số Ragas Triad, và benchmark SWE-bench/GAIA.
  * [02_synthetic_benchmarks_and_llm_as_judge.md](./04-observability-evals-and-cost/02_synthetic_benchmarks_and_llm_as_judge.md): Sinh dữ liệu kiểm thử Evol-Instruct, 4 thiên kiến của LLM Judge (Position, Verbosity, Self-enhancement, Egocentric), Swap Testing, G-Eval Softmax Logits và CI/CD regression testing.
  * [03_token_economics_and_cost_optimization.md](./04-observability-evals-and-cost/03_token_economics_and_cost_optimization.md): Mô hình toán học chi phí vòng lặp $O(N^2)$, định tuyến phân tầng Model Cascading (Big Brain vs Small Brain), Budget Circuit Breakers.
  * [04_prompt_compression_and_cache_engineering.md](./04-observability-evals-and-cost/04_prompt_compression_and_cache_engineering.md): Cơ sở toán học Shannon Entropy, nén ngữ cảnh LLMLingua cắt giảm 80% tokens, kiến trúc GPU KV-cache PagedAttention (vLLM) và cấu trúc dữ liệu RadixTree.
  * [05_speculative_decoding_and_inference_acceleration.md](./04-observability-evals-and-cost/05_speculative_decoding_and_inference_acceleration.md): Giải quyết nghẽn Memory-Bandwidth trong pha Decode, thuật toán Speculative Sampling kết hợp Draft-Target Models, Tree-based Attention và Medusa Heads tăng tốc $2.5\times - 4\times$.
  * [06_semantic_caching_and_vector_cache.md](./04-observability-evals-and-cost/06_semantic_caching_and_vector_cache.md): Bộ nhớ đệm ngữ nghĩa Semantic Cache, hiệu chuẩn ngưỡng $\tau$, tra cứu Sub-millisecond bằng LSH và tiết kiệm 100% token cho các truy vấn trùng lặp.

---

### 5. [05-specialized-agent-domains - Các Miền Tác Tử Chuyên Biệt](./05-specialized-agent-domains/README.md)
* **Trọng tâm:** Vượt ra ngoài text thuần để làm chủ mã nguồn quy mô lớn, tương tác màn hình hệ điều hành, trình duyệt web và suy luận toán học tất định.
* **Tài liệu chi tiết:**
  * [01_code_graphs_and_repository_intelligence.md](./05-specialized-agent-domains/01_code_graphs_and_repository_intelligence.md): Cây cú pháp Tree-sitter, giao thức định danh công nghiệp SCIP/LSIF, Code Knowledge Graph, và thuật toán PageRank trên đồ thị code sinh Repo Map tinh gọn.
  * [02_cross_session_memory_and_delta_caching.md](./05-specialized-agent-domains/02_cross_session_memory_and_delta_caching.md): Giải quyết bài toán Session Boundary, hệ thống Memory Bank Markdown, Git Merkle DAG Delta Caching (tiết kiệm 97% chi phí parse), và lưu trữ `failed_hypotheses`.
  * [03_multimodal_gui_and_computer_use.md](./05-specialized-agent-domains/03_multimodal_gui_and_computer_use.md): Tác tử thị giác Computer-Use, Set-of-Mark (SoM) Prompting, OmniParser, Tọa độ chuẩn hóa $[0, 1000]$, và xử lý độ trễ render trên desktop OS.
  * [04_browser_automation_and_web_agents.md](./05-specialized-agent-domains/04_browser_automation_and_web_agents.md): Tự động hóa trình duyệt web qua Playwright/CDP, nén DOM khổng lồ bằng Accessibility Tree (AXTree) giảm 90% token, Set-of-Mark web grounding, và cơ chế stealth chống bot fingerprinting.
  * [05_symbolic_ai_and_formal_verification.md](./05-specialized-agent-domains/05_symbolic_ai_and_formal_verification.md): Kiến trúc Neuro-Symbolic, vòng lặp CEGIS (Counterexample-Guided Inductive Synthesis), giải bài toán ràng buộc đa chiều với Z3 SMT Solver và chứng minh hình thức với Lean 4.
  * [06_on_device_and_edge_agents.md](./05-specialized-agent-domains/06_on_device_and_edge_agents.md): Tác tử cục bộ On-Device SLMs (SmolLM2, Qwen-Coder, Phi-3.5), WebGPU trong trình duyệt, NPU acceleration, và kiến trúc định tuyến lai Local-First.

---

### 6. [06-governance-and-enterprise-delivery - Quản Trị, An Ninh & Bàn Giao Doanh Nghiệp](./06-governance-and-enterprise-delivery/README.md)
* **Trọng tâm:** Chuyển giao hệ thống từ nguyên mẫu thí nghiệm (PoC) sang hạ tầng doanh nghiệp tuân thủ và bảo mật tối đa.
* **Tài liệu chi tiết:**
  * [01_hitl_and_hotl_human_agent_interaction.md](./06-governance-and-enterprise-delivery/01_hitl_and_hotl_human_agent_interaction.md): Khủng hoảng The Autonomy Dilemma, 3 mô hình tương tác HITL / HOTL / HOOTL, ma trận phân loại rủi ro 4 cấp (Tiered Risk Matrix), và Webhook phê duyệt bất đồng bộ.
  * [02_agent_security_red_teaming_and_guardrails.md](./06-governance-and-enterprise-delivery/02_agent_security_red_teaming_and_guardrails.md): Phòng chống Indirect Prompt Injection (IPI), kiến trúc Dual-LLM (Privileged vs Quarantined), rò rỉ dữ liệu qua thẻ ảnh Markdown, Canary Tokens, và MicroVM/gVisor Sandboxing.
  * [03_how_to_build_enterprise_ai_agents.md](./06-governance-and-enterprise-delivery/03_how_to_build_enterprise_ai_agents.md): Cẩm nang kiến trúc 6 phòng ban doanh nghiệp, Microservices phân tán, quản trị SLA/ngân sách, và tuân thủ ISO 42001 / SOC 2 Type II.
  * [04_fullstack_agent_mern_architecture.md](./06-governance-and-enterprise-delivery/04_fullstack_agent_mern_architecture.md): Ứng dụng Full-stack MERN hoàn chỉnh: MongoDB Atlas Vector Store, Express API, React UI streaming ReAct và tích hợp giao thức MCP Client qua Node.js.
  * [05_adversarial_fuzzing_and_automated_agent_red_teaming.md](./06-governance-and-enterprise-delivery/05_adversarial_fuzzing_and_automated_agent_red_teaming.md): Kiểm thử thâm nhập tự động cho tác tử, giải thuật đột biến đối kháng (PAIR, TAP, GCG), bắn phá tham số công cụ (Tool-Exploit Fuzzing) và đo lường chỉ số phòng thủ ADR.
  * [06_cryptographic_audit_trails_and_compliance.md](./06-governance-and-enterprise-delivery/06_cryptographic_audit_trails_and_compliance.md): Sổ cái kiểm toán mật mã bất biến, chuỗi băm Hash Chaining SHA-256, làm mờ dữ liệu cá nhân PII và tuân thủ EU AI Act / SOC 2 Type II.

---

## 🔗 Điều Hướng Nhanh Toàn Khóa Học
* Quay lại Trụ cột 1: [🔬 Trụ Cột 1: Research & Foundations](../01-research-and-foundations/README.md)
* Quay lại Trụ cột 2: [📝 Trụ Cột 2: Prompt & Context Engineering](../02-prompt-and-context/README.md)
* Trở về trang chủ Vault: [🏠 Vault Home MOC](../README.md)
* Xem bản đồ Canvas toàn cảnh: [🗺️ Mở Visual Canvas](../Agent-Course-Overview.canvas)
