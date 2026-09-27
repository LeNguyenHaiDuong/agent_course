# 🔍 TÌM KIẾM NGỮ NGHĨA & HỆ THỐNG TRUY XUẤT (SEMANTIC SEARCH & RETRIEVAL)

Thư mục này nghiên cứu các cơ chế biểu diễn không gian vector, giải pháp truy xuất ngữ nghĩa (Semantic Search), kỹ thuật tái xếp hạng (Re-ranking) và chiến lược tối ưu hóa chất lượng dữ liệu đầu vào cho hệ thống RAG và Tác tử AI (AI Agents).

---

## 📂 Danh Mục Tài Liệu

| 📖 [**Semantic Search & Re-ranking**](semantic_search_and_reranking.md) | **Chuyên khảo toàn diện về Tìm kiếm Ngữ nghĩa, Tái xếp hạng & Cẩm nang RAG Tiên Tiến:**<br>• **Nghịch lý từ khóa (Lexical Matching):** Thí nghiệm tư duy *"Vintage Magic Card"* vs. *"Vintage Magic Kit"*, giới hạn của BM25 và N-gram.<br>• **Hình học không gian Vector & Hiện tượng Dị hướng (Anisotropy):** Lời nguyền số chiều, hiện tượng "hình nón hẹp" (Narrow Cone Phenomenon, Ethayarajh 2019), giải pháp làm trắng BERT-Whitening (SVD Zero-Centering) và học tương phản bảo toàn tính đồng đều (Uniformity).<br>• **Phân loại tác vụ:** Asymmetric Search (RAG, Query ngắn vs Văn bản dài) vs. Symmetric Search (Title-to-Title, FAQ).<br>• **Giải phẫu 3 trường phái kiến trúc:** **Bi-Encoder / SBERT** (Mô hình 2 tháp, Vector DB) vs. **Cross-Encoder** (Full Cross-Attention) vs. **ColBERT** (Late Interaction & toán tử MaxSim).<br>• **Pipeline Phễu hai giai đoạn (Two-Stage):** Bi-Encoder thu hồi Top-50 ứng viên $\to$ Cross-Encoder tái định vị Top-3.<br>• **Chiến lược Chunking:** Sliding Window có gối đầu (Overlap), Natural Whitespace, Semantic Clustering.<br>• **Thực nghiệm Benchmarking:** So sánh OpenAI Ada-002 vs. Open-source MPNet Base, tác động tăng trưởng Recall@1 (+24.3%), độ trễ thực thi (40 giây vs 24 phút).<br>• **Fine-tuning:** Tinh chỉnh Cross-encoder và Bi-encoder trên dữ liệu domain chuyên biệt.<br>• **Cẩm nang toàn tập Kiến trúc RAG Tiên tiến (Advanced & Agentic RAG):**<br>  - Tiến hóa 3 thế hệ (Naive $\to$ Advanced $\to$ Modular/Agentic).<br>  - Tiền truy xuất (Pre-retrieval): **HyDE** (Hypothetical Document Embeddings), Multi-Query Expansion, Step-Back Prompting.<br>  - Đột phá Chunking & Indexing: **Parent Document / Hierarchical Retrieval**, **Anthropic Contextual Retrieval** (giảm 49% lỗi trượt), **Microsoft GraphRAG** (phân cụm cộng đồng Leiden giải quyết Global Sensemaking).<br>  - Hậu truy xuất (Post-retrieval): Reciprocal Rank Fusion (RRF), Cross-Encoder Rerank, Contextual Compression chống *"Lost in the Middle"* (Liu et al., 2023).<br>  - RAG Tác tử tự phản tư: **Self-RAG** (4 reflection tokens `[Retrieve]`, `[IsRel]`, `[IsSup]`), **CRAG** (3 vùng tin cậy + Web search fallback), **Adaptive RAG**.<br>  - Bảng so sánh 9 kỹ thuật RAG định lượng và Cây quyết định kiến trúc thực chiến.<br>• **Tài liệu tham khảo học thuật:** 14 bài báo khoa học cốt lõi (SBERT, DPR, ColBERT, Lost in the Middle, HyDE, Contextual Retrieval, GraphRAG, Self-RAG, CRAG, Anisotropy, Whitening). |

---

## 🔗 Liên Kết Đến Các Chuyên Đề Khác

* Chuyên đề nền tảng: [**LLM Internals & Mechanisms**](../llm-internals/README.md)
* Chuyên đề mạng nơ-ron: [**Neural Networks & Classifications**](../neural-networks/README.md)
* Chuyên đề ứng dụng Agent: [**AI Chat Systems & Architecture**](../../03-building-agents/ai_chat_systems_and_prompt_engineering.md)
* Bước chuyển tiếp: [**Trụ cột 2: Prompt & Context Engineering**](../../02-prompt-and-context/README.md)
