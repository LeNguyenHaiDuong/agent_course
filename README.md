---
title: "Agent Course: From Foundations to Autonomous AI Agents"
aliases:
  - Agent Course MOC
  - Vault Home
tags:
  - agent-course
  - moc
type: moc
created: 2026-09-20
updated: 2026-09-21
---

# Agent Course: From Foundations to Autonomous AI Agents

Kho tài liệu học tập, nghiên cứu và thực hành toàn diện về **Trí tuệ nhân tạo (AI)** được tối ưu hóa chuẩn **Obsidian Vault**: từ nền tảng **Học sâu & Mạng nơ-ron (Deep Learning & Neural Networks)**, kỹ thuật **Prompt & Context Engineering**, cho đến kiến trúc xây dựng **Hệ thống Tác tử Tự trị (Autonomous Agents & MCP)**.

> [!tip] Cấu Trúc Blog & Kho Tri Thức Markdown
> * 📚 **Blog / Knowledge Base:** Toàn bộ nội dung là các bài viết Markdown chuẩn hóa, phân cấp logic, dễ dàng đọc trực tiếp trên GitHub hoặc mở bằng bất kỳ trình đọc Markdown / Static Site Generator nào.
> * 🏷️ **Tags phân loại:** `#agent-course` `#research/neural-networks` `#research/llm` `#prompt-engineering` `#building-agents`

---

## 🗺️ Bản Đồ Kiến Trúc Kho Tài Liệu (3 Trụ Cột)

Repository được tổ chức theo cấu trúc blog phân tầng 3 trụ cột logic:

```text
agent_course/
├── README.md                                          # Mục lục tổng quan (Blog Root MOC)
│
├── 01-research-and-foundations/                       # 🔬 TRỤ CỘT 1: NGHIÊN CỨU & NỀN TẢNG HỌC THUẬT
│   ├── README.md                                      # Tổng quan & Lộ trình Trụ cột 1
│   ├── neural-networks/                               # 🧠 Mạng Nơ-ron Nhân tạo (ANN, CNN, RNN, Transformers, MoE)
│   │   ├── README.md
│   │   └── neural_networks_and_classifications.md     # Giải phẫu nơ-ron, Backpropagation, Hàm kích hoạt, Bản đồ phân loại
│   └── llm-internals/                                 # 📚 Bản chất Mô hình Ngôn ngữ Lớn (LLM Core & Pre-training)
│       ├── README.md
│       └── what_are_large_language_models.md          # Thí nghiệm điền từ, Transformer, AR vs AE, Scaling, Reasoning
│
├── 02-prompt-and-context/                             # ✍️ TRỤ CỘT 2: KỸ THUẬT CÂU LỆNH & QUẢN TRỊ NGỮ CẢNH
│   ├── README.md                                      # Tổng quan & Lộ trình Trụ cột 2
│   └── prompt-engineering/                            # 🎯 Kỹ thuật Prompt Engineering nâng cao
│       ├── README.md
│       └── advanced_prompt_engineering_techniques.md  # Chi tiết 8 kỹ thuật (CoT, ToT, DSP, CoD, OPRO)
│
└── 03-building-agents/                                # 🛠️ TRỤ CỘT 3: KỸ THUẬT XÂY DỰNG TÁC TỬ TỰ HÀNH
    ├── README.md                                      # Tổng quan & Lộ trình Trụ cột 3
    ├── ai_chat_systems_and_prompt_engineering.md      # 🏛️ Tài liệu kiến trúc dẫn nhập: Harness, Memory & 4 tầng tiến hóa
    ├── harness-and-memory/                            # 🗄️ Tầng 1: Bộ khung điều khiển & Hệ thống ghi nhớ
    │   └── README.md                                  # System Instructions, Context Drift, Dynamic Memory
    ├── tools-and-mcp/                                 # 🔌 Tầng 2: Giao thức kết nối công cụ & thế giới thực
    │   └── README.md                                  # Model Context Protocol (MCP), Tools, Resources
    └── loop-engineering/                             # 🔄 Tầng 3: Vòng lặp tự trị & Đội ngũ đa tác tử
        └── README.md                                  # ReAct, Plan-and-Execute, Evaluator-Optimizer, Subagents
```

---

## 📖 Danh Mục Tài Liệu Cốt Lõi (Wikilinks)

### 🔬 [[01-research-and-foundations/README|Trụ cột 1: Research & Foundations]]
* [[neural_networks_and_classifications|Neural Networks & Their Classifications]]: Giải phẫu nơ-ron nhân tạo, Forward Pass, Backpropagation & Chain Rule, các hàm kích hoạt (ReLU, GELU, SwiGLU), hàm mất mát, giải thuật tối ưu (SGD, AdamW), và bản đồ 8 họ kiến trúc từ MLP, CNN, RNN đến Transformer, GNN, Autoencoders, GAN, Diffusion và MoE.
* [[what_are_large_language_models|What Are Large Language Models?]]: Bản chất Language Modeling (Fill-in-the-blank), Tokenization (BPE), 4 bước nhảy vọt lịch sử (2001–2017), so sánh chuyên sâu Autoregressive (GPT) vs. Autoencoding (BERT) vs. Seq2Seq (T5), quy mô tham số, siêu tham số suy luận (`temperature`, `top_p`), và bản chất "Reasoning Machine".

### ✍️ [[02-prompt-and-context/README|Trụ cột 2: Prompt & Context Engineering]]
* [[advanced_prompt_engineering_techniques|Advanced Prompt Engineering Techniques]]: Chi tiết 8 kỹ thuật prompt từ khóa học LinkedIn Learning: Zero/Few-shot, CoT Family (Zero-shot CoT, Few-shot CoT, Hybrid CoT), Optimization Prompting (OPRO / "Take a deep breath"), Generated Knowledge, Tree of Thoughts (ToT), Directional Stimulus (DSP) và Chain of Density (CoD), kèm liên kết bài báo arXiv.

### 🛠️ [[03-building-agents/README|Trụ cột 3: Building Agents]]
* [[ai_chat_systems_and_prompt_engineering|Kiến trúc & Tiến hóa của các hệ thống AI Chat]]: Phân tích bản chất One-shot của LLM Core, giải phẫu AI Harness, cơ chế Memory (Dynamic & Semantic), SKILLS/Tools và 4 tầng tiến hóa từ Prompting đến Loop Engineering.
* [[03-building-agents/harness-and-memory/README|AI Harness & Memory Architecture]]: Bộ khung phần mềm, quản trị cửa sổ ngữ cảnh và phòng chống Context Drift.
* [[03-building-agents/tools-and-mcp/README|Model Context Protocol (MCP) & Tools]]: Giao thức chuẩn mở của Anthropic kết nối LLM với công cụ và dữ liệu ngoài.
* [[03-building-agents/loop-engineering/README|Loop Engineering & Autonomous Agents]]: Vòng lặp phản hồi tự trị: ReAct, Plan-and-Execute, Evaluator-Optimizer và Multi-agent workflows.
