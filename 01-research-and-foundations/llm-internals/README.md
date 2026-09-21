# 📚 BẢN CHẤT MÔ HÌNH NGÔN NGỮ LỚN (LLM INTERNALS)

Thư mục này nghiên cứu cơ chế vận hành nội tại của **Mô hình Ngôn ngữ Lớn (Large Language Models - LLMs)** — các cỗ máy tính toán nền tảng sinh ra từ kiến trúc Transformer.

---

## 📂 Danh Mục Tài Liệu

| Tài liệu | Mô tả chi tiết & Nội dung chuyên sâu |
| :--- | :--- |
| 📖 [**What Are Large Language Models?**](what_are_large_language_models.md) | **Chuyên khảo toàn diện về LLMs:**<br>• **Bản chất & Biểu diễn:** Thí nghiệm điền từ (Fill-in-the-blank), Toán học xác suất chuỗi, Tokenization (BPE, Subwords, Tokens vs Words).<br>• **Tiến hóa 4 bước nhảy vọt (2001–2017):** Bengio 2001, Word2Vec 2013, Seq2Seq & Bahdanau Attention, Transformer 2017.<br>• **Giải phẫu 4 gia tộc LLM:** **BERT** (Encoder-only, Wikipedia + BookCorpus, NLU), **T5** (Text-to-Text, Common Crawl C4, Multi-tasking), **GPT Series** (GPT-1 $\to$ GPT-2 trên Reddit $\to$ GPT-3 $\to$ GPT-4 Multimodal), **LLaMA / LLaMA-2** (Meta Open-weights, 7B/13B/70B, Pre-trained vs Chat).<br>• **Cuộc cách mạng Căn chỉnh (Alignment):** Thí nghiệm tư duy kinh điển *"Is the Earth flat?"* (GPT-3 Base vs InstructGPT), quy trình 3 tầng (Pre-training $\to$ SFT $\to$ RLHF / PPO).<br>• **Đạo đức dữ liệu & Thiên vị:** Tranh cãi bản quyền (Fair Use vs Copyright), Hộp đen dữ liệu thương mại, Thiên vị tiếng Anh (English-centric Bias).<br>• **Nghịch lý quy mô:** "How big is too big?" – Vì sao mô hình 110M (BERT) lại đè bẹp mô hình 175B (GPT-3) trong các bài toán thực tế chuyên biệt.<br>• **Cơ chế suy luận & Bản chất:** Inference parameters (`temperature`, `top_p`), và bản chất thực sự của LLM như một **"Reasoning Machine"** trong hệ thống Agent. |

---

## 🔗 Liên Kết Đến Các Chuyên Đề Khác

* Chuyên đề nền tảng: [**Neural Networks & Classifications**](../neural-networks/README.md)
* Bước chuyển tiếp: [**Trụ cột 2: Prompt & Context Engineering**](../../02-prompt-and-context/README.md)
