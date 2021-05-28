---
title: "Transformer-XL: Attentive Language Models Beyond a Fixed-Length Context"
authors: "Zihang Dai, Zhilin Yang, Yiming Yang, Jaime Carbonell, Quoc V. Le, Ruslan Salakhutdinov"
year: 2019
citekey: daiTransformerXLAttentiveLanguage2019
---

# Transformer-XL: Attentive Language Models Beyond a Fixed-Length Context
> **TL;DR**:  Overcome context-fragment (a.k.a fixed lenght context in vanilla Transformer decoder) by (1) cached previous hidden states and (2) introduce relative positional embedding (only take into account distance between query and key, not absolute position of which key). In training, fixed M, in testing, using context of $M*k$

- [openreview](https://openreview.net/forum?id=HJePno0cYm), surprising ICLR 2019 reject paper này
- Propose #RECL, một metrics để đo context length

## Highlight
- ![](./static/images/Screen\ Shot\ 2021-05-13\ at\ 15.35.06.png)
- ![](./static/images/Screen\ Shot\ 2021-05-14\ at\ 23.26.01.png)

---
- ![](./static/images/Screen\ Shot\ 2021-05-14\ at\ 23.10.28.png)
  - (1) Trong Vanilla Transformer, phân tách (E + U)W dot (E+U)W thành 4 thành phần:
    - (a) query embedding to key embedding
    - (b) query embedding to key position
    - (c) query position to key embedding
    - (d) query position to key position
  - $W_k E_j$ tách thành $W_{k, E} E_j$ trong (a), (c) ứng với key embedding tại $j$
  - $W_k U_j$ tách thành $W_{k, R} R_{i-j}$ trong (b), (d) ứng với key relative $i-j$
  - Thêm vector $u$ : query position tới embedding và $v$ query position tới PE
  - ![](./static/images/Screen\ Shot\ 2021-05-14\ at\ 23.24.44.png)
  - Trong ablation study B có chỉ thêm cách tính $W_{k, R} R_{i,j}$ linear time thay vì quadratic như dot product bình thường, cần đọc kỹ hơn

- Attention visualize: Lưu ý một số dòng đậm hơn ở bên đầu ![](./static/images/Screen\ Shot\ 2021-05-14\ at\ 23.46.45.png)
- Zoom in các dòng đó, thấy một số trend hợp lý (Các head đầu sẽ có attention uniform, head giữa sẽ pick các thông tin cần thiết, head cuối cũng sẽ pick các thông tin nhưng diverse hơn) ![](./static/images/Screen\ Shot\ 2021-05-14\ at\ 23.48.17.png)
- Attention visualize based on term a, b, d. Lưu ý (b) là query embed -> key position, nhìn rất giống figure 5 (đậm ở các context gần) ![](./static/images/Screen\ Shot\ 2021-05-14\ at\ 23.44.46.png)
