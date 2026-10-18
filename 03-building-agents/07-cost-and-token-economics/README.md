---
title: "07-cost-and-token-economics: Tối Ưu Hóa Chi Phí & Kinh Tế Token"
tags:
  - agent-course
  - token-economics
  - cost-optimization
type: moc
created: 2026-10-18
updated: 2026-10-18
---

# 07. Cost & Token Economics

Thư mục này nghiên cứu các giải pháp kiểm soát và tối ưu hóa chi phí token trong các vòng lặp tự trị dài hơi (Long-running Agentic Workflows).

## 📖 Danh Mục Tài Liệu
* [01_token_economics_and_cost_optimization.md](01_token_economics_and_cost_optimization.md):
  * **Giải phẫu chi phí vòng lặp:** Hiệu ứng cấp số nhân $\mathcal{O}(N^2)$ của context tích lũy.
  * **Model Cascading & Routing:** Phân tầng mô hình (Tier 1 Fast SLMs $\to$ Tier 2 Frontier $\to$ Tier 3 Reasoning), thuật toán FrugalGPT.
  * **Nén ngữ cảnh & Cắt tỉa quan sát:** Lọc kết quả thô của Tool tại biên, tóm tắt trượt (Rolling Summary).
  * **GPU Prefix Prompt Caching:** Tối ưu cấu trúc prompt đạt Cache Hit $>85\%$, giảm $80\%$ chi phí và độ trễ.
  * **Budget Circuit Breakers:** Cơ chế Soft Limit (chế độ tiết kiệm) và Hard Limit ngắt cứng khi vượt ngân sách.
