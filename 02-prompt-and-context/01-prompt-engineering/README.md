# 🎯 MODULE 1: PROMPT ENGINEERING & IN-CONTEXT LEARNING

Thư mục này lưu trữ toàn bộ các ghi chú, phân tích kỹ thuật và mẫu câu lệnh liên quan đến Prompt Engineering từ các khóa học và bài báo nghiên cứu khoa học.

---

## 📑 Tài Liệu Đã Có

* **[[advanced_prompt_engineering_techniques|Các Kỹ Thuật Prompt Engineering Nâng Cao]]**:
  * Tổng hợp toàn bộ các kỹ thuật prompting kinh điển & nâng cao: Zero/Few-Shot, CoT Family, OPRO, Tree of Thoughts (ToT), Directional Stimulus, Chain of Density, Lost-in-the-Middle context management, XML System Instructions và Meta-Prompting.
  * Phân tích bản chất kỹ thuật, trích đoạn prompt mẫu thực tế, sơ đồ luồng Mermaid, ma trận quyết định và danh mục trích dẫn bài báo nghiên cứu arXiv / GitHub.
* **[[02_dspy_and_programmatic_prompting|Lập Trình Hóa Prompt Với DSPy (Stanford NLP) & Tối Ưu Hóa Tự Động]]**:
  * Chuyển dịch mô thức từ "cắt gọt chuỗi prompt thủ công" sang **khung lập trình khai báo (Declarative Programming)**.
  * Ba trụ cột kiến trúc: **Signatures** (đặc tả Input/Output độc lập), **Modules** (`dspy.Predict`, `dspy.ChainOfThought`, `dspy.ReAct`, `dspy.ProgramOfThought`), và **Teleprompters / Optimizers** (`BootstrapFewShot`, `MIPROv2`, `COPRO`, `BootstrapFinetune`).
  * Tự động hóa sinh prompt, tự động chọn few-shot demonstrations theo hàm đo lường (Metric), giải thuật tối ưu hóa Bayesian cho chỉ thị và chưng cất tri thức (Knowledge Distillation) từ mô hình lớn sang mô hình cục bộ.

---

## 📂 Các Kỹ Thuật Đang Quản Lý

* **Nhóm Định Hình Phong Cách & Dữ Liệu:**
  * Zero-Shot Prompting
  * Few-Shot Prompting (In-Context Learning qua Induction Heads)
* **Nhóm Chuỗi Suy Luận Tuyến Tính (Chain-of-Thought):**
  * Zero-Shot CoT (`Let's think step by step`)
  * Few-Shot CoT
  * Zero-plus-Few-Shot Hybrid CoT
  * Optimization Prompting (`Take a deep breath and work on this problem step-by-step` / OPRO)
* **Nhóm Tăng Cường Tri Thức:**
  * Generated Knowledge Prompting (Quy trình 2 pha: phát sinh tri thức và tích hợp suy luận)
* **Nhóm Cây Suy Luận Đa Nhánh:**
  * Tree of Thoughts (ToT - Cơ chế nhiều chuyên gia phản biện & tỉa cành)
* **Nhóm Nén & Định Hướng:**
  * Directional Stimulus Prompting (DSP)
  * Chain of Density (CoD - Tóm tắt đệ quy 5 vòng giữ nguyên số từ)
* **Nhóm Lập Trình Khai Báo & Tối Ưu Hóa Tự Động (DSPy Paradigm):**
  * Declarative Signatures & In/Out Schemas
  * Cognitive Modules (`Predict`, `ChainOfThought`, `ReAct`, `ProgramOfThought`)
  * Automatic Prompt Optimization (`BootstrapFewShot`, `MIPROv2` Bayesian Instruction Tuning, `COPRO`/APE)
  * Multi-stage Metric Evaluation & Model-Agnostic Compilation
