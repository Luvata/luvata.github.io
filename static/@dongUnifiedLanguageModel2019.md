---
title: "Unified Language Model Pre-training for Natural Language Understanding and Generation"
authors: "Li Dong, Nan Yang, Wenhui Wang, Furu Wei, Xiaodong Liu, Yu Wang, Jianfeng Gao, Ming Zhou, Hsiao-Wuen Hon"
year: 2019
citekey: dongUnifiedLanguageModel2019
---

# Unified Language Model Pre-training for Natural Language Understanding and Generation
> **TL;DR**:  Transformer LM pretrained bằng multi-task learning, gồm Unidirectional LM (left-to-right, right-to-left), bi-directional LM (masked LM), seq2seq (concatenate 2 sequence, causal mask for target sequence) do vậy vừa có thể fine-tuning cho các task NLU (sentiment, POS tagging, QA, ...) vừa cho cả các task NLG (summarization, question generation). Model có performance NLU task ngang với BERT và đạt SOTA với các NLG task

- [neurips review](https://proceedings.neurips.cc/paper/2019/file/c20bb2d9a50d5ac1f713f8b34d9aac5a-Reviews.html)
- Lưu ý: Model này training tiếp tục từ BERT-large, trong comment có nói nếu train from scratch cho performance tương đồng nhưng lâu hơn (1), còn tiếp tục training BERT-large thì kết quả trên các task NLG vẫn không tốt bằng UniLM (2)
- (1) có thể là bold-claim vì việc training multi-task thường unstable và khó optimize, thậm chí các task có thể negative transfer lẫn nhau, và việc sử dụng pretrained BERT-large là cần thiết
- (2) Có vẻ hợp lý vì BERT nhìn chung rất mạnh trong các task NLU nhưng không tốt với NLG
- Chưa so sánh chất lượng pretrained model (không bao gồm finetuning) trên các task zero-shot NLG (vd so sánh với GPT-2, GPT-3)

## Highlight
- ![](./static/images/Screen\ Shot\ 2021-05-11\ at\ 23.40.52.png)
- ![](./static/images/Screen\ Shot\ 2021-05-11\ at\ 23.44.00.png)
  - Việc setup pretraining Seq2Seq khá mới, bằng cách khéo léo sử dụng causal mask cho target sequence