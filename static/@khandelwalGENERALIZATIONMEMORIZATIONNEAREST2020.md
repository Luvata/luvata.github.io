---
title: "GENERALIZATION THROUGH MEMORIZATION: NEAREST NEIGHBOR LANGUAGE MODELS"
authors: "Urvashi Khandelwal, Omer Levy, Dan Jurafsky, Luke Zettlemoyer, Mike Lewis"
year: 2019
citekey: khandelwalGENERALIZATIONMEMORIZATIONNEAREST2020
---

# GENERALIZATION THROUGH MEMORIZATION: NEAREST NEIGHBOR LANGUAGE MODELS
> **TL;DR**:  Tính similarity của context vector (phrase-representation) của test set với các context vector trên datastore, sau đó interpolate token distribution này với token distribution của LM, cách làm đơn giản này giúp cải thiện LM (giảm perplexity) trên cả in-domain và out-of-domain corpus. Thậm chí LM trained với dataset nhỏ + datastore lớn đã có thể out-perform LM train với dataset lớn. 

- [openreview discussion](https://openreview.net/forum?id=HklBjCEKvH)
- Ablation study về interpolation weight, về dùng representation nào tốt nhất (thường sau layer-norm, và tốt nhất là input của feed-forward), về datastore size ảnh hưởng đến perplexity
- Contribution
        - 1. Interpolate với n-grams không cải thiện tốt bằng LM -> Phrase representation là quan trọng. LM có khả năng học phrase-representation rất tốt và tốt với phép tương đồng
        - 2. Một LM lớn hoàn toàn có thể memorize training data tốt nhưng ko generalize tốt (perplexity trên held-out thấp), trong khi đó KNNLM vừa giúp cải thiện việc memorize vừa tăng tính generalization
## Highlight
- ![](./static/images/Screen Shot 2021-05-04 at 09.07.29.png)
