---
title: "UniLMv2: Pseudo-Masked Language Models for Unified Language Model Pre-Training"
authors: "Hangbo Bao, Li Dong, Furu Wei, Wenhui Wang, Nan Yang, Xiaodong Liu, Yu Wang, Songhao Piao, Jianfeng Gao, Ming Zhou, Hsiao-Wuen Hon"
year: 2020
citekey: baoUniLMv2PseudoMaskedLanguage2020
---

# UniLMv2: Pseudo-Masked Language Models for Unified Language Model Pre-Training
> **TL;DR**: Pretraining LM theo multi-task learning: (1) Auto-Encoder (MLM như BERT) và Partial Auto-regressive (span auto-regressive) và sử dụng masking + positional encoding hợp lý để **embedding của 2 task chỉ tính trong 1 lần forward**. Kết quả cho SOTA trên cả NLU và NLG. Ablation study cho thấy PAR objective comparable với AE / AR, khi kết hợp cùng AE cải thiện performance.

- [slide ICML 2020](https://icml.cc/media/Slides/icml/2020/virtual(no-parent)-16-15-00UTC-6417-unilmv2_pseudo.pdf)
- [slideslive](https://slideslive.com/38928147)

- Modeling overview: !()[.\static\images\Screen Shot 2021-05-12 at 11.03.52.png]

- (1) Với task MLM, thực hiện training auto-encoder như BERT, lưu ý token $M$ sẽ không attention với các token gốc ($x_2$, $x_4$, $x_5$), nhưng có attention với tất cả token M khác ($M_2$, $M_4$, $M_5$) !()[.\static\images\Screen Shot 2021-05-12 at 13.29.58.png]
- (2) Với task PAR, các span cần predict sẽ được mask từ trái sang phải (ở đây là span <2> -> <4, 5>). Token $P2$ thuộc span đầu tiên của task PAR, không có connection với $x_2$, $x_4$, $x_5$ !()[.\static\images\Screen Shot 2021-05-12 at 13.30.22.png] 
- (3) Token $P_4$, $P_5$ ở span thứ hai (sau span của của token $P_2$), nên attention được tính thêm với tất cả token của span trước (span của token 2 là $x_2$, connection màu đỏ) !()[.\static\images\Screen Shot 2021-05-12 at 13.30.40.png]

--- 
- Nếu train PAR <4, 5> -> <2> thì masking sẽ ngược lại: ($P2$ **có** attent với $x_4$, $x_5$; $P_4$, $P_5$ **không** attent với $x_2$ ) !()[.\static\images\Screen Shot 2021-05-12 at 11.39.18.png]
  - Và masking sẽ như sau !()[.\static\images\Screen Shot 2021-05-12 at 11.39.28.png]

## Highlight
- Thuật toán tạo span mask !()[.\static\images\Screen Shot 2021-05-12 at 11.17.59.png]
  - 40% mask span n-gram (n từ 2-6)
  - 60% mask 1 token
  - Dừng lại khi tổng số token bị mask >= 15%

