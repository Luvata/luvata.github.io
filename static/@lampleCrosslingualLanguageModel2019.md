---
title: "Cross-lingual Language Model Pretraining"
authors: "Guillaume Lample, Alexis Conneau"
year: 2019
citekey: lampleCrosslingualLanguageModel2019
---

# Cross-lingual Language Model Pretraining
> **TL;DR**:  MLM transformers unsupervised pretraining sử dụng (1) shared-vocab BPE và (2) sampling mono-lingual sentences based on corpus size giúp cải thiện performance của embedding trên nhiều task (trong đó có translation) và cải thiện perplexity của low-resource language. Thử nghiệm còn cho thấy task supervised training (Translation LM: extend từ MLM với input là concatenate của source và target sentence) còn cải thiện cross-lingual embedding hơn (SOTA trên task Translation)

- Tại sao Cross-lingual LM cho performance tốt hơn với low-resource language ? Bên cạnh việc shared vocab BPE, 2 bộ training mono-lingual còn có các **n-gram anchor span** chung nhau (vd tên người: `Tổng thống Trump` - `president Donald Trump`) qua đó có thể transfer thêm các thông tin qua các anchor của high-resource language sang low-resource language
- Tính Averaged perplexity over languages as a stopping criterion for training. 

## Highlight
- Training Cross-lingual LM gồm 2 task: MLM (70%) và Translate language model (30%) ![](./static/images/2021-05-12-16-03-18.png)
