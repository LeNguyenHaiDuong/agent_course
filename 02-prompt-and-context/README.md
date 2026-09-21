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
updated: 2026-09-21
---

# ✍️ TRỤ CỘT 2: PROMPT & CONTEXT ENGINEERING (KỸ THUẬT CÂU LỆNH & NGỮ CẢNH)

Trụ cột này đóng vai trò là **cầu nối nhận thức** giữa mô hình ngôn ngữ nền tảng (Trụ cột 1) và các hệ thống tác tử tự hành (Trụ cột 3). Trọng tâm ở đây là làm chủ nghệ thuật và khoa học điều khiển hành vi của LLM thông qua cấu trúc ngữ cảnh và chiến lược câu lệnh.

---

## 🗺️ Bản Đồ Cấu Trúc Trụ Cột 2

```text
02-prompt-and-context/
├── README.md                                    # (Tài liệu này) Giới thiệu tổng quan Trụ cột 2
└── prompt-engineering/                          # 🎯 Các kỹ thuật Prompt Engineering nâng cao
    ├── README.md                                # Danh mục các kỹ thuật & Lộ trình
    └── advanced_prompt_engineering_techniques.md# Phân tích chi tiết 8 kỹ thuật (CoT, ToT, DSP, CoD, OPRO)
```

---

## 📂 Danh Mục Chuyên Đề

### 1. [[02-prompt-and-context/prompt-engineering/README|Advanced Prompt Engineering Techniques]]
* **Trọng tâm:** 8 kỹ thuật câu lệnh nâng cao từ khóa học LinkedIn Learning (*Morten Rand-Hendriksen*):
  * **Định hình phong cách & dữ liệu:** Zero-Shot, Few-Shot (In-Context Learning).
  * **Chuỗi suy luận (Chain-of-Thought):** Zero-shot CoT (`Let's think step by step`), Few-shot CoT, Hybrid CoT, Optimization Prompting (OPRO / "Take a deep breath").
  * **Tăng cường tri thức & Lập luận đa nhánh:** Generated Knowledge Prompting, **Tree of Thoughts (ToT)** với cơ chế đa chuyên gia phản biện và tỉa cành (*pruning*).
  * **Điều hướng & Tóm tắt nén:** Directional Stimulus Prompting (DSP), **Chain of Density (CoD)** tóm tắt nén thực thể.
* **Tài liệu chi tiết:** [[advanced_prompt_engineering_techniques|advanced_prompt_engineering_techniques.md]]

---

## 🚀 Lộ Trình Mở Rộng Tiếp Theo

* `02_context_engineering_and_budgeting.md`: Kỹ thuật căn chỉnh ngân sách Token, Lost-in-the-middle, tiêm tri thức động (Dynamic Context Injection).
* `03_system_prompts_and_metaprompting.md`: Thiết kế System Instructions bảo mật, chống Jailbreak, System Prompting chuẩn cho AI Harness.

---

## 🔗 Điều Hướng Nhanh
* Trở về trang chủ: [[README|🏠 Vault Home MOC]]
* Chuyển sang Trụ cột 3: [[03-building-agents/README|🛠️ Trụ cột 3: Building Agents]]
