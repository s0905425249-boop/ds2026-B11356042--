ADR-002
Title
Why Choose ChromaDB as Vector Database

Context
本系統需要儲存課程 embedding 向量，並支援快速語意搜尋。

需求包括：
- 支援高維向量儲存
- 查詢延遲低
- 易於本地部署
- 開發與測試方便

Decision
選擇 ChromaDB 作為向量資料庫。

Status
Accepted

Alternatives Considered

FAISS
優點：
- 查詢速度極快
- Facebook 開源

缺點：
- 需自行管理索引與持久化
- 開發成本較高
- 不適合快速原型

Pinecone
優點：
- 雲端服務穩定
- 易於擴展

缺點：
- 需要付費
- 對課程專案來說成本過高

Weaviate
優點：
- 功能完整（支援 hybrid search）

缺點：
- 架構較重
- 設定複雜

Consequences

優點：
- 安裝簡單（pip install 即可）
- 適合原型開發與課堂專案
- 與 Python / LangChain 相容性高
- 支援持久化與 metadata

缺點：
- 不適合超大規模生產環境
- 效能略低於 FAISS

Conclusion
ChromaDB 在開發速度與易用性上最符合課程推薦系統需求，因此採用。
