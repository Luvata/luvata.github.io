---
title: "SpanBERT: Improving Pre-training by Representing and Predicting Spans"
authors: "Mandar Joshi, Danqi Chen, Yinhan Liu, Daniel S. Weld, Luke Zettlemoyer, Omer Levy"
year: 2020
citekey: joshiSpanBERTImprovingPretraining2020
---

# SpanBERT: Improving Pre-training by Representing and Predicting Spans
> **TL;DR**: Thay vì mask 1 token như BERT, SpanBERT **mask 1 span token** và tính loss trên từng token (MLM + SBO). SBO là cách predict 1 token bị mask trong span bằng 1 mạng feedforward từ 2 token start, end của span (Hình dưới). Kết quả cho thấy performance trên các task đều cải thiện so với BERT và các task dùng span text (vd SQuAD, Coref) significant improve. Ablation study cũng chỉ ra rằng NSP loss hurt performance on downstream task, while SBO don't.
- Overview của model: Loss trên 1 token bị mask được tính bằng MLM và SBO, với SBO nhận đầu vào là 3 vector: embedding start span, embedding end span, positional embedding của token bị mask trong span (vị trí thứ 3) ![](static/images/Screen Shot 2021-05-13 at 14.52.33.png)
- Bài này là prior work cho [[@lewisBARTDenoisingSequencetoSequence2019]], điểm khác là 1 span length N sẽ thay bằng N token mask, trong khi BART chỉ là 1 token, sau đó được encode và prediction (hay denoising) dùngback decoder

## Highlight
- Phân phối của span lenght ![](static/images/Screen Shot 2021-05-13 at 14.54.01.png)
- Cách forward của SBO: ![](static/images/Screen Shot 2021-05-13 at 14.57.24.png)
- ![](static/images/Screen Shot 2021-05-13 at 15.04.20.png)
