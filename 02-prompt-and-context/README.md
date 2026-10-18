---
title: "Trụ Cột 2: Prompt & Context Engineering"
aliases:
  - Prompt and Context MOC
tags:
  - agent-course
  - prompt-engineering
  - moc
type: moc
created: 2026-09-21
updated: 2026-09-27
---

# ✍️ TRỤ CỘT 2: PROMPT & CONTEXT ENGINEERING (KỸ THUẬT CÂU LỆNH & NGỮ CẢNH)

Trụ cột này đóng vai trò là **cầu nối nhận thức** giữa mô hình ngôn ngữ nền tảng (Trụ cột 1) và các hệ thống tác tử tự hành (Trụ cột 3). Trọng tâm ở đây là làm chủ nghệ thuật và khoa học điều khiển hành vi của LLM thông qua cấu trúc ngữ cảnh, hoạch định ngân sách token và chiến lược câu lệnh có cấu trúc.

---

## 🗺️ Bản Đồ Cấu Trúc Trụ Cột 2

```text
02-prompt-and-context/
├── README.md                                    # (Tài liệu này) Giới thiệu tổng quan Trụ cột 2
└── 01-prompt-engineering/                       # 🎯 Toàn tập kỹ thuật Prompt & Context Engineering
    ├── README.md                                # Danh mục các kỹ thuật & Lộ trình
    ├── 01_advanced_prompt_engineering_techniques.md# Cẩm nang 10 kỹ thuật (CoT, ToT, Lost-in-Middle, Meta-Prompting)
    └── 02_dspy_and_programmatic_prompting.md    # Lập trình hóa Prompt với DSPy (Stanford NLP) & Tối ưu hóa tự động
```

---

## 📂 Danh Mục Chuyên Đề Cốt Lõi

### 📖 [Các Kỹ Thuật Prompt & Context Engineering Nâng Cao (Toàn Tập)](./01-prompt-engineering/01_advanced_prompt_engineering_techniques.md)
* **Định hình phong cách & dữ liệu:** Zero-Shot, Few-Shot (In-Context Learning qua Induction Heads).
* **Chuỗi suy luận (Chain-of-Thought):** Zero-shot CoT (`Let's think step by step`), Few-shot CoT, Hybrid CoT, Optimization Prompting (OPRO / "Take a deep breath").
* **Tăng cường tri thức & Lập luận đa nhánh:** Generated Knowledge Prompting, **Tree of Thoughts (ToT)** với cơ chế đa chuyên gia phản biện và tỉa cành (*pruning*).
* **Điều hướng & Tóm tắt nén:** Directional Stimulus Prompting (DSP), **Chain of Density (CoD)** tóm tắt nén thực thể đệ quy.
* **Quản trị Cửa sổ Ngữ cảnh & Token Budgeting:** Hiện tượng **Lost in the Middle** (đường cong chú ý hình chữ U của Liu et al. 2023), quy tắc kẹp bánh mì định vị Golden Context, và phân bổ ngân sách 4 khoang Token Budget.
* **Thiết kế System Instructions Chuẩn Hóa:** Cấu trúc thẻ XML phân tách ngữ nghĩa (`<role>`, `<context>`, `<rules>`, `<output_format>`), phân cấp thứ bậc chỉ thị chống Jailbreak.
* **Meta-Prompting:** Phương pháp sử dụng AI làm Kiến Trúc Sư Prompt tự sinh System Prompt đẳng cấp sản xuất.

### 🔬 [Lập Trình Hóa Prompt Với DSPy (Stanford NLP): Kỷ Nguyên Tối Ưu Hóa Tự Động](./01-prompt-engineering/02_dspy_and_programmatic_prompting.md)
* **Chấm dứt kỷ nguyên Prompting thủ công:** Giải quyết 3 điểm nghẽn chí mạng (Tính giòn/Brittleness, Model Lock-in, Thử-sai mò mẫm vô hướng); tương đồng lịch sử với bước chuyển từ Assembly sang Trình biên dịch C/Python.
* **Ba trụ cột kiến trúc DSPy:**
  * **Signatures:** Phân ly hoàn toàn đặc tả Input/Output khỏi ngôn ngữ hiển thị (Prompt Template).
  * **Modules:** Các khối nhận thức chuẩn hóa (`dspy.Predict`, `dspy.ChainOfThought`, `dspy.ReAct`, `dspy.ProgramOfThought`).
  * **Teleprompters / Optimizers:** Các thuật toán biên dịch và tự động tối ưu hóa prompt dựa trên hàm mục tiêu (Metric).
* **Giải thuật Tối ưu hóa Tiên tiến:**
  * `BootstrapFewShot` & Random Search: Tự động khai phá và chọn lọc các chuỗi suy luận mẫu (Demonstrations) thành công.
  * **MIPROv2 (Multi-prompt Instruction Proposal Optimizer):** Tối ưu hóa xác suất Bayesian kết hợp đồng thời Chỉ thị (Instructions) và Ví dụ (Few-shot Examples).
  * **COPRO & APE (Automatic Prompt Engineer):** Khám phá không gian chỉ thị tự nhiên qua kỹ thuật Coordinate Ascent.
* **Thực hành End-to-End & Chưng cất tri thức (BootstrapFinetune):** Xây dựng Enterprise Financial RAG Agent với DSPy và chưng cất tri thức từ mô hình lớn (GPT-4) sang mô hình mã nguồn mở cục bộ (LLaMA-3 8B).

---

## 🔗 Điều Hướng Nhanh
* Trở về trang chủ: [🏠 Vault Home MOC](../README.md)
* Chuyển sang Trụ cột 3: [🛠️ Trụ cột 3: Building Agents](../03-building-agents/README.md)
* Mở bản đồ trực quan: [🗺️ Visual Canvas](../Agent-Course-Overview.canvas)
