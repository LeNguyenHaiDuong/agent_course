# 🔄 LOOP ENGINEERING & AUTONOMOUS AGENTS

Thư mục này dành riêng để ghi chú cho các khóa học về **Loop Engineering** và các kiến trúc tác tử AI tự trị (Autonomous Agents).

---

## 📌 Khái Niệm Cốt Lõi Về Loop Engineering

* **Loop Engineering là gì?** Là việc thiết kế các vòng lặp phản hồi có kiểm soát (Feedback Loops) cho phép mô hình AI tự prompt chính nó, tự quan sát kết quả hành động và tiếp tục lặp lại cho đến khi đạt được tiêu chí hoàn thành mục tiêu.
* **Các mô hình phổ biến:**
  * **ReAct (Reason + Act):** Suy luận $\rightarrow$ Thực hiện hành động $\rightarrow$ Quan sát kết quả $\rightarrow$ Lặp lại.
  * **Plan-and-Execute:** Lập kế hoạch tổng thể trước $\rightarrow$ Thực thi từng bước con $\rightarrow$ Cập nhật lại kế hoạch nếu gặp sự cố.
  * **Evaluator-Optimizer:** Một agent tạo giải pháp $\rightarrow$ một agent khác đánh giá, phản hồi $\rightarrow$ tinh chỉnh lại cho đến khi đạt chuẩn.

---

## 📋 Cấu Trúc Ghi Chú Dự Kiến Cho Khóa Học Mới

```text
03-building-agents/loop-engineering/
├── README.md               # Trang mục lục này
├── 01_loop_fundamentals.md # Kiến trúc vòng lặp tự trị, điều kiện dừng (Stopping criteria)
├── 02_react_and_planning.md# Kỹ thuật ReAct, Plan-and-Solve
├── 03_multi_agent_teams.md # Đội ngũ đa tác tử (Orchestrator, Subagents, Handoffs)
└── 04_eval_and_testing.md  # Đo lường hiệu năng và kiểm thử Agent tự trị
```
