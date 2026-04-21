# Course Advisor RAG System

## 大學課程智慧推薦系統

本專案設計一套以 RAG（Retrieval-Augmented Generation）為核心的智慧課程推薦系統，協助學生依據自身需求、興趣與能力進行修課規劃。

系統可根據學生輸入：

* 科系背景
* 興趣方向（AI、資料分析、程式設計等）
* 能力狀況（數學能力、程式基礎）
* 修課目標（畢業、考研、就業）

進行課程推薦，並提供：

* 推薦課程
* 修課順序
* 先修課程分析
* 課程難度說明
* 教師資訊
* 推薦理由

本系統透過：

* ETL 資料清洗
* Embedding 向量化
* Vector Database 儲存
* Hybrid Search 檢索
* Reranking 精排
* LLM 回答生成

提升回答的準確性、可解釋性與可信度，降低傳統 LLM 的 hallucination（幻覺）問題。

