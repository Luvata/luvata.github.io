---
authors: "Guillaume Wenzek, Marie-Anne Lachaux, Alexis Conneau, Vishrav Chaudhary, Francisco Guzmán, Armand Joulin, Edouard Grave"
year: 2019
citekey: wenzekCCNetExtractingHigh2019
---

# CCNet: Extracting High Quality Monolingual Datasets from Web Crawl Data
> **TL;DR**: Propose một phương pháp tạo high quality monolingual dataset cho cả low và high resource language từ Common crawl: (1) Tải 1 dump của CC -> (2) Normalize (lower case, chuyển số thành NUM, r emove unicode punct & accent) -> (3) Deduplicate (compare hash) -> (4) LangID dùng fastText -> (5) 5-gram KenLM Kneser-Ney perplexity ranking (LM được train với target corpus là Wiki của lang đó) -> ranking thành head, mid, tail. Tổng thời gian xử lý cho 1 snapshot (48 language) là 5000 cpu hour ...

- Nhận xét:
  - Việc filter dùng perplexity tương đối đúng dù đôi khi recall thấp (do target corpus wiki quá nhỏ tuỳ ngôn ngữ), và perplexity có correlate với performance trên các downstream task
  - (dedup -> LangID) giúp giữ lại nhiều document của low-resource lang hơn so với LangID -> deduplicate
## Highlight
- ![](./static/images/2021-05-07-16-29-42.png)
- ![](./static/images/2021-05-07-16-36-25.png)
- ![](./static/images/2021-05-07-16-38-40.png)