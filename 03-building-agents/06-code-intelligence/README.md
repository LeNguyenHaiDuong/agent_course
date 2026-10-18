---
title: "06-code-intelligence: Trí Tuệ Kho Mã Nguồn & Ngữ Cảnh Liên Phiên"
tags:
  - agent-course
  - code-intelligence
  - code-graphs
type: moc
created: 2026-10-18
updated: 2026-10-18
---

# 06. Code Intelligence & Repository Graph

Thư mục này nghiên cứu các kỹ thuật nâng cao giúp AI Agent hiểu sâu sắc toàn bộ kho mã nguồn lớn (Codebase Intelligence), vượt qua giới hạn của Vector RAG truyền thống.

## 📖 Danh Mục Tài Liệu
* [01_code_graphs_and_repository_intelligence.md](01_code_graphs_and_repository_intelligence.md):
  * **Code Property Graph (CPG):** Hợp nhất AST (Cú pháp), CFG (Luồng điều khiển) và DFG/PDG (Luồng dữ liệu).
  * **Chỉ mục Symbol chuẩn doanh nghiệp:** Giao thức SCIP & LSIF, phân giải tham chiếu chéo tệp (Go to Definition, Find all References).
  * **Graph-RAG & Blast Radius:** Thuật toán K-Hop Neighborhood và phân tích vùng ảnh hưởng khi refactor.
  * **Cross-Session Memory:** 5 kỹ thuật ghi nhớ lịch sử và ngữ cảnh dự án liên phiên (Memory Bank `CLAUDE.md`, Incremental Delta Cache, Session Compaction, ADRs).
