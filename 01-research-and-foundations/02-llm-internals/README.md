---
title: "Chuyên Đề: Bản Chất & Cơ Chế Hoạt Động Của LLM (LLM Internals)"
aliases:
  - LLM Internals MOC
  - LLM Architecture Overview
tags:
  - agent-course
  - research
  - foundations
  - llm-internals
  - moc
type: moc
created: 2026-09-20
updated: 2026-09-27
---

# 📚 BẢN CHẤT MÔ HÌNH NGÔN NGỮ LỚN (LLM INTERNALS)

Thư mục này nghiên cứu cơ chế vận hành nội tại và bản chất toán học của **Mô hình Ngôn ngữ Lớn (Large Language Models - LLMs)** — các cỗ máy tính toán nền tảng sinh ra từ kiến trúc Transformer.

---

## 📂 Danh Mục Tài Liệu Chuyên Sâu

| Tài liệu | Trọng tâm nghiên cứu & Nội dung cốt lõi |
| :--- | :--- |
| 📖 **[[what_are_large_language_models|What Are Large Language Models?]]** | **Chuyên khảo toàn diện về LLMs:**<br>• Bản chất dự đoán token kế tiếp (Next-token prediction), xác suất chuỗi.<br>• **Subword Tokenization toàn diện:** Thuật toán Byte-Pair Encoding (BPE/BBPE), WordPiece (PMI Likelihood), SentencePiece/Unigram LM (Lossless pruning); các lỗi hệ thống kinh điển: nghịch lý đếm chữ cái *"Strawberry"*, tính toán số học đa chữ số và bất bình đẳng "thuế token" đa ngôn ngữ.<br>• 4 bước nhảy vọt lịch sử (2001–2017) và giải phẫu 4 gia tộc: BERT, T5, GPT Series, LLaMA.<br>• Cuộc cách mạng Căn chỉnh Alignment (Pre-training $\to$ SFT $\to$ RLHF/DPO).<br>• Nghịch lý quy mô và bản chất "Reasoning Machine" trong hệ thống Agent. |
| 📖 **[[04_transformer_math_deep_dive|04_transformer_math_deep_dive.md - Giải Phẫu Toán Học Của Transformer]]** | **Vi tích phân & Đại số tuyến tính của Transformer:**<br>• Chứng minh toán học: Tại sao chia cho $\sqrt{d_k}$ trong Scaled Dot-Product Attention?<br>• Khảo sát Jacobian của hàm Softmax & hiện tượng bão hòa gradient.<br>• Đại số tuyến tính Multi-Head Attention (MHA), Multi-Query (MQA) và Grouped-Query Attention (GQA).<br>• Cơ chế xoay tọa độ **Rotary Position Embedding (RoPE)** trên mặt phẳng phức và kỹ thuật mở rộng ngữ cảnh triệu tokens (RoPE Scaling).<br>• **FlashAttention & Toán học Online Softmax:** Tiling bộ nhớ on-chip SRAM/HBM, công thức cập nhật lũy kế $m_{\text{new}}, d_{\text{new}}, O_{\text{new}}$ triệt tiêu ma trận $O(N^2)$.<br>• **Toán học định lượng KV-Cache & PagedAttention (vLLM):** Công thức kích thước VRAM theo số tầng, số head và chiều dài token; giải thuật phân trang chống phân mảnh bộ nhớ ảo. |
| 📖 **[[05_scaling_laws_and_quantization|05_scaling_laws_and_quantization.md - Định Luật Tỷ Lệ & Lượng Tử Hóa]]** | **Định luật quy mô & Nén mô hình phục vụ Agent cục bộ:**<br>• Phân tích sai lầm của Định luật Kaplan (OpenAI) và cuộc cách mạng **Định luật Chinchilla** (DeepMind): Tương quan $D \approx 20N$.<br>• Xu hướng "Inference-Optimal" Over-training của LLaMA-3 (15T tokens cho 8B).<br>• Toán học lượng tử hóa Affine (Scale $S$, Zero-point $Z$), Outlier features sụp đổ INT8.<br>• Các giải thuật tiên tiến: LLM.int8(), GPTQ (Inverse Hessian OBS), AWQ (Activation-aware).<br>• Hệ sinh thái Local LLM: GGUF, llama.cpp, bảng đánh đổi k-quants và công thức tính VRAM budget thực tế cho Agent. |
| 📖 **[[06_synthetic_data_and_agent_alignment|06_synthetic_data_and_agent_alignment.md - Dữ Liệu Tổng Hợp & Căn Chỉnh Tác Tử]]** | **Đột phá Bức tường Dữ liệu & Căn chỉnh Agent gọi công cụ:**<br>• Khủng hoảng cạn kiệt dữ liệu con người 2026–2028 (Epoch AI) & sự thiếu chuẩn của human data đối với Agent.<br>• Thuật toán tiến hóa **Evol-Instruct** (WizardLM) qua 5 toán tử đột biến & Magicoder (OSS-Instruct).<br>• **Multi-Agent Self-Play:** Tạo quỹ đạo tương tác công cụ $\tau = (s, a, o)$, Rejection Sampling qua Unit Test Hộp cát (Sandbox).<br>• Đánh giá sở thích tự động UltraFeedback & khử thiên kiến LLM-as-a-Judge.<br>• **Chứng minh toán học giải tích DPO:** Tái tham số hóa phần thưởng ẩn, triệt tiêu $Z(x)$ qua mô hình Bradley-Terry và dẫn xuất Loss DPO.<br>• Căn chỉnh đơn bước **ORPO** bằng Odds Ratio loại bỏ Reference model tiết kiệm 50% VRAM.<br>• Kỹ thuật Tool Distillation từ GPT-4o xuống LLaMA-3 8B và kịch bản huấn luyện QLoRA DPO Trainer bằng PyTorch & TRL. |

---

## 🔗 Liên Kết Điều Hướng
* Chuyên đề nền tảng: [[01-research-and-foundations/01-neural-networks/README|🧠 01-neural-networks - Neural Networks & Architecture Classifications]]
* Chuyên đề truy xuất: [[01-research-and-foundations/03-semantic-search/README|🔍 03-semantic-search - Semantic Search & Re-ranking]]
* Trở về mục lục Trụ cột 1: [[01-research-and-foundations/README|🔬 Trụ Cột 1: Research & Foundations]]
* Trở về trang chủ Vault: [[README|🏠 Vault Home MOC]]
