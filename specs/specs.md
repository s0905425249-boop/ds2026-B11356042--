# Specifications

## Chunking Strategy

採用：

### Markdown Header Split

依照：

* 課程名稱
* 課程目標
* 教學內容
* 評分方式
* 先修課程

進行語義切分。

### Token Split

設定：

* Chunk Size：500 tokens
* Overlap：100 tokens

避免上下文遺失。

---

## Performance Targets

### Retrieval Latency

< 2 seconds

### Top-K Accuracy

> 85%

### Faithfulness Score

> 0.90

### Answer Relevancy

> 0.85

---

## Evaluation Framework

使用：

## RAGAS

評估：

* Faithfulness
* Answer Relevancy
* Context Precision
* Context Recall

確保回答具備：

* 正確性
* 完整性
* 可追溯性

