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

> [!important] 🏛️ Bản Đồ Kiến Trúc Toàn Cảnh (The Master Architecture Blueprint)
> Để hiểu rõ bức tranh vĩ mô và mối liên hệ nhân - quả ngầm giữa **toàn bộ các thành phần** trong repository (từ Transformer Math, 4 thế hệ Chunking, Hybrid RAG, DSPy, Cognitive Memory, MCP 4 bước, ReAct Loops, AST Self-Healing cho đến MERN Stack & Evals), hãy xem cẩm nang tổng hợp:
> 👉 [**MASTER_ARCHITECTURE_AND_COMPONENTS.md - Bản Đồ Kiến Trúc Toàn Cảnh AI Agent**](MASTER_ARCHITECTURE_AND_COMPONENTS.md)

---

## 🗺️ Bản Đồ Kiến Trúc Kho Tài Liệu (3 Trụ Cột)

Repository được tổ chức theo cấu trúc blog phân tầng 3 trụ cột logic:

```text
agent_course/
├── README.md                                          # Mục lục tổng quan (Blog Root MOC)
│
├── 01-research-and-foundations/                       # 🔬 TRỤ CỘT 1: NGHIÊN CỨU & NỀN TẢNG HỌC THUẬT (16 bài)
│   ├── README.md                                      # Tổng quan & Lộ trình Trụ cột 1
│   ├── 01-neural-networks/                            # 🧠 Mạng Nơ-ron Nhân tạo (ANN, CNN, RNN, Transformers, MoE)
│   │   ├── README.md
│   │   └── 01_neural_networks_and_classifications.md     # Giải phẫu nơ-ron, Backpropagation, Hàm kích hoạt, Bản đồ phân loại
│   ├── 02-llm-internals/                              # 📚 Bản chất Mô hình Ngôn ngữ Lớn (LLM Core & Pre-training - 5 bài)
│   │   ├── README.md
│   │   ├── 01_what_are_large_language_models.md          # Thí nghiệm điền từ, Transformer, AR vs AE, Scaling, Reasoning
│   │   ├── 02_transformer_math_deep_dive.md           # Toán học Scaled Dot-Product, FlashAttention & KV-Cache
│   │   ├── 03_scaling_laws_and_quantization.md        # Định luật Chinchilla, Lượng tử hóa GPTQ/AWQ & GGUF
│   │   ├── 04_synthetic_data_and_agent_alignment.md   # Dữ liệu tổng hợp, Multi-Agent Self-Play & DPO/ORPO
│   │   └── 05_test_time_compute_and_process_reward_models.md # Test-Time Compute, PRMs & Step-level Search
│   └── 03-semantic-search/                            # 🔍 Tìm kiếm Ngữ nghĩa & Tái xếp hạng (Vector Retrieval & Re-ranking - 10 bài)
│       ├── README.md                                  # Hướng dẫn chuyên đề & thứ tự đọc
│       ├── 01_semantic_search_and_reranking.md        # Bài 1: Bi-Encoder vs Cross-Encoder, Two-Stage Pipeline & Advanced RAG
│       ├── 02_rag_architecture_and_components.md     # Bài 2: Giải phẫu 4 cấu phần RAG (Inside RAG) & Vòng lặp điều phối
│       ├── 03_embeddings_and_vector_databases.md     # Bài 3: Chiến lược Indexing (Flat, IVF, HNSW, PQ) & Khung FICE
│       ├── 04_how_database_and_embedding_choices_affect_rag.md # Bài 4: BGE vs MiniLM & Vận hành Ngày-2
│       ├── 05_theory_to_practice_making_rag_work.md  # Bài 5: Tam giác Retrieval Trilemma & Structure-Aware Chunking
│       ├── 06_maintaining_vector_indices_in_rag.md   # Bài 6: Trôi dạt dữ liệu (Content/Model/Perf Drift) & Zero-Downtime
│       ├── 07_optimizing_and_modularizing_rag_with_langchain.md # Bài 7: Pipeline LCEL, Local Embeddings & Context Compression
│       ├── 08_advanced_retrieval_tactics_for_rag.md  # Bài 8: Hybrid Search (RRF), Cross-Encoder Re-rank & Query Expansion
│       ├── 09_evaluating_and_optimizing_rag_systems.md # Bài 9: Golden Test Sets, Citation Tracking & Ragas Triad
│       └── 10_late_interaction_and_colbert_retrieval.md # Bài 10: Tương tác muộn ColBERTv2, MaxSim & PLAID Engine
│
├── 02-prompt-and-context/                             # ✍️ TRỤ CỘT 2: KỸ THUẬT CÂU LỆNH & QUẢN TRỊ NGỮ CẢNH (2 bài)
│   ├── README.md                                      # Tổng quan & Lộ trình Trụ cột 2
│   └── 01-prompt-engineering/                         # 🎯 Kỹ thuật Prompt Engineering nâng cao
│       ├── README.md                                  # Danh mục các kỹ thuật & Lộ trình
│       ├── 01_advanced_prompt_engineering_techniques.md  # Cẩm nang 10 kỹ thuật (CoT, ToT, Lost-in-Middle, Meta-Prompting)
│       └── 02_dspy_and_programmatic_prompting.md      # Lập trình hóa Prompt với DSPy (Stanford NLP) & Tối ưu hóa tự động
│
└── 03-building-agents/                                # 🛠️ TRỤ CỘT 3: KỸ THUẬT XÂY DỰNG TÁC TỬ TỰ HÀNH (36 bài)
    ├── README.md                                      # Tổng quan & Lộ trình Trụ cột 3
    ├── 01-harness-and-memory/                         # 🗄️ Mô-đun 01: Bộ khung điều khiển & Bộ nhớ nhận thức (5 bài)
    │   ├── README.md
    │   ├── 01_ai_chat_systems_and_prompt_engineering.md
    │   ├── 02_harness_architecture.md
    │   ├── 03_context_management.md
    │   ├── 04_memory_systems.md
    │   └── 05_agent_runtime_parameters_and_prompt_caching.md
    ├── 02-tools-and-mcp/                              # 🔌 Mô-đun 02: Giao thức kết nối công cụ & Structured Outputs (4 bài)
    │   ├── README.md
    │   ├── 01_mcp_architecture.md
    │   ├── 02_constrained_decoding_and_structured_outputs.md
    │   ├── 03_dynamic_tool_retrieval_and_tool_rag.md
    │   └── 04_sandboxed_tool_execution_wasm_and_microvm.md
    ├── 03-loop-and-multi-agent-engineering/           # 🔄 Mô-đun 03: Vòng lặp nhận thức, Bầy đàn & Thực thi bền vững (9 bài)
    │   ├── README.md
    │   ├── 01_loop_fundamentals.md
    │   ├── 02_react_and_planning.md
    │   ├── 03_multi_agent_teams.md
    │   ├── 04_multi_agent_debate_and_consensus.md
    │   ├── 05_ast_self_healing_code_agents.md
    │   ├── 06_durable_execution_and_stateful_workflows.md
    │   ├── 07_state_merkle_trees_and_time_travel_debugging.md
    │   ├── 08_mixture_of_agents_and_layered_routing.md
    │   └── 09_mcts_and_tree_search_reasoning_loops.md
    ├── 04-observability-evals-and-cost/               # 📊 Mô-đun 04: Quan sát, Đánh giá & Tối ưu chi phí (6 bài)
    │   ├── README.md
    │   ├── 01_agent_evals_and_tracing.md
    │   ├── 02_synthetic_benchmarks_and_llm_as_judge.md
    │   ├── 03_token_economics_and_cost_optimization.md
    │   ├── 04_prompt_compression_and_cache_engineering.md
    │   ├── 05_speculative_decoding_and_inference_acceleration.md
    │   └── 06_semantic_caching_and_vector_cache.md
    ├── 05-specialized-agent-domains/                  # 🎯 Mô-đun 05: Các miền tác tử kỹ thuật cao chuyên biệt (6 bài)
    │   ├── README.md
    │   ├── 01_code_graphs_and_repository_intelligence.md
    │   ├── 02_cross_session_memory_and_delta_caching.md
    │   ├── 03_multimodal_gui_and_computer_use.md
    │   ├── 04_browser_automation_and_web_agents.md
    │   ├── 05_symbolic_ai_and_formal_verification.md
    │   └── 06_on_device_and_edge_agents.md
    └── 06-governance-and-enterprise-delivery/         # 🛡️ Mô-đun 06: Quản trị, An ninh bảo mật & Triển khai doanh nghiệp (6 bài)
        ├── README.md
        ├── 01_hitl_and_hotl_human_agent_interaction.md
        ├── 02_agent_security_red_teaming_and_guardrails.md
        ├── 03_how_to_build_enterprise_ai_agents.md
        ├── 04_fullstack_agent_mern_architecture.md
        ├── 05_adversarial_fuzzing_and_automated_agent_red_teaming.md
        └── 06_cryptographic_audit_trails_and_compliance.md
```

---

## 📖 Danh Mục Tài Liệu Cốt Lõi (Wikilinks)

### 🔬 [Trụ cột 1: Research & Foundations](./01-research-and-foundations/README.md)
* [Neural Networks & Their Classifications](./01-research-and-foundations/01-neural-networks/01_neural_networks_and_classifications.md): Giải phẫu nơ-ron nhân tạo, Forward Pass, Backpropagation & Chain Rule, các hàm kích hoạt (ReLU, GELU, SwiGLU), hàm mất mát, giải thuật tối ưu (SGD, AdamW), và bản đồ 8 họ kiến trúc từ MLP, CNN, RNN đến Transformer, GNN, Autoencoders, GAN, Diffusion và MoE.
* [What Are Large Language Models?](./01-research-and-foundations/02-llm-internals/01_what_are_large_language_models.md): Bản chất Language Modeling (Fill-in-the-blank), Subword Tokenization toàn diện (BPE/BBPE, WordPiece, SentencePiece/Unigram LM), các lỗi hệ thống kinh điển (nghịch lý đếm chữ "Strawberry", tính toán số học đa chữ số, thuế token đa ngôn ngữ), 4 bước nhảy vọt lịch sử (2001–2017), so sánh chuyên sâu Autoregressive (GPT) vs. Autoencoding (BERT) vs. Seq2Seq (T5), quy mô tham số, siêu tham số suy luận (`temperature`, `top_p`), và bản chất "Reasoning Machine".
* [Giải Phẫu Toán Học Của Transformer](./01-research-and-foundations/02-llm-internals/02_transformer_math_deep_dive.md): Vi tích phân Scaled Dot-Product, chứng minh chia cho $\sqrt{d_k}$, phân tích Jacobian của Softmax, MHA/MQA/GQA, cơ chế quay tọa độ RoPE, **thuật toán Online Softmax & Tiling của FlashAttention (1-3)** và **toán học định lượng kích thước KV-Cache kết hợp giải thuật PagedAttention (vLLM)**.
* [Định Luật Tỷ Lệ & Kỹ Thuật Lượng Tử Hóa](./01-research-and-foundations/02-llm-internals/03_scaling_laws_and_quantization.md): Định luật Chinchilla ($D \approx 20N$), xu hướng Over-training của LLaMA-3, toán học Quantization Affine, giải thuật GPTQ, AWQ, và chuẩn GGUF/llama.cpp.
* [Dữ Liệu Tổng Hợp & Căn Chỉnh Tác Tử](./01-research-and-foundations/02-llm-internals/04_synthetic_data_and_agent_alignment.md): Khủng hoảng The Data Wall 2026-2028, giải thuật tiến hóa Evol-Instruct (WizardLM), Multi-Agent Self-Play tạo quỹ đạo công cụ, UltraFeedback, chứng minh toán học giải tích DPO, thuật toán ORPO và chắt lọc năng lực Tool Distillation cho mô hình 8B.
* [05_test_time_compute_and_process_reward_models - Test-Time Compute & Process Reward Models](./01-research-and-foundations/02-llm-internals/05_test_time_compute_and_process_reward_models.md): Định luật mở rộng thời gian suy luận (Inference Scaling Laws), so sánh ORM vs PRM, thuật toán Monte Carlo Rollouts của Math-Shepherd, Step-level Beam Search & Backtracking, và phòng chống Reward Hacking.
* [01_semantic_search_and_reranking - Semantic Search & Advanced RAG Architectures](./01-research-and-foundations/03-semantic-search/01_semantic_search_and_reranking.md): Nghịch lý khớp từ khóa ("Vintage Magic Card"), Vector Embeddings & Lời nguyền số chiều, hiện tượng Dị hướng không gian (Anisotropy "hình nón hẹp") & giải pháp làm trắng BERT-Whitening, Asymmetric vs Symmetric Search, so sánh Bi-Encoder vs Cross-Encoder, Two-Stage Pipeline, chiến lược Chunking, thực nghiệm định lượng Recall@K, và **Cẩm nang toàn tập Kiến trúc RAG Tiên tiến** (HyDE, Parent Document Retrieval, Anthropic Contextual Retrieval, Microsoft GraphRAG, Reciprocal Rank Fusion, Self-RAG, Corrective RAG / CRAG, Adaptive RAG, Ma trận so sánh định lượng và Cây quyết định kiến trúc thực chiến).
* [02_rag_architecture_and_components - Inside RAG: Kiến Trúc 4 Cấu Phần & Vòng Lặp Điều Phối](./01-research-and-foundations/03-semantic-search/02_rag_architecture_and_components.md): Giải phẫu 4 cấu phần cốt lõi của RAG (Embeddings/FAISS Retriever, Cohere Reranker, ChatOpenAI Generator, RetrievalQA Orchestrator), mô hình tư duy "Kỳ thi mở sách" (Open-Book Exam), vũ điệu 4 nhịp `Retrieve` $\to$ `Rank` $\to$ `Generate` $\to$ `Orchestrate`, pipeline LangChain mẫu mực, và ca nghiên cứu nông nghiệp thẳng đứng (Vertical Farming & IPM).
* [03_embeddings_and_vector_databases - Vai Trò Cốt Lõi Của Embeddings & Cơ Sở Dữ Liệu Vector](./01-research-and-foundations/03-semantic-search/03_embeddings_and_vector_databases.md): Dấu vân tay số học, cân bằng ngữ cảnh Chunking, 4 cấu trúc chỉ mục (Flat, IVF, HNSW, PQ), khung tiêu chuẩn FICE đánh giá Vector DB và quản trị vòng đời vector (CDC, garbage collection, shadow migration).
* [04_how_database_and_embedding_choices_affect_rag - Đánh Giá Mô Hình Embedding & Vector DB](./01-research-and-foundations/03-semantic-search/04_how_database_and_embedding_choices_affect_rag.md): Khảo nghiệm đối đầu BGE-base vs MiniLM-L6, Chunking văn bản pháp quy y tế (600-800 tokens), tối ưu nprobe Voronoi và bảo trì chỉ mục Ngày-2 (Delta Upsert, 20% Growth Rule).
* [05_theory_to_practice_making_rag_work - Cẩm Nang Kỹ Nghệ Vận Hành RAG Production](./01-research-and-foundations/03-semantic-search/05_theory_to_practice_making_rag_work.md): Khoảng cách thực tế từ Demo đến Production, tam giác đánh đổi bất khả thi (Retrieval Trilemma), Structure-Aware Chunking (AST tree-sitter) và Golden Test Set.
* [06_maintaining_vector_indices_in_rag - Duy Trì & Vận Hành Chỉ Mục Vector](./01-research-and-foundations/03-semantic-search/06_maintaining_vector_indices_in_rag.md): Xử lý 3 dạng trôi dạt (Content Drift, Model Drift, Performance Drift), quy tắc 15-20% kích hoạt Full Rebuild, di cư chỉ mục và quy trình Shadow Hot-swap không gián đoạn (Zero Downtime).
* [07_optimizing_and_modularizing_rag_with_langchain - Tối Ưu Hóa & Mô Đun Hóa RAG Với LangChain](./01-research-and-foundations/03-semantic-search/07_optimizing_and_modularizing_rag_with_langchain.md): Triết lý kiến trúc cắm ghép LCEL, mô hình nhúng cục bộ HuggingFace, lưu trữ đĩa ChromaDB bền vững và nén ngữ cảnh ContextualCompressionRetriever loại bỏ 80% token thừa.
* [08_advanced_retrieval_tactics_for_rag - Chiến Thuật Truy Xuất Nâng Cao](./01-research-and-foundations/03-semantic-search/08_advanced_retrieval_tactics_for_rag.md): Truy xuất lai ghép Hybrid Search (BM25 + Dense qua Reciprocal Rank Fusion), truy xuất có giải thích (Search-Explained), tái xếp hạng Cross-Encoder và mở rộng truy vấn (Query Expansion).
* [09_evaluating_and_optimizing_rag_systems - Đánh Giá & Tối Ưu Hóa Hệ Thống RAG](./01-research-and-foundations/03-semantic-search/09_evaluating_and_optimizing_rag_systems.md): Kiểm thử RAG liên tục, khung đo lường 3 tầng độc lập, chẩn đoán đa biến trực quan hóa qua biểu đồ phân tán và triệt tiêu ảo giác bằng Citation Tracking.
* [10_late_interaction_and_colbert_retrieval - Truy Xuất Tương Tác Muộn & ColBERTv2](./01-research-and-foundations/03-semantic-search/10_late_interaction_and_colbert_retrieval.md): Phá vỡ nút thắt Single Dense Vector, toán tử MaxSim (Maximum Similarity) so khớp đa vector query-document, nén vector phần dư Residual Compression và bộ máy truy vấn PLAID dưới 15ms.

### ✍️ [Trụ cột 2: Prompt & Context Engineering](./02-prompt-and-context/README.md)
* [Các Kỹ Thuật Prompt & Context Engineering Nâng Cao (Toàn Tập)](./02-prompt-and-context/01-prompt-engineering/01_advanced_prompt_engineering_techniques.md): Cẩm nang toàn diện 10 kỹ thuật: Zero/Few-shot (In-Context Learning), CoT Family (Zero-shot, Few-shot, Hybrid), OPRO, Generated Knowledge, Tree of Thoughts (ToT), Directional Stimulus (DSP), Chain of Density (CoD), Quản trị Cửa sổ Ngữ cảnh & khắc phục **Lost in the Middle** (Token Budgeting), và thiết kế **System Instructions chuẩn thẻ XML kết hợp Meta-Prompting**.
* [Lập Trình Hóa Prompt Với DSPy (Stanford NLP) & Tối Ưu Hóa Tự Động](./02-prompt-and-context/01-prompt-engineering/02_dspy_and_programmatic_prompting.md): Chấm dứt kỷ nguyên Prompt Crafting thủ công; triết lý Compiler cho LLM phân ly Logic và Trọng số; 3 cấu phần Signatures, Modules (`Predict`, `ChainOfThought`, `ReAct`, `ProgramOfThought`) & Optimizers (`BootstrapFewShot`, `MIPROv2` Bayesian Instruction Optimization, `COPRO`/APE); bài tập thực chiến RAG Agent & chưng cất tri thức sang LLaMA-3 cục bộ.

### 🛠️ [Trụ cột 3: Building Agents](./03-building-agents/README.md)
* **[01-harness-and-memory - AI Harness & Memory Architecture](./03-building-agents/01-harness-and-memory/README.md)**:
  * [01_ai_chat_systems_and_prompt_engineering.md](./03-building-agents/01-harness-and-memory/01_ai_chat_systems_and_prompt_engineering.md): Dẫn nhập kiến trúc Harness, Memory và 4 tầng tiến hóa nhận thức từ Prompting đến Autonomous Loops.
  * [02_harness_architecture.md](./03-building-agents/01-harness-and-memory/02_harness_architecture.md): Phân tách Lõi tĩnh vs Khung có trạng thái, 5 phân hệ phần mềm và Session Lifecycle.
  * [03_context_management.md](./03-building-agents/01-harness-and-memory/03_context_management.md): Chẩn đoán 3 bệnh lý (Context Poisoning, Context Decay, Context Starvation), giải pháp RAG, Context Pruning, Summarization và kiến trúc Context Quarantine.
  * [04_memory_systems.md](./03-building-agents/01-harness-and-memory/04_memory_systems.md): Mô hình 4 phân tầng nhận thức, quản trị bộ nhớ ảo MemGPT (Context Paging & Core Memory Tools), công thức chấm điểm Generative Agents $\alpha_{\text{rec}} R + \alpha_{\text{imp}} I + \alpha_{\text{rel}} S$, Đồ thị tri thức có nhận thức thời gian (Bi-temporal Knowledge Graph: Zep/Mem0).
  * [05_agent_runtime_parameters_and_prompt_caching.md](./03-building-agents/01-harness-and-memory/05_agent_runtime_parameters_and_prompt_caching.md): Khủng hoảng Prefill $O(N^2)$, cơ chế Prefix Caching (RadixTree) giảm 90% chi phí và TTFT từ 3.5s xuống 0.25s, quy tắc bất biến tiền tố (Static Prefix Invariance), giải phẫu siêu tham số (`temperature`, `top_p`, `max_tokens`, `stop`).
* **[02-tools-and-mcp - Model Context Protocol (MCP) & Tools](./03-building-agents/02-tools-and-mcp/README.md)**:
  * [01_mcp_architecture.md](./03-building-agents/02-tools-and-mcp/01_mcp_architecture.md): Giao thức Model Context Protocol của Anthropic, tam giác Host-Client-Server, primitives (Tools, Resources, Prompts), cơ chế stdio/SSE và code mẫu FastMCP Python.
  * [02_constrained_decoding_and_structured_outputs.md](./03-building-agents/02-tools-and-mcp/02_constrained_decoding_and_structured_outputs.md): Ma trận Unembedding $\mathbf{W}_U$, mặt nạ Logit Masking triệt tiêu $100\%$ lỗi cú pháp JSON/Tool Calling, FSM (Outlines), Pushdown Automata (llama.cpp GBNF) và tăng tốc Jump-Forward Decoding (SGLang).
  * [03_dynamic_tool_retrieval_and_tool_rag.md](./03-building-agents/02-tools-and-mcp/03_dynamic_tool_retrieval_and_tool_rag.md): Khắc phục hội chứng bão công cụ (Tool Storm) và bão hòa context, mô hình Two-stage Tool-RAG (BM25 + Dense RRF), phân cấp Hierarchical Tool Namespaces và chèn động JSON Schema.
  * [04_sandboxed_tool_execution_wasm_and_microvm.md](./03-building-agents/02-tools-and-mcp/04_sandboxed_tool_execution_wasm_and_microvm.md): Môi trường hộp cát cô lập thực thi công cụ nguy hiểm, so sánh 4 cấp độ (Process, Docker, Firecracker MicroVM, WebAssembly WASI), quản trị hạn ngạch CPU/RAM và kiến trúc Watchdog ngắt mạch tự động.
* **[03-loop-and-multi-agent-engineering - Vòng Lặp Nhận Thức, Bầy Đàn & Thực Thi Bền Vững](./03-building-agents/03-loop-and-multi-agent-engineering/README.md)**:
  * [01_loop_fundamentals.md](./03-building-agents/03-loop-and-multi-agent-engineering/01_loop_fundamentals.md): Từ One-shot sang Recursive Execution, chu trình OODA 5 bước, 4 tầng Stopping Criteria và bộ ngắt mạch chống lặp vô tận.
  * [02_react_and_planning.md](./03-building-agents/03-loop-and-multi-agent-engineering/02_react_and_planning.md): So sánh ReAct vs Plan-and-Execute vs Evaluator-Optimizer (Self-Refine).
  * [03_multi_agent_teams.md](./03-building-agents/03-loop-and-multi-agent-engineering/03_multi_agent_teams.md): Phân công lao động nhận thức qua Orchestrator-Worker, Supervisor Hierarchy, Swarm Handoffs và Context Quarantine.
  * [04_multi_agent_debate_and_consensus.md](./03-building-agents/03-loop-and-multi-agent-engineering/04_multi_agent_debate_and_consensus.md): Tranh biện đa tác tử, phá vỡ thiên kiến xác nhận đơn lẻ, Majority Voting, Borda Count & Elo Consensus.
  * [05_ast_self_healing_code_agents.md](./03-building-agents/03-loop-and-multi-agent-engineering/05_ast_self_healing_code_agents.md): Tác tử lập trình tự sửa lỗi qua Cây cú pháp AST (Tree-sitter), SWE-agent ACI và Repo Map PageRank (Aider).
  * [06_durable_execution_and_stateful_workflows.md](./03-building-agents/03-loop-and-multi-agent-engineering/06_durable_execution_and_stateful_workflows.md): Triết lý Durable Execution ("chạy như thể không bao giờ sập"), máy trạng thái State Graphs $\mathcal{S}_t$, Event-sourcing Checkpointers, Replay Determinism, Time-Travel Debugging và Human-in-the-Loop Interrupts.
  * [07_state_merkle_trees_and_time_travel_debugging.md](./03-building-agents/03-loop-and-multi-agent-engineering/07_state_merkle_trees_and_time_travel_debugging.md): Mô hình trạng thái mật mã Merkle DAG $\mathcal{H}_t = \text{SHA256}(\mathcal{H}_{t-1} \parallel \Delta \mathcal{S}_t \parallel a_t \parallel o_t \parallel T_t)$, chia sẻ cấu trúc và nén delta (structural sharing), Time-Travel Debugging, tái hiện lỗi tiền định và rẽ nhánh không sao chép (zero-copy forking).
  * [08_mixture_of_agents_and_layered_routing.md](./03-building-agents/03-loop-and-multi-agent-engineering/08_mixture_of_agents_and_layered_routing.md): Kiến trúc đa tác tử tầng Mixture-of-Agents (MoA), hiện tượng cộng hưởng hợp tác (Collaborativeness Phenomenon), đồ thị phân tầng DAG có trọng số và phễu định tuyến bất đối xứng tối ưu chi phí.
  * [09_mcts_and_tree_search_reasoning_loops.md](./03-building-agents/03-loop-and-multi-agent-engineering/09_mcts_and_tree_search_reasoning_loops.md): Vòng lặp nhận thức Monte Carlo Tree Search (MCTS), 4 pha (Selection via PUCT, Expansion, Simulation với PRM, Backpropagation), giải bài toán quy hoạch dài hạn và cắt tỉa không gian hành động.
* **[04-observability-evals-and-cost - Quan Sát, Đánh Giá & Tối Ưu Chi Phí](./03-building-agents/04-observability-evals-and-cost/README.md)**:
  * [01_agent_evals_and_tracing.md](./03-building-agents/04-observability-evals-and-cost/01_agent_evals_and_tracing.md): OpenTelemetry GenAI Semantic Conventions, Trace Tree, Langfuse Tracing, bộ chỉ số Ragas Triad và benchmark SWE-bench/GAIA.
  * [02_synthetic_benchmarks_and_llm_as_judge.md](./03-building-agents/04-observability-evals-and-cost/02_synthetic_benchmarks_and_llm_as_judge.md): Sinh benchmark Evol-Instruct, 4 thiên kiến của LLM Judge (Position, Verbosity, Self-enhancement, Egocentric), Swap Testing, G-Eval Softmax Logits và CI/CD regression testing.
  * [03_token_economics_and_cost_optimization.md](./03-building-agents/04-observability-evals-and-cost/03_token_economics_and_cost_optimization.md): Mô hình chi phí vòng lặp $O(N^2)$, kiến trúc định tuyến FrugalGPT (Tier 1 SLMs $\to$ Tier 2 Frontier $\to$ Tier 3 Reasoning), nén quan sát tại biên và Budget Circuit Breakers.
  * [04_prompt_compression_and_cache_engineering.md](./03-building-agents/04-observability-evals-and-cost/04_prompt_compression_and_cache_engineering.md): Cơ sở toán học Shannon Entropy, nén ngữ cảnh LLMLingua cắt giảm 80% tokens, GPU KV-cache PagedAttention (vLLM) và cấu trúc dữ liệu RadixTree.
  * [05_speculative_decoding_and_inference_acceleration.md](./03-building-agents/04-observability-evals-and-cost/05_speculative_decoding_and_inference_acceleration.md): Nút thắt Memory-Bound của Autoregressive Decoding, Speculative Sampling với Modified Rejection Sampling, chứng minh bất biến phân phối đầu ra $P_{\text{target}}$, tăng tốc Tree-based Attention (SpecExec), Medusa/Eagle Multi-Heads và tích hợp vLLM.
  * [06_semantic_caching_and_vector_cache.md](./03-building-agents/04-observability-evals-and-cost/06_semantic_caching_and_vector_cache.md): Bộ nhớ đệm ngữ nghĩa Semantic Cache, hiệu chỉnh ngưỡng Cosine $\tau$, khóa phức hợp nhạy ngữ cảnh (Contextual Composite Keys), băm cục bộ LSH và cắt giảm 85% chi phí vận hành tác tử.
* **[05-specialized-agent-domains - Các Miền Tác Tử Chuyên Biệt](./03-building-agents/05-specialized-agent-domains/README.md)**:
  * [01_code_graphs_and_repository_intelligence.md](./03-building-agents/05-specialized-agent-domains/01_code_graphs_and_repository_intelligence.md): Code Property Graph, giao thức SCIP/LSIF, Graph-RAG cho Codebase, thuật toán lan truyền $k$-bước (Blast Radius) và Repo Map PageRank.
  * [02_cross_session_memory_and_delta_caching.md](./03-building-agents/05-specialized-agent-domains/02_cross_session_memory_and_delta_caching.md): Giải quyết bài toán Session Boundary, hệ thống Memory Bank Markdown, Git Merkle DAG Delta Caching (tiết kiệm 97% chi phí parse) và lưu trữ `failed_hypotheses`.
  * [03_multimodal_gui_and_computer_use.md](./03-building-agents/05-specialized-agent-domains/03_multimodal_gui_and_computer_use.md): Tác tử thị giác Computer-Use, Set-of-Mark (SoM) Prompting, OmniParser, Tọa độ chuẩn hóa $[0, 1000]$, và xử lý độ trễ render trên desktop OS.
  * [04_browser_automation_and_web_agents.md](./03-building-agents/05-specialized-agent-domains/04_browser_automation_and_web_agents.md): Tự động hóa trình duyệt web qua Playwright/CDP, nén DOM bằng Accessibility Tree (AXTree) giảm 90% token, Set-of-Mark web grounding và cơ chế stealth chống bot fingerprinting.
  * [05_symbolic_ai_and_formal_verification.md](./03-building-agents/05-specialized-agent-domains/05_symbolic_ai_and_formal_verification.md): Xung đột bản chất giữa suy luận xác suất thống kê (LLMs) và kiểm định hình thức diễn dịch (Deductive Verification), kiến trúc Neuro-Symbolic, vòng lặp CEGIS, Z3 SMT Solver và Lean 4 Theorem Prover ("Proofs as Programs").
  * [06_on_device_and_edge_agents.md](./03-building-agents/05-specialized-agent-domains/06_on_device_and_edge_agents.md): Kiến trúc tác tử biên & cục bộ không phụ thuộc đám mây (Zero Cloud Egress), tối ưu hóa SLMs (SmolLM2, Qwen-2.5-Coder, Phi-3.5-mini), thực thi WebGPU trong trình duyệt, llama.cpp & NPU, và mô hình Hybrid Local-First Escalation.
* **[06-governance-and-enterprise-delivery - Quản Trị, An Ninh & Bàn Giao Doanh Nghiệp](./03-building-agents/06-governance-and-enterprise-delivery/README.md)**:
  * [01_hitl_and_hotl_human_agent_interaction.md](./03-building-agents/06-governance-and-enterprise-delivery/01_hitl_and_hotl_human_agent_interaction.md): Phổ tự trị HITL/HOTL/HOOTL, Ma trận Task-Risk Index, cơ chế leo thang động (Dynamic Escalation), chống Approval Fatigue và Emergency Kill Switch.
  * [02_agent_security_red_teaming_and_guardrails.md](./03-building-agents/06-governance-and-enterprise-delivery/02_agent_security_red_teaming_and_guardrails.md): Bảo mật tác tử, phòng chống Indirect Prompt Injection (IPI), kiến trúc Dual-LLM (Privileged vs Quarantined), rò rỉ ảnh Markdown, Canary Tokens và MicroVM/gVisor Sandboxing.
  * [03_how_to_build_enterprise_ai_agents.md](./03-building-agents/06-governance-and-enterprise-delivery/03_how_to_build_enterprise_ai_agents.md): Cẩm nang kiến trúc 6 phòng ban doanh nghiệp, Microservices phân tán, quản trị SLA/ngân sách và tuân thủ ISO 42001 / SOC 2 Type II.
  * [04_fullstack_agent_mern_architecture.md](./03-building-agents/06-governance-and-enterprise-delivery/04_fullstack_agent_mern_architecture.md): Ứng dụng Full-stack MERN: MongoDB Atlas Vector Search & Checkpointer, Express SSE Streaming, Node.js MCP Client (`@modelcontextprotocol/sdk`) và React Generative UI với HITL Modal.
  * [05_adversarial_fuzzing_and_automated_agent_red_teaming.md](./03-building-agents/06-governance-and-enterprise-delivery/05_adversarial_fuzzing_and_automated_agent_red_teaming.md): Kiểm thử xâm nhập đối kháng tự động đa lượt (Multi-turn Automated Red-Teaming), các thuật toán đột biến jailbreak (PAIR, TAP, GCG), kỹ thuật Typoglycemia, fuzzing tham số công cụ MCP (SQLi, SSRF, Path Traversal) và đo lường Attack Defense Rate (ADR) trong CI/CD.
  * [06_cryptographic_audit_trails_and_compliance.md](./03-building-agents/06-governance-and-enterprise-delivery/06_cryptographic_audit_trails_and_compliance.md): Nhật ký kiểm toán mật mã không thể làm giả (Cryptographic Audit Trails), tuân thủ EU AI Act Điều 12 & SOC 2, che giấu dữ liệu PII/HIPAA và chuỗi băm Merkle/SHA-256 xác thực toàn vẹn bằng chứng.

