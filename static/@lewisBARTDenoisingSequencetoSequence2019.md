---
title: "BART: Denoising Sequence-to-Sequence Pre-training for Natural Language Generation, Translation, and Comprehension"
authors: "Mike Lewis, Yinhan Liu, Naman Goyal, Marjan Ghazvininejad, Abdelrahman Mohamed, Omer Levy, Ves Stoyanov, Luke Zettlemoyer"
year: 2019
citekey: lewisBARTDenoisingSequencetoSequence2019
---

# BART: Denoising Sequence-to-Sequence Pre-training for Natural Language Generation, Translation, and Comprehension
> **TL;DR**:  **B**idirectional and **A**uto-**R**egressive **T**ransformers: Pretrained denoising **encoder-decoder Transformer**, với 1 task mới (text span infilling) và cách finetuning mới cho task Translation (stack 1 noising encoder mới trước BART encoder). Ablation study cho thấy pretraining task span filling cho performance tốt trên nhiều task với BART, và stack encoder outperform strong baseline cho bài toán dịch. Finally 1 model pretrain với 2 task (span infilling + sentence permutation) cho kết quả NLU ngang với RoBERTa và SOTA trên các task NLG (summarization)

- BART với encoder rỗng có thể coi như 1 language model -> Chưa có so sánh về zero-shot LM như GPT (khả năng cao sẽ kém hơn GPT giống như task Eli5)
- Với task NMT, BART (pretrained target language) chỉ cần 1 random Encoder trên source language để học cách biến source language thành noisy input của target languge, sau đó BART thực hiện denoising để ra target sentence (wow)
- Nhận xét: Một kiến trúc khá toàn diện, future work có thể so sánh từng pretraining task hoặc propose một pretraining task mới, so sánh ảnh hưởng như thế nào đến từng downstream task
- BART khác gì UniLM ? UniLM là 1 Transformer decoder sử dụng mask khéo léo, còn BART là encoder-decoder Transformer. BART's decoder luôn được train với clean text
- BART khác gì T5 ? Nhìn chung khá giống nhau :D

## Highlight
- Overview of architecture: ![](./static/images/2021-05-12-15-09-56.png)
- Pretraining tasks: ![](./static/images/2021-05-12-15-14-13.png)
- Finetuning seq2seq ![](./static/images/2021-05-12-15-22-56.png)