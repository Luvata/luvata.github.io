---
title: "Improving Language Understanding by Generative Pre-Training"
authors: "Alec Radford, Karthik Narasimhan, Tim Salimans, Ilya Sutskever"
year: 
citekey: radfordImprovingLanguageUnderstanding
---

# Improving Language Understanding by Generative Pre-Training
> **TL;DR**:  Pretrain LM (transformer) có thể cải thiện performance trên downstream task, pretraining transformer tốt hơn LSTM 

- Modeling:
  - Transformer Decoder
  - BPE
  - pretraining trên 6gb Book corpus -> Long range dependency
  - Joint training bằng loss của LM (weight 0.5) và loss của task (weight 0.5)

- Nhận xét
    - Tăng số layer sử dụng khi finetuning -> Tăng performance
    - Relative task **zero-shot performance đều tăng khi tăng số pretraining step**, đồng thời Transformer (đường liền) cho kết quả tốt hơn LSTM pretraining (nét đứt) chứng tỏ kiến trúc Transformer có khả năng học tốt hơn ?


## Highlight
- Cách setup các task ![](static/images/Screen Shot 2021-05-01 at 19.33.20.png)
- Nhận xét về số layer khi finetuning và gain từ finetuning ![](static/images/Screen Shot 2021-05-01 at 19.44.31.png)