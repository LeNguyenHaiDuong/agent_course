---
title: "Trụ Cột 3: Building Agents"
aliases:
  - Building Agents MOC
  - Autonomous Agents Architecture
tags:
  - agent-course
  - building-agents
  - moc
type: moc
created: 2026-09-20
updated: 2026-09-21
---

# 🛠️ TRỤ CỘT 3: BUILDING AGENTS (KỸ THUẬT XÂY DỰNG TÁC TỬ TỰ HÀNH)

Trụ cột này là đích đến tối thượng của khóa học: **Biến một mô hình ngôn ngữ tĩnh (Static One-Shot LLM) thành một Hệ thống Tác tử Tự trị (Autonomous Agentic System)** có khả năng quan sát môi trường, suy luận nhiều bước, tự gọi công cụ và tự sửa lỗi để hoàn thành các mục tiêu phức tạp.

---

## 🗺️ Bản Đồ Cấu Trúc Trụ Cột 3

```text
03-building-agents/
├── README.md                                    # (Tài liệu này) Giới thiệu tổng quan Trụ cột 3
├── ai_chat_systems_and_prompt_engineering.md    # 🏛️ Tài liệu kiến trúc dẫn nhập: Harness, Memory & 4 tầng tiến hóa
│
├── harness-and-memory/                          # 🗄️ Tầng 1: Bộ khung điều khiển & Hệ thống ghi nhớ
│   └── README.md                                # System Instructions, Context Drift, Dynamic Memory
│
├── tools-and-mcp/                               # 🔌 Tầng 2: Giao thức kết nối công cụ & thế giới thực
│   └── README.md                                # Model Context Protocol (MCP), Function Calling, Tools
│
└── loop-engineering/                           # 🔄 Tầng 3: Vòng lặp tự trị & Đội ngũ đa tác tử
    └── README.md                                # ReAct, Plan-and-Execute, Evaluator-Optimizer, Subagents
```

---

## 📂 Danh Mục Các Thành Phần Kiến Trúc

### 🏛️ Tài Liệu Kiến Trúc Nền Tảng (Foundational Architecture)
* 📖 [[ai_chat_systems_and_prompt_engineering|Kiến trúc & Tiến hóa của các hệ thống AI Chat]]:
  * Phân tích bản chất One-Shot và tính tĩnh (Static) của LLM Core.
  * Giải phẫu một AI Software Harness (System Instructions, Chat History, Memory, SKILLS & Tools).
  * 3 cấu phần của hệ thống Memory (User Profile, Dynamic Memory, Semantic Retrieval).
  * 4 cấp độ tiến hóa từ Prompting đến Agentic Loop Engineering.

---

### 1. [[03-building-agents/harness-and-memory/README|AI Harness & Memory Architecture]]
* **Trọng tâm:** Bộ khung phần mềm quản lý tương tác giữa người dùng và LLM Core.
* **Nhiệm vụ:**
  * Quản trị cửa sổ ngữ cảnh (Context Window Hygiene, chống Context Drift khi code/debug dài).
  * Cơ chế bộ nhớ động (Dynamic Memory Extraction) và truy vấn lịch sử qua Semantic Search.
  * Phân quyền thực thi và cô lập môi trường (Sandboxing).

### 2. [[03-building-agents/tools-and-mcp/README|Model Context Protocol (MCP) & Tool Integration]]
* **Trọng tâm:** Giao thức chuẩn mở của Anthropic kết nối LLM với thế giới thực.
* **Nhiệm vụ:**
  * Mô hình Client-Host-Server trong MCP.
  * Xây dựng và tích hợp MCP Tools (chạy lệnh, gọi API, thao tác tệp tin) và Resources (truy xuất database, tài liệu).
  * Bảo mật và kiểm soát quyền hạn trong giao thức MCP.

### 3. [[03-building-agents/loop-engineering/README|Loop Engineering & Autonomous Workflows]]
* **Trọng tâm:** Thiết kế các vòng lặp phản hồi (Feedback Loops) tự động hóa.
* **Nhiệm vụ:**
  * Vòng lặp **ReAct (Reason + Act)**: Suy luận $\rightarrow$ Hành động $\rightarrow$ Quan sát.
  * Luồng **Plan-and-Execute**: Lập kế hoạch tổng thể $\rightarrow$ Thực thi từng bước con $\rightarrow$ Cập nhật kế hoạch.
  * Luồng **Evaluator-Optimizer**: Đánh giá $\rightarrow$ Phản biện $\rightarrow$ Tinh chỉnh cho đến khi đạt tiêu chí dừng.
  * Phối hợp đa tác tử (Multi-agent teams, Subagent delegation).

---

## 🔗 Điều Hướng Nhanh
* Trở về trang chủ: [[README|🏠 Vault Home MOC]]
* Xem bản đồ Canvas: [[Agent-Course-Overview.canvas|🗺️ Mở Visual Canvas]]
