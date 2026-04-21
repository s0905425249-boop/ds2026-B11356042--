# System Architecture

## Data Source

資料來源包含：

* 課程大綱 PDF
* 系所課程介紹網頁
* 選課系統資料
* 教師授課資訊
* 歷年修課紀錄（匿名化）

---

## System Flow

課程資料（PDF / HTML）
↓
ETL 清洗與標準化
↓
Chunking（Markdown Header + Token Split）
↓
Embedding Model（BGE-M3）
↓
Vector Database（ChromaDB）
↓
Retriever（Hybrid Search）
↓
Reranker（BGE Reranker）
↓
LLM（GPT / Llama）
↓
課程推薦結果

---

## Key Design Points

### ETL

將非結構化資料（PDF、HTML）轉換為可檢索文本。

### Embedding

使用 BGE-M3 將文本轉換為向量表示。

### Vector Database

使用 ChromaDB 儲存向量資料。

### Hybrid Search

結合：

* Dense Retrieval（語意搜尋）
* Sparse Retrieval（Keyword Search）

提升課程名稱與專有名詞查詢效果。

### Reranking

使用 reranker 提升 Top-K 檢索品質。

### Hallucination Control

透過：

* Source Citation
* Confidence Score
* Low Confidence Reject

降低錯誤推薦。

