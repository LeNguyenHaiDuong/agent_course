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
* **Trọng tâm:** Bản chất toán học của Language Modeling (Fill-in-the-blank), Subword Tokenization (BPE), 4 bước nhảy vọt lịch sử (2001–2017), so sánh chuyên sâu Autoregressive (GPT) vs. Autoencoding (BERT) vs. Seq2Seq (T5), quy mô tham số & VRAM, siêu tham số suy luận (`temperature`, `top_p`), và bản chất "Reasoning Machine".
* **Tài liệu chi tiết:** [[what_are_large_language_models|what_are_large_language_models.md]]

### 3. [[01-research-and-foundations/semantic-search/README|Semantic Search & Re-ranking Architecture]]
* **Trọng tâm:** Nghịch lý khớp từ khóa (Vintage Magic Card vs Kit), Vector Embeddings & Lời nguyền số chiều, Asymmetric vs Symmetric Search, so sánh chuyên sâu Bi-Encoder (Siamese) vs Cross-Encoder (Full Attention), quy trình phễu 2 giai đoạn (Two-Stage Pipeline), chiến lược Chunking và thực nghiệm định lượng Recall@K (OpenAI vs Open-source).
* **Tài liệu chi tiết:** [[semantic_search_and_reranking|semantic_search_and_reranking.md]]

---

## 🚀 Lộ Trình Mở Rộng Tiếp Theo

* `03_tokenization_and_embeddings.md`: Phân tích sâu thuật toán Byte-Pair Encoding (BPE), WordPiece và không gian vector hình học.
* `04_transformer_math_deep_dive.md`: Khảo sát vi tích phân của Multi-Head Self-Attention, ma trận $Q, K, V$ và Positional Encodings (RoPE).
* `05_scaling_laws_and_quantization.md`: Định luật tỷ lệ Chinchilla, các kỹ thuật lượng tử hóa trọng số (INT8, INT4, GPTQ, AWQ).

---

## 🔗 Điều Hướng Nhanh
* Trở về trang chủ: [[README|🏠 Vault Home MOC]]
* Chuyển sang Trụ cột 2: [[02-prompt-and-context/README|✍️ Trụ cột 2: Prompt & Context Engineering]]
