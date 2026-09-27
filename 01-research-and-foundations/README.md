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
├── neural-networks/                             # 🧠 Nền tảng Mạng Nơ-ron & Học sâu (ANN, CNN, RNN, Transformers, MoE)
│   ├── README.md
│   └── neural_networks_and_classifications.md   # Giải phẫu nơ-ron, Backpropagation, Hàm kích hoạt, Bản đồ phân loại
├── llm-internals/                               # 📚 Bản chất Mô hình Ngôn ngữ Lớn (LLM Core & Pre-training)
│   ├── README.md
│   └── what_are_large_language_models.md        # Thí nghiệm điền từ, Transformer, AR vs AE, Scaling, Reasoning
└── semantic-search/                             # 🔍 Tìm kiếm Ngữ nghĩa, Không gian Vector & Tái xếp hạng (Re-ranking)
    ├── README.md
    └── semantic_search_and_reranking.md         # Bi-Encoder vs Cross-Encoder, Two-stage Retrieval, Chunking & Benchmarks
```

---

## 📂 Danh Mục Chuyên Đề

### 1. [[01-research-and-foundations/neural-networks/README|Neural Networks & Architecture Classifications]]
* **Trọng tâm:** Toán học nơ-ron nhân tạo (Perceptron), Forward/Backpropagation, các hàm kích hoạt (ReLU, GELU, SwiGLU), các giải thuật tối ưu (SGD, AdamW), và bản đồ phân loại kiến trúc: MLP, CNN, RNN/LSTM/GRU, Transformer, GNN, Autoencoders, GAN, Diffusion Models, và Mixture of Experts (MoE).
* **Tài liệu chi tiết:** [[neural_networks_and_classifications|neural_networks_and_classifications.md]]

### 2. [[01-research-and-foundations/llm-internals/README|LLM Internals & Mechanisms]]
* **Trọng tâm:** Bản chất toán học của Language Modeling (Fill-in-the-blank), Subword Tokenization toàn diện (BPE/BBPE, WordPiece, SentencePiece/Unigram LM), các lỗi hệ thống kinh điển (nghịch lý đếm chữ "Strawberry", số học đa chữ số, thuế token đa ngôn ngữ), 4 bước nhảy vọt lịch sử (2001–2017), so sánh chuyên sâu Autoregressive (GPT) vs. Autoencoding (BERT) vs. Seq2Seq (T5), quy mô tham số & VRAM, siêu tham số suy luận (`temperature`, `top_p`), và bản chất "Reasoning Machine".
* **Tài liệu chi tiết:**
  * [[what_are_large_language_models|What Are Large Language Models?]]: Tổng quan bản chất mô hình ngôn ngữ lớn, giải phẫu Tokenization, căn chỉnh Alignment và đạo đức dữ liệu.
  * [[04_transformer_math_deep_dive|Giải Phẫu Toán Học Của Transformer]]: Vi tích phân Scaled Dot-Product, chứng minh chia cho $\sqrt{d_k}$, phân tích Jacobian của Softmax, MHA/MQA/GQA, và cơ chế quay tọa độ Rotary Position Embedding (RoPE).
  * [[05_scaling_laws_and_quantization|Định Luật Tỷ Lệ & Kỹ Thuật Lượng Tử Hóa]]: Định luật Chinchilla ($D \approx 20N$), xu hướng Over-training của LLaMA-3, toán học Quantization Affine, giải thuật GPTQ, AWQ, và chuẩn GGUF/llama.cpp.
  * [[06_synthetic_data_and_agent_alignment|Dữ Liệu Tổng Hợp & Căn Chỉnh Tác Tử]]: Khủng hoảng The Data Wall 2026-2028, giải thuật tiến hóa Evol-Instruct (WizardLM), Multi-Agent Self-Play tạo quỹ đạo công cụ, UltraFeedback, chứng minh toán học giải tích DPO, thuật toán ORPO và chắt lọc năng lực Tool Distillation cho mô hình 8B.

### 3. [[01-research-and-foundations/semantic-search/README|Semantic Search & Advanced RAG Architectures]]
* **Trọng tâm:** Nghịch lý khớp từ khóa (Vintage Magic Card vs Kit), Vector Embeddings & Lời nguyền số chiều, hiện tượng Dị hướng không gian (Anisotropy "hình nón hẹp") & giải pháp làm trắng BERT-Whitening, Asymmetric vs Symmetric Search, so sánh chuyên sâu Bi-Encoder vs Cross-Encoder, quy trình phễu 2 giai đoạn (Two-Stage Pipeline), chiến lược Chunking, thực nghiệm định lượng Recall@K (OpenAI vs Open-source), và **Cẩm nang toàn tập Kiến trúc RAG Tiên tiến** (HyDE, Parent Document Retrieval, Anthropic Contextual Retrieval, Microsoft GraphRAG, Reciprocal Rank Fusion, Self-RAG, Corrective RAG / CRAG, Adaptive RAG, Ma trận so sánh định lượng và Cây quyết định kiến trúc thực chiến).
* **Tài liệu chi tiết:** [[semantic_search_and_reranking|semantic_search_and_reranking.md]]

---

## 🔗 Điều Hướng Nhanh
* Trở về trang chủ: [[README|🏠 Vault Home MOC]]
* Chuyển sang Trụ cột 2: [[02-prompt-and-context/README|✍️ Trụ cột 2: Prompt & Context Engineering]]
