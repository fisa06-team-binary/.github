# 🔍 AI 기반 하이브리드 검색 및 RAG 파이프라인 최적화 랩
<img width="1920" height="1080" alt="서지혜 (2)" src="https://github.com/user-attachments/assets/7fbea90c-6398-4de2-a4c8-5079f4d4d35e" />

<div align="center">
  <p><strong>"정확하지만 좁은 BM25, 넓지만 느슨한 Vector Search. 이 둘을 어떻게 안정적으로 통합할 것인가?"</strong></p>
  <p>단순한 텍스트 매칭(Lexical)이나 문맥 검색(Semantic) 단일 구조의 한계를 극복하기 위해,<br><strong>'데이터 필터링 - 하이브리드 검색 - LLM 검증'</strong>으로 이어지는 아키텍처를 설계하고 성능을 최적화한 프로젝트 시리즈입니다.</p>
</div>

<br>

## 📂 Repositories (프로젝트 바로가기)
각 Phase별 상세한 엔지니어링 과정과 트러블슈팅은 아래 레포지토리에서 확인하실 수 있습니다.

| Phase | Project | Core Engineering | Link |
| :---: | :--- | :--- | :--- |
| **Phase 1** | **오답률 0% 하이브리드 RAG 파이프라인** | `ChromaDB`, `Metadata Filtering`, `LLM Re-ranking` | [➡️ Phase 1 Repository](https://github.com/fisa06-team-binary/RAG-Search-Architecture-test) |
| **Phase 2** | **금융 고객 타겟팅 (RRF 하이브리드 검색)** | `SQL Hard Filter`, `BM25`, `Dense Vector`, `RRF 융합` | [➡️ Phase 2 Repository](https://github.com/fisa06-team-binary/Hybrid-Search-RRF-Lab) |
| **Phase 3** | **주식 종목 AI 탐색기 (Elasticsearch)** | `Elasticsearch 8.x`, `Query Expansion(LLM)` | [➡️ Phase 3 Repository](https://github.com/fisa06-team-binary/stock-rag-platform) |

<br>

## ⚡ Key Performance & Impact

### 1. 연산 효율성 극대화 및 Latency 최적화
* **Problem**: 전체 데이터를 대상으로 하이브리드/AI 연산 수행 시 시스템 병목 발생
* **Solution**: 검색 엔진 앞단에 SQL 하드 필터링 배치
* **Impact**: 초기 모수 10,000건 중 **94.4%의 불필요한 연산을 0.00ms 단위로 차단**, 총 응답 시간을 **16.69ms에서 4.93ms로 단축 (약 3.3배 향상)**

### 2. 점수 편향 오류 해결 및 검색 품질 검증
* **Problem**: 스케일이 다른 BM25와 Vector 엔진을 단순 가중합(Score Fusion)할 경우 발생하는 순위 왜곡 및 운영 불안정성
* **Solution**: 점수 스케일에 독립적인 **순위 기반 융합(RRF, Reciprocal Rank Fusion)** 도입
* **Impact**: '외식 소비가 많은 고객' 시나리오에서 엔진 간 편향을 차단하고 실제 VIP 고과금 유저 추출 성공. 정답 검출률(**Recall@10**) 기존 대비 **약 7배 향상**

### 3. 오답률 0%의 타겟팅 신뢰도 확보
* **Impact**: Phase 2의 3-Step 하이브리드 RAG 구조를 통해 4가지 마케팅 페르소나 추출 테스트에서 **정밀도(Precision) 100.0%** 달성

<br>

## 🛠️ Tech Stack

* **Language**: ![Python](https://img.shields.io/badge/Python-3.11%2B-3776AB?style=flat&logo=python&logoColor=white)
* **Search & Vector DB**: ![Elasticsearch](https://img.shields.io/badge/Elasticsearch-005571?style=flat&logo=elasticsearch&logoColor=white) ![ChromaDB](https://img.shields.io/badge/ChromaDB-FF6F00?style=flat&logo=chroma&logoColor=white)
* **AI & NLP**: ![OpenAI](https://img.shields.io/badge/OpenAI_API-412991?style=flat&logo=openai&logoColor=white) ![SentenceTransformers](https://img.shields.io/badge/SentenceTransformers-F9AB00?style=flat&logo=huggingface&logoColor=white)
* **Algorithm**: `BM25`, `RRF (Reciprocal Rank Fusion)`

---
<div align="center">
  <i>"정렬(Ranking)도 결국 구조적인 데이터 파이프라인의 결과물이다"</i>
</div>
