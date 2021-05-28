---
title: "The Curious Case of Neural Text Degeneration"
authors: "Ari Holtzman, Jan Buys, Li Du, Maxwell Forbes, Yejin Choi"
year: 2020
citekey: holtzmanCuriousCaseNeural2020a
---

# The Curious Case of Neural Text Degeneration
> **TL;DR**:  Vấn đề của 2 phương pháp generate text phổ biến hiện nay là Beam search (high confidence but less surprising, low diversity, even duplicate) và Pure sampling (bị overestimate rare tokens). Propose 1 cách sampling mới là nucleus (dynamic chọn K trong pure sampling sao cho tổng top K > ngưỡng P). 
- [openreview](https://openreview.net/forum?id=rygGQyrFvH)

## Highlight
- ![](./static/images/Screen\ Shot\ 2021-05-11\ at\ 00.38.25.png)
  - Dù beam search cho probability cao nhưng text bị duplicate và low surprising. Màu cam là perplexity của model đó đo trên text của human
- ![](./static/images/Screen\ Shot\ 2021-05-11\ at\ 00.54.27.png)