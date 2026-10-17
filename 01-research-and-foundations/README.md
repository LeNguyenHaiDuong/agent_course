---
title: "Trụ Cột 1: Research & Foundations"
aliases:
  - Research and Foundations MOC
tags:
  - agent-course
  - research
  - moc
type: moc
created: 2026-09-21
updated: 2026-09-21
---

# 🔬 TRỤ CỘT 1: RESEARCH & FOUNDATIONS (NGHIÊN CỨU & NỀN TẢNG)

Trụ cột này tập trung vào việc nghiên cứu bản chất toán học, lý thuyết học sâu, giải phẫu cấu trúc mạng nơ-ron và cơ chế hoạt động nội tại của các Mô hình Ngôn ngữ Lớn (LLMs).

---

## 🗺️ Bản Đồ Cấu Trúc Trụ Cột 1

```text
01-research-and-foundations/
├── README.md                                    # (Tài liệu này) Giới thiệu tổng quan Trụ cột 1
├── 01-neural-networks/                          # 🧠 Chuyên đề 1: Nền tảng Mạng Nơ-ron & Học sâu (ANN, CNN, RNN, MoE)
│   ├── README.md
│   └── neural_networks_and_classifications.md   # Giải phẫu nơ-ron, Backpropagation, Hàm kích hoạt, Bản đồ phân loại
├── 02-llm-internals/                            # 📚 Chuyên đề 2: Bản chất Mô hình Ngôn ngữ Lớn (LLM Core & Transformer)
│   ├── README.md
│   ├── what_are_large_language_models.md        # Thí nghiệm điền từ, Transformer, AR vs AE, Scaling, Reasoning
│   ├── 04_transformer_math_deep_dive.md         # Toán học Scaled Dot-Product, FlashAttention & KV-Cache
│   ├── 05_scaling_laws_and_quantization.md      # Định luật Chinchilla, Lượng tử hóa GPTQ/AWQ & GGUF
│   └── 06_synthetic_data_and_agent_alignment.md # Dữ liệu tổng hợp, Multi-Agent Self-Play & DPO/ORPO
└── 03-semantic-search/                          # 🔍 Chuyên đề 3: Tìm kiếm Ngữ nghĩa, Không gian Vector & Tái xếp hạng
    ├── README.md                                # Hướng dẫn chuyên đề & thứ tự đọc
    ├── 01_semantic_search_and_reranking.md      # Bài 1: Bi-Encoder vs Cross-Encoder, Two-Stage Pipeline & Advanced RAG
    └── 02_rag_architecture_and_components.md    # Bài 2: Giải phẫu 4 cấu phần RAG (Inside RAG) & Vòng lặp điều phối
```

---

## 📂 Danh Mục Chuyên Đề

### 1. [01-neural-networks - Neural Networks & Architecture Classifications](./01-neural-networks/README.md)
* **Trọng tâm:** Toán học nơ-ron nhân tạo (Perceptron), Forward/Backpropagation, các hàm kích hoạt (ReLU, GELU, SwiGLU), các giải thuật tối ưu (SGD, AdamW), và bản đồ phân loại kiến trúc: MLP, CNN, RNN/LSTM/GRU, Transformer, GNN, Autoencoders, GAN, Diffusion Models, và Mixture of Experts (MoE).
* **Tài liệu chi tiết:** [neural_networks_and_classifications.md](./01-neural-networks/neural_networks_and_classifications.md)

### 2. [02-llm-internals - LLM Internals & Mechanisms](./02-llm-internals/README.md)
* **Trọng tâm:** Bản chất toán học của Language Modeling (Fill-in-the-blank), Subword Tokenization toàn diện (BPE/BBPE, WordPiece, SentencePiece/Unigram LM), các lỗi hệ thống kinh điển (nghịch lý đếm chữ "Strawberry", số học đa chữ số, thuế token đa ngôn ngữ), 4 bước nhảy vọt lịch sử (2001–2017), so sánh chuyên sâu Autoregressive (GPT) vs. Autoencoding (BERT) vs. Seq2Seq (T5), quy mô tham số & VRAM, siêu tham số suy luận (`temperature`, `top_p`), và bản chất "Reasoning Machine".
* **Tài liệu chi tiết:**
  * [What Are Large Language Models?](./02-llm-internals/what_are_large_language_models.md): Tổng quan bản chất mô hình ngôn ngữ lớn, giải phẫu Tokenization, căn chỉnh Alignment và đạo đức dữ liệu.
  * [Giải Phẫu Toán Học Của Transformer](./02-llm-internals/04_transformer_math_deep_dive.md): Vi tích phân Scaled Dot-Product, chứng minh chia cho $\sqrt{d_k}$, phân tích Jacobian của Softmax, MHA/MQA/GQA, và cơ chế quay tọa độ Rotary Position Embedding (RoPE).
  * [Định Luật Tỷ Lệ & Kỹ Thuật Lượng Tử Hóa](./02-llm-internals/05_scaling_laws_and_quantization.md): Định luật Chinchilla ($D \approx 20N$), xu hướng Over-training của LLaMA-3, toán học Quantization Affine, giải thuật GPTQ, AWQ, và chuẩn GGUF/llama.cpp.
  * [Dữ Liệu Tổng Hợp & Căn Chỉnh Tác Tử](./02-llm-internals/06_synthetic_data_and_agent_alignment.md): Khủng hoảng The Data Wall 2026-2028, giải thuật tiến hóa Evol-Instruct (WizardLM), Multi-Agent Self-Play tạo quỹ đạo công cụ, UltraFeedback, chứng minh toán học giải tích DPO, thuật toán ORPO và chắt lọc năng lực Tool Distillation cho mô hình 8B.

### 3. [03-semantic-search - Semantic Search & Advanced RAG Architectures](./03-semantic-search/README.md)
* **Trọng tâm:** Khắc phục ảo giác tự tin với mô hình "Kỳ thi mở sách" (Open-Book Exam), 4 cấu phần RAG (Retriever, Ranker, Generator, Orchestrator), vũ điệu $\textbf{Retrieve} \to \textbf{Rank} \to \textbf{Generate} \to \textbf{Orchestrate}$, Nghịch lý khớp từ khóa (Vintage Magic Card vs Kit), Vector Embeddings & Lời nguyền số chiều, hiện tượng Dị hướng không gian (Anisotropy "hình nón hẹp") & giải pháp làm trắng BERT-Whitening, Asymmetric vs Symmetric Search, so sánh chuyên sâu Bi-Encoder vs Cross-Encoder, quy trình phễu 2 giai đoạn (Two-Stage Pipeline), chiến lược Chunking, thực nghiệm định lượng Recall@K (OpenAI vs Open-source), và **Cẩm nang toàn tập Kiến trúc RAG Tiên tiến** (HyDE, Parent Document Retrieval, Anthropic Contextual Retrieval, Microsoft GraphRAG, Reciprocal Rank Fusion, Self-RAG, Corrective RAG / CRAG, Adaptive RAG, Ma trận so sánh định lượng và Cây quyết định kiến trúc thực chiến).
* **Tài liệu chi tiết (Theo thứ tự đọc):**
  * 📖 **Bài 1:** [01_semantic_search_and_reranking.md](./03-semantic-search/01_semantic_search_and_reranking.md): Chuyên khảo toàn diện về không gian vector, Bi-Encoder vs Cross-Encoder, Two-Stage Pipeline và 9 kiến trúc RAG hiện đại.
  * 📖 **Bài 2:** [02_rag_architecture_and_components.md](./03-semantic-search/02_rag_architecture_and_components.md): Phân tích chuyên sâu 4 cấu phần cốt lõi (Inside RAG), pipeline LangChain/FAISS/Cohere/ChatOpenAI, case study Nông nghiệp thẳng đứng và các thách thức vận hành.

---

## 🔗 Điều Hướng Nhanh
* Trở về trang chủ: [🏠 Vault Home MOC](../README.md)
* Chuyển sang Trụ cột 2: [✍️ Trụ cột 2: Prompt & Context Engineering](../02-prompt-and-context/README.md)
