# 🔍 TÌM KIẾM NGỮ NGHĨA & HỆ THỐNG TRUY XUẤT (SEMANTIC SEARCH & RETRIEVAL)

Thư mục này nghiên cứu các cơ chế biểu diễn không gian vector, giải pháp truy xuất ngữ nghĩa (Semantic Search), kỹ thuật tái xếp hạng (Re-ranking) và chiến lược tối ưu hóa chất lượng dữ liệu đầu vào cho hệ thống RAG và Tác tử AI (AI Agents).

---

### 📂 Danh Mục Tài Liệu (Thứ Tự Đọc Khuyến Nghị)

| Thứ Tự | Tài Liệu | Trọng Tâm Nghiên Cứu & Nội Dung Cốt Lõi |
| :---: | :--- | :--- |
| **01** | 📖 [**01_semantic_search_and_reranking.md**](01_semantic_search_and_reranking.md) | **Chuyên khảo toàn diện về Tìm kiếm Ngữ nghĩa, Tái xếp hạng & Cẩm nang RAG Tiên Tiến:**<br>• **Nghịch lý từ khóa (Lexical Matching):** Thí nghiệm tư duy *"Vintage Magic Card"* vs. *"Vintage Magic Kit"*, giới hạn của BM25 và N-gram.<br>• **Hình học không gian Vector & Hiện tượng Dị hướng (Anisotropy):** Lời nguyền số chiều, hiện tượng "hình nón hẹp" (Narrow Cone Phenomenon, Ethayarajh 2019), giải pháp làm trắng BERT-Whitening (SVD Zero-Centering) và học tương phản bảo toàn tính đồng đều (Uniformity).<br>• **Phân loại tác vụ:** Asymmetric Search (RAG, Query ngắn vs Văn bản dài) vs. Symmetric Search (Title-to-Title, FAQ).<br>• **Giải phẫu 3 trường phái kiến trúc:** **Bi-Encoder / SBERT** (Mô hình 2 tháp, Vector DB) vs. **Cross-Encoder** (Full Cross-Attention) vs. **ColBERT** (Late Interaction & toán tử MaxSim).<br>• **Pipeline Phễu hai giai đoạn (Two-Stage):** Bi-Encoder thu hồi Top-50 ứng viên $\to$ Cross-Encoder tái định vị Top-3.<br>• **Chiến lược Chunking:** Sliding Window có gối đầu (Overlap), Natural Whitespace, Semantic Clustering.<br>• **Thực nghiệm Benchmarking:** So sánh OpenAI Ada-002 vs. Open-source MPNet Base, tác động tăng trưởng Recall@1 (+24.3%), độ trễ thực thi (40 giây vs 24 phút).<br>• **Fine-tuning:** Tinh chỉnh Cross-encoder và Bi-encoder trên dữ liệu domain chuyên biệt.<br>• **Cẩm nang toàn tập Kiến trúc RAG Tiên tiến (Advanced & Agentic RAG):** Tiến hóa 3 thế hệ (Naive $\to$ Advanced $\to$ Modular/Agentic), Pre-retrieval (HyDE, Multi-Query, Step-Back), Chunking & Indexing (Parent Document, Anthropic Contextual Retrieval, GraphRAG), Post-retrieval (RRF, Cross-Encoder Re-rank), RAG Tác tử tự phản tư (Self-RAG, CRAG, Adaptive RAG), Bảng so sánh 9 kỹ thuật RAG định lượng và Cây quyết định kiến trúc thực chiến.<br>• **Tài liệu tham khảo học thuật:** 14 bài báo khoa học cốt lõi (SBERT, DPR, ColBERT, Lost in the Middle, HyDE, Contextual Retrieval, GraphRAG, Self-RAG, CRAG, Anisotropy, Whitening). |
| **02** | 📖 [**02_rag_architecture_and_components.md**](02_rag_architecture_and_components.md) | **Giải phẫu 4 cấu phần cốt lõi & vòng lặp điều phối của RAG (Inside RAG):**<br>• **Mô hình tư duy:** Khắc phục ảo giác tự tin (Confident Hallucination), so sánh Thí sinh thi mở sách (Open-Book Exam) vs thi đóng sách (Zero-RAG).<br>• **4 cấu phần cốt lõi:** Embeddings & Retriever (FAISS + OpenAI), Ranker / Re-ranker (Cohere Rerank - phân biệt tương đồng từ vựng vs liên quan ngữ cảnh), Generator (ChatOpenAI - Temp factuality), Orchestration Layer (RetrievalQA / LCEL - Vị nhạc trưởng).<br>• **Vũ điệu 4 nhịp:** $\textbf{Retrieve} \to \textbf{Rank} \to \textbf{Generate} \to \textbf{Orchestrate}$.<br>• **Thực chiến mã nguồn:** Pipeline chuẩn mực với LangChain, FAISS `allow_dangerous_deserialization`, Contextual Compression và kiểm định Retriever độc lập.<br>• **Case Study:** Báo cáo đầu tư nông nghiệp thẳng đứng (Vertical Farming & IPM) - trích xuất số liệu chuẩn xác sẵn sàng cho slide gọi vốn VCs.<br>• **Thách thức & Hướng giải quyết:** Data Freshness (Dynamic Indexing), Context Limits (Compression), Ambiguous Queries (Multi-step Reasoning). |

---

## 🔗 Liên Kết Đến Các Chuyên Đề Khác

* Chuyên đề mạng nơ-ron: [[01-research-and-foundations/01-neural-networks/README|🧠 01-neural-networks]]
* Chuyên đề nền tảng LLM: [[01-research-and-foundations/02-llm-internals/README|📚 02-llm-internals]]
* Chuyển tiếp sang Trụ cột 2: [[02-prompt-and-context/README|✍️ Trụ cột 2: Prompt & Context Engineering]]
* Ứng dụng sang Trụ cột 3: [[03-building-agents/README|🛠️ Trụ cột 3: Building Agents]]
