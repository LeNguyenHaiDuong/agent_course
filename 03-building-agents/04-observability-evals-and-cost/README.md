---
title: "Mô-đun 04: Observability, Evals & Cost Optimization"
aliases:
  - Observability and Evals MOC
  - Cost Optimization Overview
tags:
  - agent-course
  - building-agents
  - observability
  - evals
  - token-economics
  - prompt-compression
  - moc
type: moc
created: 2026-10-18
updated: 2026-10-18
---

# 📊 MÔ-ĐUN 04: OBSERVABILITY, EVALS & COST OPTIMIZATION

Thư mục này dành riêng để nghiên cứu và thực hành chuyên sâu về **Hạ tầng Quan sát (Observability)**, phương pháp luận **Đánh giá Tác tử (Agent Evals & LLM-as-a-Judge)**, mô hình toán học **Kinh tế học Token (Token Economics)** và các kỹ thuật phần cứng/thuật toán **Nén Prompt & Tối ưu hóa Bộ đệm (KV-Cache Engineering)**.

---

## 📌 Khái Niệm Cốt Lõi Về Evals & Token Economics

* **Tại sao Agent Evals khác biệt với Model Evals?** Model Evals đo lường năng lực ngôn ngữ tĩnh (MMLU, GSM8K). Trong khi đó, Agent Evals phải đo lường khả năng tương tác động trong môi trường bất định: Tỷ lệ hoàn thành mục tiêu (Pass@k), số lượt gọi công cụ dư thừa, khả năng tự hồi phục sau lỗi ngoại vi, và chi phí tài chính tích lũy trên mỗi nhiệm vụ.
* **Quy luật chi phí trong hệ thống tự trị:** Khi số bước lặp tăng lên, chi phí token prefill tăng theo hàm bậc hai nếu không có chiến lược nén và caching hiệu quả.

---

## 📂 Danh Mục Tài Liệu Theo Thứ Tự Đọc

* 📖 **[01_agent_evals_and_tracing.md - Hạ Tầng Quan Sát, Distributed Tracing & Đánh Giá Tác Tử](./01_agent_evals_and_tracing.md)**:
  * Sự khác biệt giữa kiểm thử LLM tĩnh và Agent động đa bước.
  * Chuẩn OpenTelemetry cho AI: Spans, Traces, và Metadata cấu trúc.
  * Bộ tiêu chí đánh giá cốt lõi: Task Completion Rate, Trajectory Efficiency, Tool Accuracy, Cost per Resolution.
  * Giám sát hệ thống thực chiến: Tích hợp OpenInference, LangSmith, Phoenix/Arize.
  * Thực hành Python: Hệ thống Tracing phân tán tự xây dựng cho Agent Loop.

* 📖 **[02_synthetic_benchmarks_and_llm_as_judge.md - Dữ Liệu Tổng Hợp, Benchmarking Tác Tử & LLM-as-a-Judge](./02_synthetic_benchmarks_and_llm_as_judge.md)**:
  * Phương pháp sinh tập kiểm thử đa dạng tự động bằng thuật toán **Evol-Instruct** (In-Depth & In-Breadth Evolution).
  * 4 Thiên kiến chí mạng của LLM Judge: Position Bias, Verbosity Bias, Self-Enhancement Bias, Egocentric Bias.
  * Kỹ thuật khắc phục sai số: **Swap Testing (Hoán vị vị trí)**, **Multi-Agent Judge Panels**, và trích xuất điểm xác suất qua Softmax Logits của G-Eval.
  * Tích hợp tự động hóa vào đường ống CI/CD GitHub Actions để chống hồi quy hiệu năng (Regression Testing).

* 📖 **[03_token_economics_and_cost_optimization.md - Kinh Tế Học Token & Tối Ưu Hóa Chi Phí Tác Tử Doanh Nghiệp](./03_token_economics_and_cost_optimization.md)**:
  * Mô hình toán học chi phí Agent: Chi phí tích lũy theo số bước lặp và khủng hoảng Prefill $O(N^2)$.
  * Ma trận phân tầng mô hình (Model Tiering & Cascading): Định tuyến linh hoạt giữa Big Brain (Claude 3.5 Sonnet / GPT-4o) và Small Brain (Haiku / Flash / Qwen 2.5 Coder).
  * Kỹ thuật Dynamic Output Truncation và ép khuôn token.
  * Chiến lược giám sát ngân sách thời gian thực: Hard Budget Caps, Soft Throttling, và Alerting Webhooks.

* 📖 **[04_prompt_compression_and_cache_engineering.md - Nén Prompt, Tối Ưu Hóa KV-Cache & RadixTree](./04_prompt_compression_and_cache_engineering.md)**:
  * Cơ sở toán học thông tin học (Information Theory): Khái niệm Shannon Entropy và Self-Information.
  * Thuật toán nén ngữ cảnh **LLMLingua**: Đo lường Perplexity phân phối để cắt tỉa token dư thừa, nén tới $5\times - 10\times$ mà không mất thông tin.
  * Giải phẫu phần cứng GPU: Cơ chế **PagedAttention (vLLM)** chia nhỏ KV-cache thành các khối bộ nhớ ảo chống phân mảnh RAM.
  * Cấu trúc dữ liệu **RadixTree / Prefix Tree**: Tái sử dụng KV-cache giữa nhiều nhánh rẽ của Multi-Agent và Tree-of-Thought.
  * Thực hành Python: Triển khai bộ nén prompt dựa trên Entropy và giả lập Radix Tree KV-Cache.

* 📖 **[05_speculative_decoding_and_inference_acceleration.md - Speculative Decoding & Tăng Tốc Suy Luận Vòng Lặp Tác Tử](./05_speculative_decoding_and_inference_acceleration.md)**:
  * Bản chất nghẽn Memory-Bandwidth trong pha Decode tự hồi quy: Chỉ số Arithmetic Intensity $AI \approx 1\text{ FLOP/Byte}$.
  * Thuật toán **Speculative Sampling** kết hợp Draft Model ($M_q$) và Target Model ($M_p$), kiểm chứng song song trong 1 Forward Pass qua Modified Rejection Sampling.
  * Chứng minh toán học tính bất biến phân phối: Tăng tốc $2\times - 3.5\times$ mà bảo đảm $100\%$ chất lượng và độ chính xác logic.
  * Các biến thể tiên tiến: **Tree-based Speculative Decoding** và kiến trúc không cần Draft model (**Medusa / Eagle Heads**).
  * Tối ưu hóa hạ tầng đa GPU: Continuous Batching và Tensor Parallelism cho Agent Loops.

* 📖 **[06_semantic_caching_and_vector_cache.md - Semantic Caching & Vector Cache Cho Tác Tử](./06_semantic_caching_and_vector_cache.md)**:
  * Sự bất lực của Exact Match Cache (Redis) trước sự đa dạng câu chữ của người dùng.
  * Cơ chế Semantic Cache: Chiếu câu hỏi vào không gian vector, so khớp Cosine Similarity vượt ngưỡng $\tau$, phản hồi sau $2\text{ms}$ với chi phí $0\text{ token}$.
  * Kỹ thuật hiệu chuẩn ngưỡng $\tau$ (Precision vs. Recall) và khóa kết hợp ngữ cảnh đa vai trò (Contextual Composite Keys).
  * Tăng tốc tra cứu bằng thuật toán Locality-Sensitive Hashing (LSH) và cơ chế dọn dẹp TTL.
  * Thực hành Code: Xây dựng `SemanticCacheEngine` bằng Python đo lường tỷ lệ Cache Hit Rate và chi phí tiết kiệm.

---

## 🔗 Điều Hướng Nhanh
* Quay lại Mô-đun trước: [🔄 Mô-đun 03: Loop & Multi-Agent Engineering](../03-loop-and-multi-agent-engineering/README.md)
* Chuyển sang Mô-đun kế tiếp: [🎯 Mô-đun 05: Specialized Agent Domains](../05-specialized-agent-domains/README.md)
* Trở về mục lục Trụ cột 3: [🛠️ Trụ Cột 3: Building Agents](../README.md)
* Trở về trang chủ Vault: [🏠 Vault Home MOC](../../README.md)
