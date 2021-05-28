---
title: "Language Models are Unsupervised Multitask Learners"
authors: "Alec Radford, Jeffrey Wu, Rewon Child, David Luan, Dario Amodei, Ilya Sutskever"
year: 
citekey: radfordLanguageModelsAre
---

# Language Models are Unsupervised Multitask Learners
> **TL;DR**:  một LM đủ lớn và train với 1 dataset lớn có thể học được một số task (dịch, QA, ...) mà không cần supervised data, mô tả của task đã nằm trong context luôn

- Modeling: 
  - Modified Transformer Decoder (Layer norm, initialize scale $1/\sqrt{n}$, more layers, vocab size and context size)
  - Pretraining trên 40Gb Web text đã deduplicate bằng Bloom Filter 8-grams
  - BPE on byte sequences (dog, dog!, dog.)
    
- Đánh giá:
  - Perplexity trên held-out set
  - Đánh giá zero-shot trên các task translation, token disambiguity, last token, simple QA 

## Highlight
  - Việc nhớ data có xuất hiện, được tính bằng 8-grams overlap. Chi tiết được đề cập trong [[@carliniExtractingTrainingData2020]] ![](./images/Screen\ Shot\ 2021-05-02\ at\ 21.03.07.png)
  
  - Model size matters: Bigger -> better ![](./images/Screen\ Shot\ 2021-05-02\ at\ 21.16.14.png)