---
title: "CTRL: A Conditional Transformer Language Model for Controllable Generation"
authors: "Nitish Shirish Keskar, Bryan McCann, Lav R. Varshney, Caiming Xiong, Richard Socher"
year: 2019
citekey: keskarCTRLConditionalTransformer2019
---

# CTRL: A Conditional Transformer Language Model for Controllable Generation
## What
Controlling LM bằng việc dùng control code (token trước prompt) giúp việc generate đúng style và topic hơn. Đồng thời penalized sampling giúp giảm việc duplicate khi generate argmax nhưng vẫn generate được những thông tin chính xác mà model học được khi pretraining

## Why
- Việc dùng control code work vì model được train với nhiều data, và nhiều control code (vd Wiki, subreddit)
  - !()[./static/images/Screen Shot 2021-05-18 at 19.30.17.png]

- Nếu thuần sampling (Temperature top k / Nucleus sampling) với những prompt chỉ có 1 đáp án đúng (vd Thủ đô của Việt Nam là gì ?), sampling có thể trả về Hà Nội, Đà Nẵng, HCM. Còn argmax sẽ trả về HN. Vậy để sample ra truth nhưng vẫn không bị lặp lại (do argmax) thì bên cạnh dùng argmax propose là penalize nếu token bị lặp lại
## How
- Control code: Pretraining Auto-regressive Language model với token đầu tiên là control code (vd Wiki, eli5, ...). Model là GPT. Dùng vocab lớn để chứa cả control code. Control code có thể là cả url (vd Links https://..) hoặc Chủ đề (horror, movie, ...)
- Penalized decoding: Giảm probs nếu token sau trùng token trước.

## And
- Model rất lớn và có bộ vocab lớn x4 lần model thường (250k tokens).
- Penalized sampling được lưu ý là **chỉ hoạt động tốt** khi **model đã được train tương đối**