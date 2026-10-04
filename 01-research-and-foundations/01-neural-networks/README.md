# 🧠 NỀN TẢNG MẠNG NƠ-RON NHÂN TẠO (NEURAL NETWORKS)

Thư mục này nghiên cứu cấu trúc, toán học và các phân loại kiến trúc của **Mạng nơ-ron nhân tạo (Artificial Neural Networks - ANN)** — nền tảng cốt lõi của toàn bộ lĩnh vực Học sâu (Deep Learning).

---

## 📂 Danh Mục Tài Liệu

| Tài liệu | Mô tả chi tiết & Các họ kiến trúc khảo sát |
| :--- | :--- |
| 🧬 [**Neural Networks & Their Classifications**](neural_networks_and_classifications.md) | **Chuyên khảo toán học, phân loại & chẩn đoán toàn diện (1,500 dòng):**<br>• **Nền tảng & Giải tích:** Giải phẫu Perceptron, Định lý xấp xỉ vạn năng (Universal Approximation Theorem), Forward/Backpropagation với Ma trận sai số độ nhạy $\boldsymbol{\delta}$, 6 hàm kích hoạt (Sigmoid $\to$ SwiGLU), Khởi tạo trọng số (Xavier/He), Chuẩn hóa (BatchNorm, LayerNorm, RMSNorm), Tối ưu hóa (SGD, Adam, AdamW).<br>• **Kiến trúc liên kết:** FNN/MLP, CNN (Toán học Kernel, Stride, Padding, Receptive Field, ví dụ tính số học từng bước, LeNet $\to$ AlexNet $\to$ VGG $\to$ ResNet $\to$ ConvNeXt), RNN/LSTM/GRU (Khai triển BPTT, Phân tích bán kính phổ, CEC & 4 phương trình cổng), Transformer (Scaled Dot-Product Attention, Multi-Head, RoPE, Pre-LN vs RMSNorm, Encoder/Decoder/ViT), GNN (Khung Message Passing MPNN, GCN, GAT, GraphSAGE).<br>• **Mô thức tạo sinh:** Autoencoders (AE, DAE, VAE với chứng minh ELBO & Reparameterization Trick, VQ-VAE), GAN (Minimax Game, Cân bằng Nash & JSD, WGAN-GP với khoảng cách Wasserstein, StyleGAN), Diffusion Models (DDPM Markov chains, Closed-form Gaussian marginal, U-Net khử nhiễu, CFG, Latent Diffusion SDXL, Diffusion Transformer DiT).<br>• **Kiến trúc hiện đại:** Sparse Mixture of Experts (MoE Top-k Gating, Auxiliary Load Balancing Loss, Mixtral 8x7B, DeepSeek-V3), State Space Models (SSM LTI, Rời rạc hóa ZOH, Góc nhìn kép Đệ quy/Tích chập, Đột phá Mamba Selective Scan).<br>• **Bảng so sánh 10 họ kiến trúc & Cây quyết định chọn mô hình thực tế.**<br>• **Chẩn đoán & Xử lý sự cố động học (Diagnostics & Debugging):** Giải phẫu chi tiết kèm ví dụ bằng số thực tế cho 7 bệnh lý kinh điển: Triệt tiêu Gradient (Vanishing), Bùng nổ Gradient (Exploding & Gradient Clipping), Nơ-ron Chết (Dying ReLU), Học quá mức (Overfitting & Dropout/Data Augmentation), Trôi dạt phân phối nội tại (Internal Covariate Shift), Điểm yên ngựa (Saddle Points), Sập chế độ (Mode Collapse trong GAN), kèm **Bảng tra cứu đơn thuốc xử lý nhanh (Debugging Cheat Sheet)**. |

---

## 🔗 Liên Kết Đến Các Chuyên Đề Khác

* Chuyên đề tiếp theo: [[01-research-and-foundations/02-llm-internals/README|📚 02-llm-internals - LLM Internals & Mechanisms]]
* Quay lại mục lục: [[01-research-and-foundations/README|🔬 Trụ Cột 1: Research & Foundations]]

