# Course Recommendation RAG System Whitepaper

## 1. Overview

本專案旨在建立一個基於 Retrieval-Augmented Generation（RAG）的課程推薦系統，
讓使用者可以透過自然語言查詢課程，例如：

- 「適合初學者的 Python 課程」
- 「不考試、偏實作的選修課」
- 「資工系推薦必修課」

系統會從課程資料中檢索相關內容，並結合大型語言模型生成推薦結果。

---

## 2. Problem Statement

傳統課程查詢方式存在以下問題：

- 課程資訊分散（PDF / 網頁 / 系統）
- 關鍵字搜尋效果有限
- 無法理解語意需求（例如「涼課」、「甜課」）
- 無法跨課程比較

因此需要一個能理解語意並進行智能推薦的系統。

---

## 3. System Overview (RAG Pipeline)

系統架構如下：

Course Data (PDF / HTML / DB)
↓
ETL Processing (Cleaning & Normalization)
↓
Chunking (Markdown Header + Token Split)
↓
Embedding (BGE-M3)
↓
Vector Database (ChromaDB)
↓
Hybrid Retrieval (Dense + Keyword Search)
↓
Reranker (BGE Reranker)
↓
LLM Generation (GPT / Llama)
↓
Course Recommendation Output

---

## 4. Key Technologies

### 4.1 Embedding Model: BGE-M3
Used for encoding course descriptions into vector representations.

Advantages:
- Strong multilingual capability (especially Chinese)
- Supports dense + sparse + multi-vector representations
- Suitable for semantic search tasks

---

### 4.2 Vector Database: ChromaDB
Stores embeddings and enables similarity search.

Advantages:
- Lightweight and easy to deploy
- Fast development cycle
- Good integration with Python ecosystem

---

### 4.3 Retrieval Strategy: Hybrid Search

Combines:
- Dense Retrieval (semantic similarity)
- Sparse Retrieval (keyword matching)

This improves performance for:
- Course names
- Technical terms
- Abbreviations

---

### 4.4 Reranking

Top-K retrieved results are re-ranked using BGE Reranker to improve relevance ordering.

---

## 5. Data Processing (ETL)

Raw data sources include:
- Course syllabi (PDF)
- Department websites
- Course database exports

Processing steps:
1. Text extraction
2. Cleaning (remove noise, headers, duplicates)
3. Normalization
4. Chunking (semantic + token-based)

---

## 6. Chunking Strategy

Two-layer approach:

### Markdown Header Split
Splits by:
- Course name
- Objectives
- Content
- Grading
- Prerequisites

### Token-based Split
- Chunk size: 500 tokens
- Overlap: 100 tokens

This ensures context completeness.

---

## 7. Hallucination Control

To reduce incorrect AI-generated answers:

- Source grounding (retrieved context required)
- Confidence scoring
- Low-confidence rejection strategy

---

## 8. Evaluation Metrics

We use RAGAS framework:

- Faithfulness (是否忠於資料)
- Answer Relevancy（回答是否相關）
- Context Precision（檢索準確度）
- Context Recall（是否找齊資訊）

Target performance:
- Faithfulness ≥ 0.90
- Answer Relevancy ≥ 0.85

---

## 9. Conclusion

This system demonstrates how RAG can be applied to educational course recommendation,
combining semantic retrieval, hybrid search, and LLM generation.

It improves:
- Search relevance
- User experience
- Course discoverability
