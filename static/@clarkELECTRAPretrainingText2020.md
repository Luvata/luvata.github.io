---
title: "ELECTRA: Pre-training Text Encoders as Discriminators Rather Than Generators"
authors: "Kevin Clark, Minh-Thang Luong, Quoc V. Le, Christopher D. Manning"
year: 2020
citekey: clarkELECTRAPretrainingText2020
---

# ELECTRA: Pre-training Text Encoders as Discriminators Rather Than Generators
> **TL;DR**:  Một pretraining task, thay vì training như BERT qua MLM, ELECTRA sử dụng (1) generator để fill in `[MASK]`, kết quả tokens thu được qua (2) discriminator để binary classify which tokens are replaced by generator. Kết quả cho thấy ELECTRA pretraining task có sample efficiency cao hơn BERT, GPT (chỉ sử dụng 1 GPU V100 trong 4 ngày), ELECTRA small outperform BERT base, ELECTRA base outperform BERT Large

- [openreview](https://openreview.net/forum?id=r1xMH1BtvB)
- overview architecture:![](./static/images/Screen Shot 2021-05-15 at 12.30.02.png)
- Other config:
  - Weight-tying giữa generator và discriminator (tying token embedding + positional embedding / tying tất cả)
  - Training generator với $n$ step, sau đó initialize discriminator với weight của generator, rồi train discriminator tiếp với $n$ steps cùng với freeze weight của generator

## Highlight
- GLUE eli5 ![](./static/images/Screen Shot 2021-05-15 at 12.18.07.png)
- Which config make ELECTRA become that efficient ![](./static/images/Screen Shot 2021-05-15 at 12.36.13.png):
  - **ELECTRA 15%**: chỉ tính loss trên các token bị mask -> Kết quả thấp hơn hẳn, do vậy gain của ELECTRA là nhờ việc loss tính trên tất cả tokens
  - Replace MLM: giống BERT nhưng không dùng mask tokens mà dùng các token bị thay thế của Generator (slightly better than BERT). Trong BERT cũng có 1 task tương tự là replace 10% tokens bằng random tokens
  - All-tokens MLM: giống Replace MLM nhưng tính trên tất cả tokens, đồng thời **thêm 1 task** check xem token có copy không (giống discriminator), loss được weight giữa 2 task. Kết quả tương đối tốt
 > In total, these results suggest a large amount of ELECTRA’s improvement can be attributed to **learning from all tokens** and a smaller amount can be attributed to alleviating the pre-train fine-tune mismatch.