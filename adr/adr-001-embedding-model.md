# ADR-001

## Title

Why Choose BGE-M3 as Embedding Model

---

## Context

本系統需要處理大量中文課程資料，包含：

* 課程名稱
* 教學內容
* 教師資訊
* 修課規則

因此 embedding model 必須具備：

* 中文語意理解能力
* 支援 Hybrid Search
* 成本可控
* 本地部署能力

---

## Decision

選擇：

## BGE-M3

作為主要 Embedding Model。

---

## Status

Accepted

---

## Consequences

優點：

* 中文效果佳
* 支援 dense + sparse + multi-vector
* 免費使用
* 適合教育場景

缺點：

* 本地部署需 GPU 資源
* 初期設定較 OpenAI API 複雜

