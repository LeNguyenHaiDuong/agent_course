# 🔍 TÌM KIẾM NGỮ NGHĨA & HỆ THỐNG TRUY XUẤT (SEMANTIC SEARCH & RETRIEVAL)

Thư mục này nghiên cứu các cơ chế biểu diễn không gian vector, giải pháp truy xuất ngữ nghĩa (Semantic Search), kỹ thuật tái xếp hạng (Re-ranking) và chiến lược tối ưu hóa chất lượng dữ liệu đầu vào cho hệ thống RAG và Tác tử AI (AI Agents).

---

## 📂 Danh Mục Tài Liệu

| Tài liệu | Mô tả chi tiết & Nội dung chuyên sâu |
| :--- | :--- |
| 📖 [**Semantic Search & Re-ranking**](semantic_search_and_reranking.md) | **Chuyên khảo toàn diện về Tìm kiếm Ngữ nghĩa & Tái xếp hạng:**<br>• **Nghịch lý từ khóa (Lexical Matching):** Thí nghiệm tư duy *"Vintage Magic Card"* vs. *"Vintage Magic Kit"*, giới hạn của BM25 và N-gram.<br>• **Toán học không gian Vector:** Dense Embeddings (DPR, OpenAI Contrastive Learning), Lời nguyền số chiều (Curse of Dimensionality), Cosine Similarity vs. Euclidean Distance vs. Dot Product.<br>• **Phân loại tác vụ:** Asymmetric Search (RAG, Query ngắn vs Văn bản dài) vs. Symmetric Search (Title-to-Title, FAQ).<br>• **Giải phẫu 3 trường phái kiến trúc:** **Bi-Encoder / SBERT** (Mô hình 2 tháp, giảm từ 65h xuống 5s, Vector DB) vs. **Cross-Encoder** (Full Cross-Attention, Nogueira & Cho) vs. **ColBERT** (Late Interaction & toán tử MaxSim).<br>• **Pipeline Phễu hai giai đoạn (Two-Stage):** Bi-Encoder thu hồi Top-50 ứng viên $\to$ Cross-Encoder tái định vị Top-3.<br>• **Chiến lược Chunking:** Sliding Window có gối đầu (Overlap), Natural Whitespace, Semantic Clustering.<br>• **Thực nghiệm Benchmarking:** So sánh OpenAI Ada-002 vs. Open-source MPNet Base, tác động tăng trưởng Recall@1 (+24.3%), độ trễ thực thi (40 giây vs 24 phút).<br>• **Fine-tuning:** Tinh chỉnh Cross-encoder và Bi-encoder trên dữ liệu domain chuyên biệt.<br>• **Tác động đến AI Agents:** Hiện tượng *"Lost in the Middle"* (Liu et al., 2023), nền tảng Semantic Memory và trần hiệu năng của RAG Chatbots.<br>• **Tài liệu tham khảo học thuật:** 6 bài báo khoa học cốt lõi (SBERT, DPR, BERT Re-ranking, ColBERT, OpenAI Embeddings, Lost in the Middle). |

---

## 🔗 Liên Kết Đến Các Chuyên Đề Khác

* Chuyên đề nền tảng: [**LLM Internals & Mechanisms**](../llm-internals/README.md)
* Chuyên đề mạng nơ-ron: [**Neural Networks & Classifications**](../neural-networks/README.md)
* Chuyên đề ứng dụng Agent: [**AI Chat Systems & Architecture**](../../03-building-agents/ai_chat_systems_and_prompt_engineering.md)
* Bước chuyển tiếp: [**Trụ cột 2: Prompt & Context Engineering**](../../02-prompt-and-context/README.md)
