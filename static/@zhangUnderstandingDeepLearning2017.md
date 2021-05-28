---
title: "Understanding deep learning requires rethinking generalization"
authors: "Chiyuan Zhang, Samy Bengio, Moritz Hardt, Benjamin Recht, Oriol Vinyals"
year: 2017
citekey: zhangUnderstandingDeepLearning2017
---

# Understanding deep learning requires rethinking generalization
> **TL;DR**:  Thực nghiệm là huấn luyện mô hình trên bộ dữ liệu đã random nhãn, shuffle pixel, random pixel, các kiến trúc đều có thể đưa loss về 0. Bài này dài, tóm lại gồm 2 ý: (1) Optimization là bài toán ko khó nhưng optimization tốt chưa chắc đã thu được 1 model generalize tốt (trên một bộ data random label) . (2) Explicit Regularization không thực sự tăng generalization của model, nhưng Implicit Regularization có với data random label

- [openreview](https://openreview.net/forum?id=Sy8gdB9xx)
  - Được điểm cao trong ICLR2016 review, tuy nhiên có nhiều "gạch đá"

- Có lẽ cần đọc thêm về Rademacher complexity và các phương pháp để đo generalization bound của model

 
## Highlight
- ![](.\static\images\Screen\ Shot\ 2021-05-08\ at\ 23.47.17.png)
- ![](.\static\images\Screen\ Shot\ 2021-05-08\ at\ 23.55.04.png)
- ![](.\static\images\Screen\ Shot\ 2021-05-09\ at\ 00.07.20.png)

## Điều chưa rõ
- Gram matrix & Kernel trick
- Rademacher complexity & VC-dimension