---
title: "Prompt Compression & Cache Engineering: Kỹ Thuật Nén Ngữ Cảnh Không Mất Mát & Tối Ưu Hóa GPU KV-Cache"
tags:
  - agent-course
  - autonomous-agents
  - prompt-compression
  - kv-cache
  - vllm
  - radix-tree
  - token-economics
aliases:
  - Prompt Compression
  - GPU KV-Cache Engineering
  - LLMLingua Pruning
type: note
created: 2026-10-18
updated: 2026-10-18
---

# Prompt Compression & Cache Engineering: Kỹ Thuật Nén Ngữ Cảnh Không Mất Mát & Tối Ưu Hóa GPU KV-Cache

---

## 🧭 TỔNG QUAN ĐỊNH VỊ KIẾN TRÚC

Trong các tác tử AI tự hành vận hành nhiều bước (Multi-step Agents), hai thách thức hạ tầng lớn nhất đe dọa khả năng mở rộng (Scalability) của hệ thống là:
1. **Băng thông bộ nhớ GPU (GPU VRAM Memory Wall):** Mỗi token trong Context Window đều phải lưu trữ cặp khóa-giá trị ($K, V$) trong VRAM. Với các context dài $100.000$ tokens trên mô hình 70B, dung lượng KV-Cache của một request duy nhất có thể ngốn tới hàng chục GB VRAM, làm giảm mạnh số lượng luồng xử lý đồng thời (Concurrency / Throughput).
2. **Độ trễ Time-to-First-Token (TTFT):** Khi ngữ cảnh dài, thời gian tính toán giai đoạn nạp ban đầu (Prefill Phase) tăng theo cấp số bậc hai $\mathcal{O}(L^2)$, khiến người dùng phải đợi $5 - 10$ giây trước khi Agent sinh ra từ đầu tiên.

Để vượt qua rào cản này, các kỹ sư Agentic hiện đại kết hợp hai kỹ thuật bổ trợ:
* **Prompt Compression (Nén ngữ cảnh bằng lý thuyết thông tin):** Cắt tỉa các token rác không mang ngữ nghĩa bằng mô hình nhỏ (như LLMLingua / Perplexity Pruning), giảm $50\% - 75\%$ chiều dài prompt trước khi gửi tới LLM chính.
* **Cache Engineering (Kỹ nghệ Prefix Caching trên GPU):** Tận dụng cấu trúc dữ liệu cây cơ số (**RadixTree**) và phân trang bộ nhớ ảo (**PagedAttention** trong vLLM / SGLang) để tái sử dụng $90\%$ kết quả tính toán của các bước trước đó.

```
┌────────────────────────────────────────────────────────────────────────────────────────┐
│                        COMPRESSION & CACHING PIPELINE                                  │
├────────────────────────────────────────────────────────────────────────────────────────┤
│ Raw Prompt (10.000 tokens thô: tài liệu RAG, Tool logs, Chat history)                 │
│                                │                                                       │
│                                ▼                                                       │
│ [ LLMLingua / Entropy Pruner ] ──► Loại bỏ token dư thừa, nén xuống còn 3.000 tokens  │
│                                │                                                       │
│                                ▼                                                       │
│ [ RadixTree Prefix Cache ]     ──► So khớp tiền tố trên GPU VRAM                       │
│                                    • 2.500 tokens TRÚNG CACHE (Đã tính sẵn KV)         │
│                                    • Chỉ tính toán mới 500 tokens!                     │
│                                │                                                       │
│                                ▼                                                       │
│ [ LLM Generation ]             ──► TTFT giảm từ 4.2s xuống 0.2s | Chi phí giảm 85%!   │
└────────────────────────────────────────────────────────────────────────────────────────┘
```

---

## 1. NỀN TẢNG TOÁN HỌC: LÝ THUYẾT THÔNG TIN & PERPLEXITY PRUNING

Không phải từ ngữ nào trong ngôn ngữ tự nhiên cũng mang cùng một lượng thông tin. Trong tiếng Anh hay tiếng Việt, các mạo từ, giới từ, và các đoạn giải thích dài dòng thường có mức độ bất định (Entropy) rất thấp, nghĩa là LLM hoàn toàn có thể tự suy diễn ra chúng ngay cả khi bị xóa bỏ.

### 1.1. Khái Niệm Lượng Thông Tin (Self-Information)
Xét một chuỗi token $x_1, x_2, \dots, x_n$. Lượng thông tin chứa trong token $x_i$ khi biết ngữ cảnh phía trước $x_{<i}$ được đo lường bằng:

$$
I(x_i \mid x_{<i}) = - \log P(x_i \mid x_{<i})
$$

* Nếu một từ hoàn toàn đoán trước được ($P(x_i) \to 1$), lượng thông tin $I(x_i) \to 0$. Ta có thể **xóa bỏ token này mà không làm mất mát ngữ nghĩa**.
* Nếu một từ mang tính bất ngờ, chứa từ khóa chuyên môn hoặc số liệu quan trọng ($P(x_i) \ll 1$), lượng thông tin $I(x_i)$ rất lớn. Bắt buộc phải **giữ lại nguyên vẹn**.

### 1.2. Thuật Toán Nén LLMLingua
Được phát triển bởi Microsoft Research, LLMLingua sử dụng một mô hình ngôn ngữ nhỏ (Small Language Model như Llama-3.2-1B hoặc GPT-2 Small) làm **Bộ nén (Compressor)**:
1. Cho mô hình nhỏ tính toán perplexity của từng token trong câu.
2. Thiết lập ngưỡng phân vị $\tau_{\text{entropy}}$ dựa trên tỷ lệ nén mong muốn (ví dụ: muốn nén $60\%$).
3. Loại bỏ toàn bộ các token có $I(x_i) < \tau_{\text{entropy}}$, đồng thời giữ lại các token có cấu trúc cú pháp (dấu ngoặc, dấu hai chấm, tên hàm, số liệu).
4. Prompt sau khi nén có thể trông kỳ lạ đối với mắt người (giống như điện tín viết tắt), nhưng **LLM lớn vẫn giải mã và hiểu $100\%$ ý định ban đầu**.

---

## 2. KỸ NGHỆ GPU KV-CACHE: PAGEDATTENTION & RADIXTREE

### 2.1. Bản Chất Toán Học Của KV-Cache
Trong cơ chế Self-Attention:
* Token mới sinh ra ở bước $t$ cần tính ma trận tương tác $Q_t K_{1:t}^T$.
* Để tránh phải tính lại ma trận $K$ và $V$ của toàn bộ các token quá khứ từ $1$ đến $t-1$, các vector này được lưu lại trên VRAM gọi là **Key-Value Cache (KV-Cache)**.

Kích thước của KV-Cache cho một request được tính bằng:

$$
\text{Memory}_{\text{KV}} = 2 \times n_{\text{layers}} \times n_{\text{heads}} \times d_{\text{head}} \times L_{\text{context}} \times b_{\text{precision}}
$$

*Ví dụ:* Với mô hình Llama-3-70B ($L=80$, $n_{\text{heads}}=8$ trong GQA, $d=128$, float16 $b=2$ bytes):
Mỗi token tiêu tốn:
$$2 \times 80 \times 8 \times 128 \times 2 = 327.680\text{ bytes} \approx 0.32\text{ MB / token}$$
Với Context $100.000$ tokens, một Agent duy nhất ngốn **$32\text{ GB VRAM}$** chỉ riêng cho KV-Cache!

### 2.2. Kiến Trúc RadixTree Prefix Caching (vLLM & SGLang)
Trong các vòng lặp Agent, các bước liên tiếp thường dùng chung phần lớn ngữ cảnh:
* Bước 1: `[System Prompt] + [Task] + [Action 1] + [Obs 1]`
* Bước 2: `[System Prompt] + [Task] + [Action 1] + [Obs 1] + [Action 2] + [Obs 2]`

Nếu không có Prefix Caching, GPU phải tính lại từ đầu đoạn `[System Prompt] + [Task] + [Action 1] + [Obs 1]` ở Bước 2.
**Giải pháp RadixTree:** Biểu diễn không gian KV-Cache thành một cây tiền tố (Trie / Radix Tree):
* Các node trên cây lưu trữ các khối trang bộ nhớ (Memory Pages).
* Khi request mới tới, engine tìm kiếm đường đi dài nhất trên cây trùng với prompt đầu vào.
* Toàn bộ phần trùng khớp được giữ nguyên trong VRAM mà không tốn một phép tính ma trận nào!

---

## 3. MÃ NGUỒN THỰC CHIẾN: MÔ PHỎNG BỘ NÉN PERPLEXITY & RADIX CACHE

```python
"""
Mô-đun Kỹ nghệ Nén Ngữ cảnh và Quản trị Bộ nhớ KV-Cache
Yêu cầu thư viện: pip install pydantic
"""

from typing import List, Dict, Tuple, Optional
from pydantic import BaseModel
import math


class TokenEntropyPruner:
    """Bộ nén ngữ cảnh dựa trên lượng thông tin (Self-Information Pruning)"""

    # Bảng phân bổ xác suất từ giả lập của mô hình ngôn ngữ nén (SLM Compressor)
    # Token có xác suất càng cao thì lượng thông tin càng thấp
    COMMON_WORDS_PROB = {
        "the": 0.85, "a": 0.80, "an": 0.75, "is": 0.70, "are": 0.65,
        "and": 0.60, "or": 0.55, "to": 0.75, "in": 0.70, "of": 0.80,
        "that": 0.60, "it": 0.65, "with": 0.50, "for": 0.60, "as": 0.55
    }

    @classmethod
    def compute_self_information(cls, token: str) -> float:
        # I(x) = -log2(P(x))
        clean_word = token.lower().strip(".,!?:;()")
        prob = cls.COMMON_WORDS_PROB.get(clean_word, 0.05) # Từ khóa chuyên ngành có xác suất thấp -> Thông tin cao
        return -math.log2(prob)

    @classmethod
    def compress_prompt(cls, raw_text: str, target_ratio: float = 0.50) -> Tuple[str, float]:
        tokens = raw_text.split()
        if not tokens:
            return raw_text, 0.0

        # Tính lượng thông tin cho từng token
        token_info = [(tok, cls.compute_self_information(tok)) for tok in tokens]

        # Sắp xếp để tìm ngưỡng giữ lại
        sorted_info = sorted(token_info, key=lambda x: x[1], reverse=True)
        keep_count = max(1, int(len(tokens) * (1.0 - target_ratio)))
        threshold_info = sorted_info[keep_count - 1][1]

        # Lọc giữ lại các token có lượng thông tin cao, bảo toàn thứ tự ban đầu
        compressed_tokens = []
        for tok, info in token_info:
            # Luôn giữ lại số liệu, dấu ngoặc, và từ có thông tin cao
            if info >= threshold_info or any(char.isdigit() for char in tok) or len(tok) > 10:
                compressed_tokens.append(tok)

        compressed_text = " ".join(compressed_tokens)
        actual_compression = 1.0 - (len(compressed_tokens) / len(tokens))

        return compressed_text, actual_compression


class RadixCacheNode:
    """Node trong cây RadixTree đại diện cho một phân đoạn token đã lưu KV-Cache"""

    def __init__(self, prefix: str):
        self.prefix = prefix
        self.children: Dict[str, RadixCacheNode] = {}
        self.is_cached: bool = True


class RadixPrefixCacheSimulator:
    """Mô phỏng cơ chế GPU Prefix Cache hit/miss trong vLLM/SGLang"""

    def __init__(self):
        self.root = RadixCacheNode("")

    def insert(self, tokens: List[str]) -> None:
        curr = self.root
        for tok in tokens:
            if tok not in curr.children:
                curr.children[tok] = RadixCacheNode(tok)
            curr = curr.children[tok]

    def match_prefix(self, tokens: List[str]) -> Tuple[int, int]:
        """Trả về (số lượng token trùng Cache, số lượng token phải tính mới)"""
        curr = self.root
        matched_tokens = 0

        for tok in tokens:
            if tok in curr.children:
                matched_tokens += 1
                curr = curr.children[tok]
            else:
                break

        unmatched_tokens = len(tokens) - matched_tokens
        return matched_tokens, unmatched_tokens


# ==========================================
# CHẠY THỰC NGHIỆM MÔ PHỎNG NÉN & CACHE
# ==========================================
def main():
    print("=" * 65)
    print("THỬ NGHIỆM 1: PROMPT COMPRESSION (LLMLINGUA SIMULATOR)")
    print("=" * 65)

    raw_document = (
        "The system is currently operating in an unstable state and the database "
        "is returning connection timeout errors for user authentication requests. "
        "It is imperative to immediately inspect the configuration file at /etc/db.conf "
        "and restart the postgresql service on port 5432."
    )
    print(f"Văn bản gốc ({len(raw_document.split())} words):\n\"{raw_document}\"\n")

    compressed, ratio = TokenEntropyPruner.compress_prompt(raw_document, target_ratio=0.45)
    print(f"Văn bản sau khi nén ({len(compressed.split())} words, Tiết kiệm {ratio*100:.1f}% token):")
    print(f"\"{compressed}\"\n")
    print("Nhận xét: Các từ thừa ('the', 'is', 'and', 'it') bị cắt bỏ nhưng giữ nguyên")
    print("từ khóa cốt lõi: 'database', 'timeout', '/etc/db.conf', 'postgresql', '5432'.")

    print("\n" + "=" * 65)
    print("THỬ NGHIỆM 2: GPU PREFIX CACHING (RADIXTREE SIMULATOR)")
    print("=" * 65)

    cache = RadixPrefixCacheSimulator()

    # Bước 1 của Agent
    step_1_tokens = ["SYSTEM_PROMPT", "TOOLS_DEF", "USER_QUERY", "THOUGHT_1", "ACTION_1"]
    cache.insert(step_1_tokens)
    hit, miss = cache.match_prefix(step_1_tokens)
    print(f"Bước 1: Toàn bộ tính toán mới -> Hit: {hit} | Miss (Compute): {miss}")

    # Bước 2 của Agent: Kế thừa toàn bộ Bước 1 và sinh thêm Action 2
    step_2_tokens = ["SYSTEM_PROMPT", "TOOLS_DEF", "USER_QUERY", "THOUGHT_1", "ACTION_1", "OBS_1", "THOUGHT_2"]
    hit_2, miss_2 = cache.match_prefix(step_2_tokens)
    print(f"Bước 2: Hit: {hit_2} tokens ({hit_2/len(step_2_tokens)*100:.1f}%) | Phải tính mới: {miss_2} tokens")
    print(f"-> Tiết kiệm {hit_2/len(step_2_tokens)*100:.1f}% thời gian Prefill tính toán ma trận Attention!")
    print("=" * 65)


if __name__ == "__main__":
    main()
```

---

## 4. BẢNG SO SÁNH MA TRẬN KỸ THUẬT

| Kỹ Thuật | Tỷ Lệ Nén / Tiết Kiệm | Tác Động Độ Trễ TTFT | Rủi Ro Mất Mát Tri Thức |
| :--- | :--- | :--- | :--- |
| **Naive Token Truncation (Cắt đuôi)** | $30\% - 50\%$ | Không đổi | Rất cao (Mất thông tin ở cuối văn bản). |
| **LLMLingua / Perplexity Pruning** | **$40\% - 70\%$** | Giảm $50\%$ TTFT | Thấp (Bảo toàn số liệu, keyword, code syntax). |
| **GPU RadixTree Prefix Caching** | **$70\% - 90\%$** | **Giảm 80% - 90% TTFT** | Bằng $0$ (Bảo toàn toán học chính xác $100\%$). |

---

## 🔗 LIÊN KẾT HỆ THỐNG
* Nền tảng Runtime Caching: [05_agent_runtime_parameters_and_prompt_caching.md](../01-harness-and-memory/05_agent_runtime_parameters_and_prompt_caching.md) - Giải phẫu siêu tham số GPU
* Quản trị kinh tế Token: [03_token_economics_and_cost_optimization.md](03_token_economics_and_cost_optimization.md) - Mô hình định tuyến chi phí FrugalGPT
* Trở về mục lục chính: [README.md](../../README.md)
