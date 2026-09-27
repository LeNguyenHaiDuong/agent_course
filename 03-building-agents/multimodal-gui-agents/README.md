---
title: "Tầng Mở Rộng: Multimodal GUI Agents & Computer-Use"
aliases:
  - Multimodal GUI Agents MOC
  - Computer Use MOC
tags:
  - agent-course
  - building-agents
  - multimodal
  - gui-agents
  - computer-use
  - moc
type: moc
created: 2026-09-27
updated: 2026-09-27
---

# 🖥️ MULTIMODAL GUI AGENTS & COMPUTER-USE

Thư mục này lưu trữ các nghiên cứu kiến trúc, kỹ thuật nhận thức thị giác và hướng dẫn thực hành xây dựng các tác tử AI có khả năng tương tác trực tiếp với giao diện người dùng đồ họa (GUI) và hệ điều hành thông qua màn hình (Pixels), chuột và bàn phím.

---

## 📌 Khái Niệm Cốt Lõi Về Computer-Use

* **Vượt qua giới hạn của API:** Trong khi các Agent truyền thống yêu cầu các API có cấu trúc ([[01_mcp_architecture|MCP]]), phần lớn các phần mềm doanh nghiệp cũ và ứng dụng desktop không có API. Tác tử GUI giải quyết vấn đề này bằng cách nhìn màn hình và tương tác như một con người thực sự.
* **3 Cột Trụ Kỹ Thuật:**
  1. **Visual UI Grounding:** Căn chỉnh không gian để nhận diện các nút bấm, icon, input field nhỏ qua **Set-of-Mark (SoM) Prompting** và **OmniParser**.
  2. **VLA (Vision-Language-Action):** Chuyển dịch chuỗi suy luận thị giác thành các hành động nguyên thủy trên OS (`click`, `double_click`, `type`, `hotkey`, `scroll`).
  3. **Hệ Thống Thử Nghiệm OSWorld:** Đánh giá năng lực tác tử trên môi trường desktop Ubuntu hoàn chỉnh.

---

## 📂 Danh Mục Tài Liệu Chuyên Sâu

* 📖 **[[01_multimodal_gui_and_computer_use|01_multimodal_gui_and_computer_use.md - Kỷ Nguyên Tác Tử Tương Tác Trực Quan Màn Hình & Hệ Điều Hành]]**:
  * **Khủng hoảng & Triết lý:** Nghịch lý "Vật chất tối của API", chuyển dịch từ API sang Pixels.
  * **Giải phẫu Grounding:** Thất bại của Direct Coordinate Regression, thuật toán Set-of-Mark (SoM), kiến trúc OmniParser, và Normalized Coordinates $[0, 1000] \times [0, 1000]$.
  * **Mô hình VLA & Vòng lặp OODA:** Không gian hành động nguyên thủy (Atomic Action Space), cơ chế Screen Capturing và PyAutoGUI Controller.
  * **Bệnh lý hệ thống thực chiến:** Render Latency & Race conditions, bùng nổ Token từ Screenshot & giải pháp Frame Differencing, bảo mật chống Visual Indirect Prompt Injection.
  * **Hệ thống Benchmark quốc tế:** Đánh giá chi tiết benchmark OSWorld, WebArena và Mind2Web.
  * **Thực hành Code hoàn chỉnh:** Pipeline Python xây dựng GUI Agent hoàn chỉnh kết hợp Claude 3.5 Sonnet Computer Use API.

---

## 🔗 Điều Hướng Nhanh
* Trở về mục lục Trụ cột 3: [[03-building-agents/README|🛠️ Trụ Cột 3: Building Agents]]
* Trở về trang chủ Vault: [[README|🏠 Vault Home MOC]]
* Xem bản đồ Canvas: [[Agent-Course-Overview.canvas|🗺️ Mở Visual Canvas]]
