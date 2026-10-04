---
title: "Agent Course: From Foundations to Autonomous AI Agents"
aliases:
  - Agent Course MOC
  - Vault Home
tags:
  - agent-course
  - moc
type: moc
created: 2026-09-20
updated: 2026-09-21
---

# Agent Course: From Foundations to Autonomous AI Agents

Kho tài liệu học tập, nghiên cứu và thực hành toàn diện về **Trí tuệ nhân tạo (AI)** được tối ưu hóa chuẩn **Obsidian Vault**: từ nền tảng **Học sâu & Mạng nơ-ron (Deep Learning & Neural Networks)**, kỹ thuật **Prompt & Context Engineering**, cho đến kiến trúc xây dựng **Hệ thống Tác tử Tự trị (Autonomous Agents & MCP)**.

> [!tip] Cấu Trúc Blog & Kho Tri Thức Markdown
> * 📚 **Blog / Knowledge Base:** Toàn bộ nội dung là các bài viết Markdown chuẩn hóa, phân cấp logic, dễ dàng đọc trực tiếp trên GitHub hoặc mở bằng bất kỳ trình đọc Markdown / Static Site Generator nào.
> * 🏷️ **Tags phân loại:** `#agent-course` `#research/neural-networks` `#research/llm` `#prompt-engineering` `#building-agents`

---

## 🗺️ Bản Đồ Kiến Trúc Kho Tài Liệu (3 Trụ Cột)

Repository được tổ chức theo cấu trúc blog phân tầng 3 trụ cột logic:

```text
agent_course/
├── README.md                                          # Mục lục tổng quan (Blog Root MOC)
│
├── 01-research-and-foundations/                       # 🔬 TRỤ CỘT 1: NGHIÊN CỨU & NỀN TẢNG HỌC THUẬT
│   ├── README.md                                      # Tổng quan & Lộ trình Trụ cột 1
│   ├── 01-neural-networks/                            # 🧠 Mạng Nơ-ron Nhân tạo (ANN, CNN, RNN, Transformers, MoE)
│   │   ├── README.md
│   │   └── neural_networks_and_classifications.md     # Giải phẫu nơ-ron, Backpropagation, Hàm kích hoạt, Bản đồ phân loại
│   ├── 02-llm-internals/                              # 📚 Bản chất Mô hình Ngôn ngữ Lớn (LLM Core & Pre-training)
│   │   ├── README.md
│   │   ├── what_are_large_language_models.md          # Thí nghiệm điền từ, Transformer, AR vs AE, Scaling, Reasoning
│   │   ├── 04_transformer_math_deep_dive.md           # Toán học Scaled Dot-Product, FlashAttention & KV-Cache
│   │   ├── 05_scaling_laws_and_quantization.md        # Định luật Chinchilla, Lượng tử hóa GPTQ/AWQ & GGUF
│   │   └── 06_synthetic_data_and_agent_alignment.md   # Dữ liệu tổng hợp, Multi-Agent Self-Play & DPO/ORPO
│   └── 03-semantic-search/                            # 🔍 Tìm kiếm Ngữ nghĩa & Tái xếp hạng (Vector Retrieval & Re-ranking)
│       ├── README.md                                  # Hướng dẫn chuyên đề & thứ tự đọc
│       ├── 01_semantic_search_and_reranking.md        # Bài 1: Bi-Encoder vs Cross-Encoder, Two-Stage Pipeline & Advanced RAG
│       └── 02_rag_architecture_and_components.md     # Bài 2: Giải phẫu 4 cấu phần RAG (Inside RAG) & Vòng lặp điều phối
│
├── 02-prompt-and-context/                             # ✍️ TRỤ CỘT 2: KỸ THUẬT CÂU LỆNH & QUẢN TRỊ NGỮ CẢNH
│   ├── README.md                                      # Tổng quan & Lộ trình Trụ cột 2
│   └── 01-prompt-engineering/                         # 🎯 Kỹ thuật Prompt Engineering nâng cao
│       ├── README.md                                  # Danh mục các kỹ thuật & Lộ trình
│       ├── advanced_prompt_engineering_techniques.md  # Cẩm nang 10 kỹ thuật (CoT, ToT, Lost-in-Middle, Meta-Prompting)
│       └── 02_dspy_and_programmatic_prompting.md      # Lập trình hóa Prompt với DSPy (Stanford NLP) & Tối ưu hóa tự động
│
└── 03-building-agents/                                # 🛠️ TRỤ CỘT 3: KỸ THUẬT XÂY DỰNG TÁC TỬ TỰ HÀNH
    ├── README.md                                      # Tổng quan & Lộ trình Trụ cột 3
    ├── 00_ai_chat_systems_and_prompt_engineering.md   # 🏛️ Bài 00 (Nhập môn): Dẫn nhập kiến trúc Harness, Memory & 4 tầng tiến hóa
    ├── 01-harness-and-memory/                         # 🗄️ Tầng 1: Bộ khung điều khiển & Hệ thống ghi nhớ
    │   ├── README.md
    │   ├── 01_harness_architecture.md
    │   ├── 02_context_management.md
    │   ├── 03_memory_systems.md
    │   └── 04_agent_runtime_parameters_and_prompt_caching.md
    ├── 02-tools-and-mcp/                              # 🔌 Tầng 2: Giao thức kết nối công cụ & thế giới thực
    │   ├── README.md
    │   ├── 01_mcp_architecture.md
    │   └── 02_constrained_decoding_and_structured_outputs.md
    ├── 03-loop-engineering/                           # 🔄 Tầng 3: Vòng lặp tự trị & Đội ngũ đa tác tử
    │   ├── README.md
    │   ├── 01_loop_fundamentals.md
    │   ├── 02_react_and_planning.md
    │   ├── 03_multi_agent_teams.md
    │   ├── 04_ast_self_healing_code_agents.md
    │   └── 05_durable_execution_and_stateful_workflows.md
    ├── 04-observability-and-evals/                    # 📊 Tầng 4: Giám sát vết & Đánh giá chất lượng
    │   ├── README.md
    │   └── 01_agent_evals_and_tracing.md
    ├── 05-multimodal-gui-agents/                      # 🖥️ Tầng 5: Tác tử đa phương thức & Computer-Use
    │   ├── README.md
    │   └── 01_multimodal_gui_and_computer_use.md
    └── 06_how_to_build_enterprise_ai_agents.md        # 🏗️ Bài 06 (Tổng kết): CẨM NANG TOÀN TẬP kiến trúc khối, 6 phòng ban & Production
```

---

## 📖 Danh Mục Tài Liệu Cốt Lõi (Wikilinks)

### 🔬 [[01-research-and-foundations/README|Trụ cột 1: Research & Foundations]]
* [[neural_networks_and_classifications|Neural Networks & Their Classifications]]: Giải phẫu nơ-ron nhân tạo, Forward Pass, Backpropagation & Chain Rule, các hàm kích hoạt (ReLU, GELU, SwiGLU), hàm mất mát, giải thuật tối ưu (SGD, AdamW), và bản đồ 8 họ kiến trúc từ MLP, CNN, RNN đến Transformer, GNN, Autoencoders, GAN, Diffusion và MoE.
* [[what_are_large_language_models|What Are Large Language Models?]]: Bản chất Language Modeling (Fill-in-the-blank), Subword Tokenization toàn diện (BPE/BBPE, WordPiece, SentencePiece/Unigram LM), các lỗi hệ thống kinh điển (nghịch lý đếm chữ "Strawberry", tính toán số học đa chữ số, thuế token đa ngôn ngữ), 4 bước nhảy vọt lịch sử (2001–2017), so sánh chuyên sâu Autoregressive (GPT) vs. Autoencoding (BERT) vs. Seq2Seq (T5), quy mô tham số, siêu tham số suy luận (`temperature`, `top_p`), và bản chất "Reasoning Machine".
  * [[04_transformer_math_deep_dive|Giải Phẫu Toán Học Của Transformer]]: Vi tích phân Scaled Dot-Product, chứng minh chia cho $\sqrt{d_k}$, phân tích Jacobian của Softmax, MHA/MQA/GQA, cơ chế quay tọa độ RoPE, **thuật toán Online Softmax & Tiling của FlashAttention (1-3)** và **toán học định lượng kích thước KV-Cache kết hợp giải thuật PagedAttention (vLLM)**.
  * [[05_scaling_laws_and_quantization|Định Luật Tỷ Lệ & Kỹ Thuật Lượng Tử Hóa]]: Định luật Chinchilla ($D \approx 20N$), xu hướng Over-training của LLaMA-3, toán học Quantization Affine, giải thuật GPTQ, AWQ, và chuẩn GGUF/llama.cpp.
  * [[06_synthetic_data_and_agent_alignment|Dữ Liệu Tổng Hợp & Căn Chỉnh Tác Tử]]: Khủng hoảng The Data Wall 2026-2028, giải thuật tiến hóa Evol-Instruct (WizardLM), Multi-Agent Self-Play tạo quỹ đạo công cụ, UltraFeedback, chứng minh toán học giải tích DPO, thuật toán ORPO và chắt lọc năng lực Tool Distillation cho mô hình 8B.
* [[01_semantic_search_and_reranking|01_semantic_search_and_reranking - Semantic Search & Advanced RAG Architectures]]: Nghịch lý khớp từ khóa ("Vintage Magic Card"), Vector Embeddings & Lời nguyền số chiều, hiện tượng Dị hướng không gian (Anisotropy "hình nón hẹp") & giải pháp làm trắng BERT-Whitening, Asymmetric vs Symmetric Search, so sánh Bi-Encoder vs Cross-Encoder, Two-Stage Pipeline, chiến lược Chunking, thực nghiệm định lượng Recall@K, và **Cẩm nang toàn tập Kiến trúc RAG Tiên tiến** (HyDE, Parent Document Retrieval, Anthropic Contextual Retrieval, Microsoft GraphRAG, Reciprocal Rank Fusion, Self-RAG, Corrective RAG / CRAG, Adaptive RAG, Ma trận so sánh định lượng và Cây quyết định kiến trúc thực chiến).
* [[02_rag_architecture_and_components|02_rag_architecture_and_components - Inside RAG: Kiến Trúc 4 Cấu Phần & Vòng Lặp Điều Phối]]: Giải phẫu 4 cấu phần cốt lõi của RAG (Embeddings/FAISS Retriever, Cohere Reranker, ChatOpenAI Generator, RetrievalQA Orchestrator), mô hình tư duy "Kỳ thi mở sách" (Open-Book Exam), vũ điệu 4 nhịp `Retrieve` $\to$ `Rank` $\to$ `Generate` $\to$ `Orchestrate`, pipeline LangChain mẫu mực, và ca nghiên cứu nông nghiệp thẳng đứng (Vertical Farming & IPM).

### ✍️ [[02-prompt-and-context/README|Trụ cột 2: Prompt & Context Engineering]]
* [[advanced_prompt_engineering_techniques|Các Kỹ Thuật Prompt & Context Engineering Nâng Cao (Toàn Tập)]]: Cẩm nang toàn diện 10 kỹ thuật: Zero/Few-shot (In-Context Learning), CoT Family (Zero-shot, Few-shot, Hybrid), OPRO, Generated Knowledge, Tree of Thoughts (ToT), Directional Stimulus (DSP), Chain of Density (CoD), Quản trị Cửa sổ Ngữ cảnh & khắc phục **Lost in the Middle** (Token Budgeting), và thiết kế **System Instructions chuẩn thẻ XML kết hợp Meta-Prompting**.
* [[02_dspy_and_programmatic_prompting|Lập Trình Hóa Prompt Với DSPy (Stanford NLP) & Tối Ưu Hóa Tự Động]]: Chấm dứt kỷ nguyên Prompt Crafting thủ công; triết lý Compiler cho LLM phân ly Logic và Trọng số; 3 cấu phần Signatures, Modules (`Predict`, `ChainOfThought`, `ReAct`, `ProgramOfThought`) & Optimizers (`BootstrapFewShot`, `MIPROv2` Bayesian Instruction Optimization, `COPRO`/APE); bài tập thực chiến RAG Agent & chưng cất tri thức sang LLaMA-3 cục bộ.

### 🛠️ [[03-building-agents/README|Trụ cột 3: Building Agents]]
* [[00_ai_chat_systems_and_prompt_engineering|00_ai_chat_systems_and_prompt_engineering - Kiến trúc & Tiến hóa của các hệ thống AI Chat]]: **Tài liệu dẫn nhập kiến trúc:** Phân tích bản chất One-shot của LLM Core, giải phẫu AI Harness, cơ chế Memory (Dynamic & Semantic), SKILLS/Tools và 4 tầng tiến hóa từ Prompting đến Loop Engineering.
* [[03-building-agents/01-harness-and-memory/README|01-harness-and-memory - AI Harness & Memory Architecture]]: Bộ khung phần mềm, quản trị cửa sổ ngữ cảnh và phòng chống Context Drift.
  * [[01_harness_architecture|Giải Phẫu Kiến Trúc AI Harness]]: Phân tách Lõi tĩnh vs Khung có trạng thái, 5 phân hệ phần mềm và Session Lifecycle.
  * [[02_context_management|Quản Trị Cửa Sổ Ngữ Cảnh: Bệnh Lý, Tỉa Nhánh, Tóm Tắt & Cô Lập]]: Chẩn đoán 3 bệnh lý (Context Poisoning, Context Decay, Context Starvation), giải pháp RAG, Context Pruning, Summarization và kiến trúc Context Quarantine.
  * [[03_memory_systems|Kiến Trúc Bộ Nhớ Đa Tầng Cho AI Agents]]: Mô hình 4 phân tầng nhận thức, quản trị bộ nhớ ảo MemGPT (Context Paging & Core Memory Tools), công thức chấm điểm Generative Agents $\alpha_{\text{rec}} R + \alpha_{\text{imp}} I + \alpha_{\text{rel}} S$, Đồ thị tri thức có nhận thức thời gian (Bi-temporal Knowledge Graph: Zep/Mem0) và chu trình củng cố ký ức ban đêm (Sleep Cycles).
  * [[04_agent_runtime_parameters_and_prompt_caching|Tham Số Vận Hành Tác Tử & Tối Ưu Hóa Prompt Caching]]: Khủng hoảng Prefill $O(N^2)$, cơ chế Prefix Caching (RadixTree) giảm 90% chi phí và TTFT từ 3.5s xuống 0.25s, quy tắc bất biến tiền tố (Static Prefix Invariance), giải phẫu siêu tham số (`temperature`, `top_p`, `max_tokens`, `stop`, cấm `penalties` trong Agent) và kịch bản đo lường hiệu năng thời gian thực.
* [[03-building-agents/02-tools-and-mcp/README|02-tools-and-mcp - Model Context Protocol (MCP) & Tools]]: Giao thức chuẩn mở của Anthropic kết nối LLM với công cụ và dữ liệu ngoài.
  * [[01_mcp_architecture|Kiến Trúc Giao Thức Model Context Protocol (MCP)]]: Khảo sát bài toán tích hợp $N \times M$, tam giác Host-Client-Server, 3 cấu phần nguyên thủy (Tools, Resources, Prompts), cơ chế truyền tải stdio/SSE, giải phẫu JSON-RPC 2.0 và code mẫu FastMCP Python.
  * [[02_constrained_decoding_and_structured_outputs|Constrained Decoding & Grammar-Guided Structured Outputs]]: Bản chất tầng Logits và ma trận Unembedding $\mathbf{W}_U$, mặt nạ nhị phân Logit Masking triệt tiêu $100\%$ lỗi cú pháp JSON/Tool Calling, biên dịch Regex sang FSM (Outlines), Pushdown Automata (llama.cpp GBNF) và tăng tốc Jump-Forward Decoding (SGLang).
* [[03-building-agents/03-loop-engineering/README|03-loop-engineering - Loop Engineering & Autonomous Agents]]: Vòng lặp phản hồi tự trị: ReAct, Plan-and-Execute, Evaluator-Optimizer và Multi-agent workflows.
  * [[01_loop_fundamentals|Nền Tảng Loop Engineering: Vòng Lặp Tự Trị, Điều Kiện Dừng & Circuit Breakers]]: Từ One-shot sang Recursive Execution, 4 tầng Stopping Criteria và bộ ngắt mạch chống lặp vô tận.
  * [[02_react_and_planning|Các Mô Hình Vòng Lặp Cốt Lõi (ReAct, Plan-and-Execute, Evaluator-Optimizer)]]: So sánh định lượng và ma trận đánh đổi giữa ReAct, Plan-and-Execute, và Evaluator-Optimizer.
  * [[03_multi_agent_teams|Kiến Trúc Đội Ngũ Đa Tác Tử (Multi-Agent Systems)]]: Phân công lao động nhận thức qua mô hình Orchestrator-Worker, Supervisor Hierarchy, Swarm Handoffs và kỹ thuật Context Quarantine.
  * [[04_ast_self_healing_code_agents|Tác Tử Lập Trình Tự Sửa Lỗi Qua Cây Cú Pháp Trừu Tượng (AST)]]: Phòng chống Cascading Regressions, 4 tầng kiểm định (AST Syntax Gate $< 1\text{ms}$, Static Typing, Sandboxed Traceback, Test Verification), ACI Interface (SWE-agent), Repo Map (Aider) và Verbal RL (Reflexion).
  * [[05_durable_execution_and_stateful_workflows|Thực Thi Bền Vững & Stateful Workflows]]: Triết lý Durable Execution ("chạy như thể không bao giờ sập"), máy trạng thái State Graphs $\mathcal{S}_t$, Event-sourcing Checkpointers, Replay Determinism & Observation Caching chống lặp tác dụng phụ ngoại vi, Time-Travel Debugging và Human-in-the-Loop Interrupts (`interrupt_before`).
* [[03-building-agents/04-observability-and-evals/README|04-observability-and-evals - Agent Observability, Evals & Governance]]: Đo lường định lượng, Tracing phân tán và thẩm định tự động chất lượng Agent trên Production.
  * [[01_agent_evals_and_tracing|Hệ Thống Giám Sát, Đo Lường & Đánh Giá Tác Tử AI]]: Chuẩn OpenTelemetry GenAI Semantic Conventions, Cây vết (Trace Tree), tích hợp Langfuse Tracing, bộ chỉ số Ragas Triad, giải phẫu 4 thiên vị LLM-as-a-Judge, kỹ thuật G-Eval xác suất Softmax, benchmark SWE-bench/GAIA và phương pháp sinh tập kiểm thử tổng hợp (Synthetic Testset).
* [[03-building-agents/05-multimodal-gui-agents/README|05-multimodal-gui-agents - Multimodal GUI Agents & Computer-Use]]: Tác tử đa phương thức nhìn màn hình (Pixels) và tương tác hệ điều hành như người dùng thật.
  * [[01_multimodal_gui_and_computer_use|Kỷ Nguyên Tác Tử Tương Tác Trực Quan Màn Hình & Hệ Điều Hành]]: Nghịch lý "Vật chất tối của API", Visual UI Grounding, Set-of-Mark (SoM) Prompting, OmniParser, Tọa độ chuẩn hóa $[0, 1000] \times [0, 1000]$, Không gian hành động nguyên thủy (Atomic Action Space), phòng chống Render Latency, Frame Differencing tiết kiệm 85% token và đánh giá benchmark OSWorld.
* [[06_how_to_build_enterprise_ai_agents|06_how_to_build_enterprise_ai_agents - Cẩm Nang Toàn Tập Xây Dựng AI Agent Doanh Nghiệp (Enterprise AI Agent Blueprint)]]: **Bản thiết kế tổng hợp & Capstone Production:** Sơ đồ khối 6 tầng, thích ứng chuyên sâu 6 phòng ban (Sales, HR, Finance, Legal, CS/IT, Engineering), AI Design Patterns (ReAct, Plan-and-Execute, Evaluator-Optimizer, Multi-Agent), 5 thất bại hệ thống kinh điển & chiến lược phòng vệ, quy trình 6 giai đoạn đưa Agent từ Prototype lên Production.

