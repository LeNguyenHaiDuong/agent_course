---
title: "Tầng 4: Observability, Evals & Agent Governance"
aliases:
  - Observability and Evals MOC
  - Agent Evals Overview
tags:
  - agent-course
  - building-agents
  - observability
  - evals
  - tracing
  - moc
type: moc
created: 2026-09-27
updated: 2026-09-27
---

# 📊 OBSERVABILITY, EVALS & AGENT GOVERNANCE
## Giám Sát Phân Tán (Distributed Tracing), Đánh Giá Chất Lượng (Evals Frameworks) & Kiểm Soát Vận Hành Production

Thư mục này nghiên cứu và lưu trữ các chuẩn mực đo lường định lượng, khung đánh giá tự động (Evals Frameworks), kiến trúc vết phân tán (Distributed Tracing với OpenTelemetry & Langfuse), và các phương pháp giải trừ thiên vị nhận thức khi áp dụng mô hình LLM-as-a-Judge trong doanh nghiệp.

---

## 📌 Khái Niệm Cốt Lõi Về Observability & Evals

* **Khoảng cách giữa PoC và Production:** Một Agent chạy mượt mà trong phòng thí nghiệm với 5 câu hỏi thử nghiệm vẫn có thể sụp đổ trên môi trường thực tế nếu không có hệ thống đo lường ranh giới an toàn và độ tin cậy.
* **3 Trụ Cột Đánh Giá Tác Tử:**
  1. **Pre-release Offline Evals:** Đo lường trên bộ dữ liệu kiểm chuẩn chuẩn mực (Golden Datasets) trước khi triển khai mã nguồn mới.
  2. **CI/CD Regression Testing:** Tích hợp kiểm thử đơn vị tự động (Unit Tests for Prompts/Agents) qua DeepEval và `pytest`.
  3. **Online Production Observability:** Ghi vết chi tiết từng chặng (Spans, Tokens, Latency, Tool Calls) qua Langfuse và chuẩn OpenTelemetry.

---

## 📂 Danh Mục Tài Liệu Chuyên Sâu

* 📖 **[[01_agent_evals_and_tracing|01_agent_evals_and_tracing.md - Hệ Thống Giám Sát, Đo Lường & Đánh Giá Tác Tử AI]]**:
  * **Hạ tầng Tracing phân tán:** Chuẩn ngữ nghĩa OpenTelemetry GenAI Semantic Conventions, Cây vết (Trace Tree: Spans, Events), và code mẫu tích hợp Langfuse Python cho ReAct Agent.
  * **Khung đo lường RAG:** Bộ ba chỉ số Ragas Triad (Faithfulness, Answer Relevance, Context Precision, Context Recall) và kiểm thử hồi quy bằng DeepEval.
  * **Giải phẫu chuyên sâu LLM-as-a-Judge:** 4 thiên vị cố hữu (*Position Bias, Verbosity Bias, Self-Enhancement Bias, Leniency Bias*) và chiến lược hóa giải; Kỹ thuật **G-Eval** kết hợp chuỗi tư duy CoT và xác suất Softmax Token; So sánh Pairwise vs. Single-score Rubrics.
  * **Benchmark tác tử thực chiến:** Tiêu chuẩn SWE-bench (GitHub issues thực tế) và GAIA (Trợ lý đa năng đa phương thức); Đo lường Tool Calling Accuracy và đường cong Pareto giữa Tỷ lệ hoàn thành tác vụ (TCR) vs. Chi phí vận hành.
  * **Phương pháp tạo tập kiểm thử tổng hợp (Synthetic Testset Generation):** Kỹ thuật Evol-Instruct tự động sinh dữ liệu kiểm chuẩn từ kho tài liệu nội bộ.
  * **Giám sát liên tục & Vòng lặp phản hồi:** Thu thập tín hiệu người dùng ngầm định & tường minh, phát hiện trôi dạt ngữ nghĩa (Semantic Drift Detection).

---

## 🔗 Điều Hướng Nhanh
* Bản thiết kế doanh nghiệp: [[how_to_build_enterprise_ai_agents|🏗️ Cẩm Nang Toàn Tập Xây Dựng AI Agent Doanh Nghiệp]]
* Trở về mục lục Trụ cột 3: [[03-building-agents/README|🛠️ Trụ Cột 3: Building Agents]]
* Trở về trang chủ Vault: [[README|🏠 Vault Home MOC]]
* Xem bản đồ Canvas: [[Agent-Course-Overview.canvas|🗺️ Mở Visual Canvas]]
