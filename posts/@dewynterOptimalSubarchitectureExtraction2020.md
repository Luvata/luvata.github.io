---
authors: "Adrian Wynter, Daniel J. Perry"
year: 2020
citekey: dewynterOptimalSubarchitectureExtraction2020
unlisted: true 
---

# Optimal Subarchitecture Extraction For BERT
> **TL;DR**:  BORT: Một phương pháp compress BERT sử dụng NAS để tìm configure (Depth, Attention head, Hidden size, Intermediate layer size) tối ưu cho tốc độ inference, độ chính xác & model size. Sau đó thử nghiệm pretraining với 2 setting: MLM và Distillation cho thấy performance competitive nhưng tốc độ học nhanh hơn BERT và RoBERTa Large

- Concept chưa hiểu:
  - #ABnC-property
  - #L-Lipschitz-smoothness
  - #FPTAS-solver
## Highlight
![](./static/images/2021-05-13-14-16-35.png)
