---
title: "XLNet: Generalized Autoregressive Pretraining for Language Understanding"
authors: "Zhilin Yang, Zihang Dai, Yiming Yang, Jaime Carbonell, Ruslan Salakhutdinov, Quoc V. Le"
year: 2020
citekey: yangXLNetGeneralizedAutoregressive2020
---

# XLNet: Generalized Autoregressive Pretraining for Language Understanding
> **TL;DR**: Một pretrained method cho auto-regressive LM (GPT like) nhưng có thể capture bi-directional context (như BERT) bằng cách (1) permutation LM và (2) two stream attention. Kết quả XLNet outperform BERT và RoBERTa trên nhiều NLU task. Tuy nhiên** không thấy đề cập performance của NLG task**

- Standard softmax for Permuation LM does not work: Khi predict `4->1->**3**->2` và `4->1->**2**->3`, 2 token này có chung biểu diễn (từ 4 và 1) nhưng khác target distribution -> cần làm 2 biểu diễn của 2 token này khác nhau -> biểu diễn cần **condition on current token position**
  - ![](./static/images/Screen\ Shot\ 2021-05-15\ at\ 10.50.12.png)
  - ![](./static/images/Screen\ Shot\ 2021-05-15\ at\ 10.51.53.png)
- Tuy nhiên nếu biểu diễn condition on current token -> predict this token become trivial (contradiction) -> propose two stream attention: $g$ và $h$
  - ![](./static/images/Screen\ Shot\ 2021-05-15\ at\ 11.05.40.png)
  - $g_i$ không encode $x_i$, do vậy dùng để predict $x_i$
  - $h_i$ có encode $x_i$ và dùng để predict $x_{j \neq i}$

- ![](./static/images/Screen\ Shot\ 2021-05-15\ at\ 11.09.26.png)
- ![](./static/images/Screen\ Shot\ 2021-05-15\ at\ 11.09.43.png)

## Highlight
- Vấn đề của BERT
  - (1) Independent assumption: Giả thuyết là tất cả các mask đều independ lẫn nhau (vd 2 token bị mask là `New`, `York` trong câu `New York is a city` thì loss là $P(New|is,a,city)$ và $P(York |is,a,city)$
  - (2) pretrain-finetune discrepancy: Do sử dụng artificial symbol `[MASK]` không có trong finetuning

- Trong appendix có 3 pattern Attention mới so với BERT
  - ![](./static/images/Screen\ Shot\ 2021-05-15\ at\ 11.10.43.png)

-  Training lâu và khó hơn BERT, propose method là chỉ tính loss trên một phần, không phải với tất cả token ![](./static/images/Screen\ Shot\ 2021-05-15\ at\ 11.17.29.png)

- Không thấy đề cập performance của NLG tasks