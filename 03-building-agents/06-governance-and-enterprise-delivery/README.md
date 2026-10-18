---
title: "Mô-đun 06: Governance, Security & Enterprise Delivery"
aliases:
  - Governance and Enterprise Delivery MOC
  - Enterprise Agent Architecture Overview
tags:
  - agent-course
  - building-agents
  - governance
  - hitl
  - security
  - enterprise
  - mern-stack
  - moc
type: moc
created: 2026-10-18
updated: 2026-10-18
---

# 🛡️ MÔ-ĐUN 06: GOVERNANCE, SECURITY & ENTERPRISE DELIVERY

Thư mục này dành riêng để nghiên cứu và chuyển giao công nghệ cấp độ doanh nghiệp (Enterprise Grade): từ cơ chế tương tác người - máy (**Human-in-the-Loop & Human-on-the-Loop**), an ninh bảo mật và kiểm thử xâm nhập (**Security, Red Teaming & Guardrails**), cẩm nang xây dựng hệ thống tác tử doanh nghiệp toàn diện, cho đến kiến trúc ứng dụng fullstack hoàn chỉnh (**Fullstack MERN Agent Architecture**).

---

## 📌 Khái Niệm Cốt Lõi Về Quản Trị & Chuyển Giao Doanh Nghiệp

* **Tại sao hầu hết các PoC Tác tử thất bại khi lên Production?** Một hệ thống Agent hoạt động tốt trong phòng lab thường gãy đổ ở môi trường doanh nghiệp do thiếu 3 yếu tố sống còn:
  1. **Khả năng kiểm soát rủi ro (Risk Governance):** Không có ranh giới rõ ràng khi nào Agent được tự quyết và khi nào phải xin phê duyệt con người (HITL).
  2. **An ninh bảo mật đa tầng (Defense-in-Depth):** Không phòng thủ trước tấn công Indirect Prompt Injection và nguy cơ rò rỉ dữ liệu qua kênh ngầm.
  3. **Hạ tầng phân tán ổn định (Production Readiness):** Không có kiến trúc Event-driven, State Store bền vững, WebSocket streaming và giao diện người dùng tương tác trực tiếp.

---

## 📂 Danh Mục Tài Liệu Theo Thứ Tự Đọc

* 📖 **[01_hitl_and_hotl_human_agent_interaction.md - Quản Trị Tác Tử: Human-in-the-Loop (HITL) & Human-on-the-Loop (HOTL)](./01_hitl_and_hotl_human_agent_interaction.md)**:
  * **Bản chất quản trị:** Khủng hoảng "Thế lưỡng nan của quyền tự chủ" (The Autonomy Dilemma), cán cân rủi ro giữa Tốc độ tự động hóa và An toàn vận hành.
  * **Giải phẫu 3 mô hình tương tác:** Human-in-the-Loop (Can thiệp chặn trước đồng bộ), Human-on-the-Loop (Giám sát thụ động qua Telemetry & Kill-switches), và Human-out-of-the-Loop (Tự trị hoàn toàn có giới hạn).
  * **Ma trận phân loại rủi ro 4 cấp (Tiered Risk Matrix):** Tier 1 (Tự động 100%), Tier 2 (Shadow execution), Tier 3 (2-Phase Commit bắt buộc phê duyệt), Tier 4 (Cấm AI tự động).
  * **Kiến trúc kỹ thuật bất đồng bộ:** Cơ chế ngắt điểm dừng (`interrupt_before`), Replay Time-travel và Webhook notification đa kênh (Slack, Teams, Web UI).
  * **Thực hành Code:** Triển khai `TieredGovernanceEngine` Python hỗ trợ Time-travel debugging và Webhook approval.

* 📖 **[02_agent_security_red_teaming_and_guardrails.md - Bảo Mật Tác Tử, Red Teaming & Tường Lửa Ngăn Chặn Tấn Công](./02_agent_security_red_teaming_and_guardrails.md)**:
  * **Phân loại vectơ tấn công (OWASP Top 10 for LLMs):** Direct Jailbreak, Indirect Prompt Injection (IPI - Hiểm họa số 1), Side-Channel Exfiltration (Markdown images, DNS tunneling), Confused Deputy.
  * **Kiến trúc Dual-LLM (Privileged vs. Quarantined):** Tách biệt ranh giới nhận thức giữa mô hình đọc dữ liệu không an toàn và mô hình nắm giữ quyền gọi công cụ.
  * **Input & Output Guardrails:** Cơ chế Canary Tokens phát hiện rò rỉ System Prompt, làm mờ dữ liệu PII/Secrets (Presidio) và vô hiệu hóa các thẻ Markdown độc hại.
  * **Cô lập môi trường thực thi (Sandboxing):** So sánh Docker vs gVisor vs MicroVM (Firecracker/E2B), áp dụng seccomp và dropped Linux capabilities.
  * **Phương pháp luận Red Teaming & Thực hành Python:** Triển khai lớp `SecurityGuardrailEngine` toàn diện phòng chống tấn công.

* 📖 **[03_how_to_build_enterprise_ai_agents.md - Cẩm Nang Xây Dựng Tác Tử AI Cấp Độ Doanh Nghiệp Toàn Diện](./03_how_to_build_enterprise_ai_agents.md)**:
  * **Khung năng lực toàn diện (The Enterprise Framework):** 6 Cấu phần cấu thành hệ thống AI Agent sẵn sàng cho môi trường doanh nghiệp.
  * **Kiến trúc phân tán Microservices:** Tách biệt Ingestion Service, Planning/Orchestrator Service, Tool Execution Cluster, và Distributed State Checkpointer (Redis/PostgreSQL).
  * **Quản trị chi phí & SLA doanh nghiệp:** Đảm bảo thời gian đáp ứng (TTFT, Latency), tính dự đoán được về ngân sách và xử lý chuyển tiếp lỗi (Failover & Graceful Degradation).
  * **Quy chuẩn tuân thủ (Compliance & Auditability):** Chuẩn ISO 42001, SOC 2 Type II, EU AI Act và lưu trữ nhật ký kiểm toán bất biến (Immutable Audit Trails).

* 📖 **[04_fullstack_agent_mern_architecture.md - Kiến Trúc Ứng Dụng Tác Tử Toàn Diện Với MERN Stack](./04_fullstack_agent_mern_architecture.md)**:
  * **Kiến trúc Fullstack MERN hoàn chỉnh:** Tích hợp MongoDB Atlas (Hybrid Search & State Store), Express backend, React Frontend và Node.js runtime.
  * **Giao tiếp thời gian thực:** Triển khai Server-Sent Events (SSE) và WebSockets để stream suy luận ReAct và hiển thị tiến trình gọi công cụ động.
  * **Giao thức MCP trong Node.js:** Sử dụng `@modelcontextprotocol/sdk` để kết nối các công cụ nghiệp vụ qua `stdio` và `SSE`.
  * **Thực hành Fullstack:** Mã nguồn hoàn chỉnh từ UI tương tác phê duyệt HITL đến backend xử lý luồng sự kiện bất đồng bộ.

* 📖 **[05_adversarial_fuzzing_and_automated_agent_red_teaming.md - Adversarial Fuzzing & Automated Agent Red-Teaming](./05_adversarial_fuzzing_and_automated_agent_red_teaming.md)**:
  * **Phương thức tấn công đa lượt:** Attacker Agent vs. Target Agent, chu trình trinh sát, đột biến và đầu độc trạng thái.
  * **Các giải thuật đột biến đối kháng:** PAIR (Prompt Automatic Iterative Refinement), TAP (Tree of Attacks with Pruning), Typoglycemia và Cipher bypasses.
  * **Bắn phá tham số công cụ (Tool-Exploit Fuzzing):** Path traversal, SSRF đám mây, Command chaining và Privilege escalation trong MCP servers.
  * **Continuous Red-Teaming trong CI/CD:** Đo lường chỉ số phòng thủ ADR (Attack Defense Rate) và MTTC (Mean Turns to Compromise).
  * **Thực hành Code:** Triển khai `AutomatedAgentRedTeamer` bằng Python tự động sinh biến thể tấn công và xuất báo cáo an toàn.

* 📖 **[06_cryptographic_audit_trails_and_compliance.md - Cryptographic Audit Trails & Enterprise Compliance](./06_cryptographic_audit_trails_and_compliance.md)**:
  * **Sự vô dụng của plaintext logs:** Tại sao log thông thường không thể dùng làm bằng chứng pháp lý trước tòa.
  * **Khung pháp lý quốc tế:** Tuân thủ EU AI Act (Điều 12), SOC 2 Type II và HIPAA cho AI Agent tự hành.
  * **Kiến trúc chuỗi băm liên hoàn (Hash Chaining):** $\mathcal{H}_i = \text{SHA256}(\mathcal{H}_{i-1} \parallel T_i \parallel \text{Payload})$, tự động phát hiện mọi hành vi sửa xóa gian lận trong 1ms.
  * **Bộ lọc PII Redaction:** Tự động làm mờ số thẻ, mật khẩu, API keys trước khi ký số.
  * **Thực hành Code:** Triển khai `CryptographicAuditTrailEngine` bằng Python với cơ chế kiểm tra tính toàn vẹn và phát hiện xâm nhập trái phép.

---

## 🔗 Điều Hướng Nhanh
* Quay lại Mô-đun trước: [🎯 Mô-đun 05: Specialized Agent Domains](../05-specialized-agent-domains/README.md)
* Trở về mục lục Trụ cột 3: [🛠️ Trụ Cột 3: Building Agents](../README.md)
* Trở về trang chủ Vault: [🏠 Vault Home MOC](../../README.md)
* Xem bản đồ Canvas: [🗺️ Mở Visual Canvas](../../Agent-Course-Overview.canvas)
