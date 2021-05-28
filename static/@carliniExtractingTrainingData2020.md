---
title: "Extracting Training Data from Large Language Models"
authors: "Nicholas Carlini, Florian Tramer, Eric Wallace, Matthew Jagielski, Ariel Herbert-Voss, Katherine Lee, Adam Roberts, Tom Brown, Dawn Song, Ulfar Erlingsson, Alina Oprea, Colin Raffel"
year: 2020
citekey: carliniExtractingTrainingData2020
---

# Extracting Training Data from Large Language Models
> **TL;DR**: Một paper extensively research on memorization and training data extraction trong language model, case-study là GPT-2, với việc ghi nhớ các thông tin nhạy cảm. Cách thực hiện là sampling từ LM, sau đó filter các content không thể nằm trong training data, và soát tay các kết quả còn lại. Qua đó thấy được nhiều vấn đề LM còn mắc phải

 - Cách extract: 3 sampling method: init với `BOS`, decay temperature, prompt từ internet
 - Cách tìm ra văn bản bị memorization: Dựa vào perplexity thấp, zlib, và correlation cao với smaller LM (small và large đều có ppl thấp, sẽ loại các docs có small ppl cao, large ppl thấp, tương tự với lowercase)
 - Một cách filter nữa là nhìn từ tokenizer (vd `goodness` bị tách thành `goo d ness` vì trong training sẽ luôn chọn token có length lớn nhất)
  - Nhìn chung việc **memorization** trong LM khi **đoạn văn bản xuất hiện nhiều lần trong training set** (do de-duplicate mức document nên bị sót)
  - **Prompt ảnh hưởng lớn đến khả năng nhớ của LM (vd về PI)**
  - GPT-2 đôi khi cũng **generate ra những văn bản sai sự thật** (refer đến 1 celebrity, đúng một phần sau đó là make-up content)
## Highlight
![](./images/Screen\ Shot\ 2021-05-03\ at\ 16.01.54.png)
![](./images/Screen\ Shot\ 2021-05-03\ at\ 16.06.33.png)
![](./images/Screen\ Shot\ 2021-05-03\ at\ 16.12.25.png)