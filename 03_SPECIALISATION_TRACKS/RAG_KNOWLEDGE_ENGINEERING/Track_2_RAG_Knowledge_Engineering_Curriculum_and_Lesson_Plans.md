# TRACK 2: RAG & KNOWLEDGE ENGINEERING — CURRICULUM, SYLLABUS AND WEEKLY LESSON PLANS (WEEKS 5–10)
## Asabiyyah Technologies Global Applied AI Engineering Masterclass

| Field | Value |
|---|---|
| Document ID | ASB-RAG-001 |
| Version | 0.2 Draft (Stage 4 Curriculum + Stage 5 Expanded Lesson Plans) |
| Status | Draft – pending management review |
| Owner (role) | Track 2 Lead Instructor — RAG & Knowledge Engineering (TBC) |
| Last updated | 2026-11-16 |
| Parent document | [MASTER_PROGRAMME_BLUEPRINT.md](../../MASTER_PROGRAMME_BLUEPRINT.md) §12.2 |
| Related decisions | AD-01, AD-02, CD-01, CD-02, **CD-04**, PD-03, PD-04, PD-05, GD-02 |
| Stage of origin | Stage 4 (Specialisation Curriculum) and Stage 5 (Weekly Lesson Plans) |

> **Mandatory Curriculum Decision (CD-04):** This track extends strictly beyond basic vector search. It teaches document preprocessing, `BM25` lexical search, dense semantic retrieval, **Hybrid Retrieval via Reciprocal Rank Fusion (`RRF`)**, cross-encoder reranking, query transformation, metadata/ACL filtering, and grounded source attribution. Every learner must benchmark and compare retrieval approaches on a defined test dataset and submit a quantitative **Retrieval & RAG Evaluation Report** `[SRC-008, SRC-009, SRC-010, SRC-011]`.

---

## 1. Track overview and target engineering role

- **Track Focus:** Designing, indexing, securing, and quantitatively evaluating knowledge-grounded AI systems that answer domain-specific queries with verifiable citations and zero cross-tenant data leakage.
- **Target Engineering Role:** *RAG & Knowledge Systems Engineer / AI Search & Retrieval Engineer / Applied NLP Knowledge Engineer.*
- **Prerequisites:** Common Core completion (Weeks 1–4) and passing Gate 1 ($\ge 65\%$).

---

## 2. Competency framework and learning outcomes (`SC-RAG`)

| Outcome ID | Measurable Learning Outcome | Bloom Level | Mapped Competencies | Assessment Verification |
|---|---|---|---|---|
| **RAG-LO-1** | Build a deterministic document ingestion, cleaning, structure-aware chunking, and rich metadata extraction pipeline for heterogeneous PDF, Markdown, HTML, and tabular corpora. | Apply / Analyse | `CC-01`, `SC-RAG` | Week 5 Ingestion Pipeline & Chunk Quality Audit |
| **RAG-LO-2** | Implement and index both a **BM25 lexical retriever** (`rank_bm25` / SQLite `FTS5`) and a **dense semantic retriever** (`sentence-transformers` + local `Qdrant`/`Chroma`), analysing exact-keyword vs semantic failure modes (CD-04). | Apply / Analyse | `CC-04`, `SC-RAG` | Week 6 Lexical vs Dense Lab & Recall@k comparison |
| **RAG-LO-3** | Implement **Hybrid Retrieval with Reciprocal Rank Fusion (`RRF`)**, **Cross-Encoder Reranking**, and **Query Transformation** (query rewriting, decomposition, step-back prompting) (CD-04). | Apply / Create | `SC-RAG` | Week 7 Hybrid + RRF + Reranker Pipeline |
| **RAG-LO-4** | Enforce pre-retrieval **Metadata & Role-Based Access Control (ACL) Filtering**, grounded generation with strict citation verification, abstention on insufficient evidence, and **OWASP AISVS 1.0 Chapter C8** (Vector & Embedding Security) defences (CD-02, CD-04). | Analyse / Evaluate | `CC-07`, `SC-RAG` | Week 8 Secure Grounded RAG & Cross-Tenant Red-Team Test |
| **RAG-LO-5** | Construct a labelled 35+ item retrieval evaluation dataset and author a reproducible **Comparative Retrieval & RAG Evaluation Report** comparing `BM25`, `Dense`, `Hybrid (RRF)`, and `Hybrid (RRF) + Reranking` across `Recall@k`, `MRR@k`, `NDCG@k`, Faithfulness, Answer Relevance, and latency (CD-01, CD-04). | Evaluate / Create | `CC-06`, `CC-09`, `SC-RAG` | Weeks 9–10 Specialist Project & Comparative Retrieval Report (Gate 3) |

---

## 3. Tools, technical requirements, and low-cost accessibility

- **Primary CPU-Friendly Open-Source Stack:**
  - *Document Parsing:* `pypdf` / `pymupdf4llm`, `BeautifulSoup4`, custom Markdown/section-header splitter.
  - *Lexical Retrieval:* `rank-bm25` and Python's built-in `SQLite FTS5` `[SRC-008, SRC-022]`.
  - *Dense Embeddings (CPU-optimised):* `sentence-transformers` running `BAAI/bge-small-en-v1.5` (`~130 MB`, 384-dim) or `all-MiniLM-L6-v2` (`~90 MB`) `[SRC-016]`.
  - *Vector Store:* `Qdrant` (embedded local disk mode `QdrantClient(path="./qdrant_db")` — zero Docker/server overhead on 8 GB laptops) or `Chroma` `[SRC-022]`.
  - *Reranker (CPU-optimised):* Cross-Encoder `cross-encoder/ms-marco-MiniLM-L-6-v2` (`~90 MB`) `[SRC-016]`.
  - *Evaluation & Tracing:* Custom IR metric suite (`Recall@k`, `Precision@k`, `MRR@k`, `NDCG@k`) + `RAGAS` / local judge + `Arize Phoenix` OpenTelemetry tracing `[SRC-006, SRC-011, SRC-020]`.
- **Offline & Low-Bandwidth Provision:** Total embedding + reranker weights are under `250 MB` and are distributed in the Week 5 Download Manifest alongside a curated 150-document Nigerian regulatory/technical corpus (NDPA 2023, CBN guidelines, clinical/agricultural handbooks) so 100% of indexing and retrieval runs offline on an 8 GB CPU laptop.

---

## 4. Six-week workload allocation (Weeks 5–10)

Per **PD-03** (`12–15 hours/week`, `72–90 hours total`):

| Week | Title | Live Instructor-Led | Guided Labs | Independent Study | Project Dev & Assessment | Weekly Total |
|---|---|---|---|---|---|---|
| **Week 5** | Document Ingestion, Structure-Aware Chunking & Metadata Schemas | 4.0 h | 3.0 h | 2.5 h | 4.0 h | **13.5 h** |
| **Week 6** | Lexical (`BM25`) vs Dense Semantic Retrieval & Vector Databases | 4.0 h | 3.0 h | 2.5 h | 4.0 h | **13.5 h** |
| **Week 7** | Hybrid Retrieval, Reciprocal Rank Fusion (`RRF`), Reranking & Query Transformation (CD-04) | 4.0 h | 3.0 h | 2.5 h | 4.5 h | **14.0 h** |
| **Week 8** | Metadata ACL Filtering, Grounded Citations & Vector Security (AISVS C8 / CD-02) | 4.0 h | 3.0 h | 2.5 h | 4.0 h | **13.5 h** |
| **Week 9** | Retrieval & Generation Evaluation: Dataset Design & Comparative Benchmarking (CD-01, CD-04) | 4.0 h | 3.0 h | 2.5 h | 4.5 h | **14.0 h** |
| **Week 10** | Production RAG API, Caching, Failure Diagnosis & Specialist Project Delivery | 4.0 h | 3.0 h | 2.0 h | 5.0 h | **14.0 h** |
| **Total** | **Track 2 Specialisation (6 Weeks)** | **24.0 h** | **18.0 h** | **14.5 h** | **26.0 h** | **82.5 h** *(within 72–90 h)* |

---

## 5. Detailed Weekly Syllabus and Stage 5 Instructor Lesson Plans (Weeks 5–10)

### WEEK 5: Document Ingestion, Preprocessing, Structure-Aware Chunking & Metadata Engineering
- **Time:** 13.5 h (`4.0 h` Live | `3.0 h` Lab | `2.5 h` Independent | `4.0 h` Project)
- **Learning Objectives:** Parse noisy multi-format documents, implement fixed-window vs recursive vs structure/heading-aware chunking, preserve table/clause integrity, and attach deterministic provenance metadata (`doc_id`, `section_path`, `effective_date`, `access_role`, `sha256`).
- **Instructor-Led Content & Demos (4.0 h):**
  - *Session 5A (2.0 h):* **Explain** why retrieval quality is bounded by ingestion quality ("garbage in, hallucination out"). **Demonstrate** how naive character splitting breaks legal clauses and financial tables in Nigerian policy PDFs, and build a heading-aware Markdown/PDF chunker with overlap and parent-section context headers.
  - *Session 5B (2.0 h):* **Explain** metadata schema design for filtering and citation attribution. **Demonstrate** building an idempotent ingestion pipeline that hashes documents (`sha256`) to skip unchanged files and outputs validated `ChunkRecord` `Pydantic` objects.
- **Guided Practical Lab (3.0 h):** *Lab RAG-05 — Multi-Format Ingestion & Chunk Inspector:* Ingest a 40-document corpus (PDF + HTML + Markdown), compare 3 chunking strategies (`256-token fixed`, `512-token recursive`, `heading-aware structural`), and inspect boundary splits.
- **Independent Study & Project Work (6.5 h):** Select and ingest the domain corpus for the Track 2 Specialist Project.
- **Deliverable:** `GitHub PR #5` — Idempotent ingestion pipeline + chunk statistics report.
- **Common Learner Difficulties & Prep Notes:** *Issue:* Multi-column PDFs scrambling reading order. *Mitigation:* Teach layout-aware extraction (`pymupdf4llm`) and validation heuristics that flag garbled character density.

### WEEK 6: Lexical (`BM25`) vs Dense Semantic Retrieval & Vector Databases (CD-04)
- **Time:** 13.5 h (`4.0 h` Live | `3.0 h` Lab | `2.5 h` Independent | `4.0 h` Project)
- **Learning Objectives:** Explain the probabilistic BM25 scoring formula (term frequency saturation $k_1$, document length normalisation $b$) `[SRC-008]` and dense vector embeddings (cosine/dot-product similarity, HNSW indexing); implement both retrievers and demonstrate queries where each outperforms the other.
- **Instructor-Led Content & Demos (4.0 h):**
  - *Session 6A (2.0 h):* **Explain** `BM25` mechanics `[SRC-008]`. **Demonstrate** building a `BM25` index (`rank_bm25` + `SQLite FTS5`) with custom tokenisation that preserves section numbers (`Section 37(1)`), form codes, and Nigerian entity names where dense embeddings fail.
  - *Session 6B (2.0 h):* **Explain** bi-encoder embedding models and HNSW vector indexing. **Demonstrate** embedding chunks on CPU with `bge-small-en-v1.5` into local `Qdrant`, running conceptual/paraphrase queries where `BM25` returns zero hits `[SRC-016, SRC-022]`.
- **Guided Practical Lab (3.0 h):** *Lab RAG-06 — Dual Retriever Build & Failure Contrast:* Build `BM25Retriever` and `DenseVectorRetriever` over the Week 5 corpus; create 10 exact-identifier queries and 10 paraphrase queries to measure `Recall@5` on both engines.
- **Independent Study & Project Work (6.5 h):** Index the Specialist Project corpus in both `BM25` and `Qdrant` and draft the first 20 queries of the project evaluation dataset.
- **Deliverable:** `GitHub PR #6` — Working `BM25` and `Qdrant` retrievers + 20-query contrast table.
- **Common Learner Difficulties & Prep Notes:** *Issue:* Mixing asymmetric query prefixes (e.g., forgetting `Represent this sentence for searching relevant passages:` when required by specific BGE models) or comparing unnormalised vectors. *Fix:* Encapsulate embedding calls inside a single tested `EmbeddingService` class.

### WEEK 7: Hybrid Retrieval, Reciprocal Rank Fusion (`RRF`), Cross-Encoder Reranking & Query Transformation (CD-04)
- **Time:** 14.0 h (`4.0 h` Live | `3.0 h` Lab | `2.5 h` Independent | `4.5 h` Project)
- **Learning Objectives:** Implement **Reciprocal Rank Fusion (`RRF`)** from first principles `[SRC-009]`, integrate a local **Cross-Encoder Reranker**, and implement **Query Transformation** (query rewriting, multi-query expansion, sub-question decomposition) (CD-04).
- **Instructor-Led Content & Demos (4.0 h):**
  - *Session 7A (2.0 h):* **Explain** why raw BM25 scores (unbounded $[0, \infty)$) and cosine similarities ($[-1, 1]$) cannot be naively averaged, and why **Reciprocal Rank Fusion**
    $$\text{RRF\_Score}(d \in D) = \sum_{m \in M} \frac{1}{k + r_m(d)} \quad (k = 60)$$
    provides calibration-free rank combination `[SRC-009]`. **Demonstrate** coding RRF in 25 lines of Python and adding a second-stage cross-encoder (`ms-marco-MiniLM-L-6-v2`) that scores $(q, d)$ pairs jointly to boost top-3 precision (`MRR@3`).
  - *Session 7B (2.0 h):* **Explain** query transformation patterns for ambiguous, conversational, or compound user queries. **Demonstrate** conversational query contextualisation and multi-query decomposition with latency budgeting on CPU.
- **Guided Practical Lab (3.0 h):** *Lab RAG-07 — The Four-Stage Retrieval Pipeline:* Implement a configurable pipeline supporting 4 modes (`bm25`, `dense`, `hybrid_rrf`, `hybrid_rrf_rerank`) plus optional query rewriting; log per-stage latency in OpenTelemetry spans.
- **Independent Study & Project Work (7.0 h):** Integrate the 4-mode retrieval pipeline into the Specialist Project and expand the evaluation dataset to $\ge 35$ labelled query-chunk-answer triples.
- **Deliverable:** `GitHub PR #7` — Hybrid RRF + Cross-Encoder Reranker + Query Transformation module.
- **Common Learner Difficulties & Prep Notes:** *Issue:* Running the cross-encoder on 100+ candidates, causing CPU latency $>5\text{s}$. *Fix:* Retrieve top-25 from BM25 + top-25 from Dense $\rightarrow$ fuse via RRF to top-15 $\rightarrow$ rerank only top-15 down to top-5 (`<250 ms` on CPU).

### WEEK 8: Metadata ACL Filtering, Grounded Source Attribution & Vector Security (AISVS C8 / CD-02)
- **Time:** 13.5 h (`4.0 h` Live | `3.0 h` Lab | `2.5 h` Independent | `4.0 h` Project)
- **Learning Objectives:** Enforce pre-retrieval metadata and role-based access filtering (`tenant_id`, `clearance_level`, `effective_date`), structured citation generation with verbatim span verification, abstention when retrieval confidence is below threshold, and **OWASP AISVS 1.0 Chapter C8** (Memory, Embeddings & Vector Database Security) + **OWASP LLM08:2025** defences `[SRC-001, SRC-002]`.
- **Instructor-Led Content & Demos (4.0 h):**
  - *Session 8A (2.0 h):* **Explain** why post-retrieval filtering leaks existence/timing information and breaks top-$k$ recall; teach pre-retrieval metadata filter pushdown in `Qdrant` and `BM25`. **Demonstrate** grounded answer synthesis requiring inline `[doc_id:chunk_id]` citations and an automated post-check that strips uncited claims.
  - *Session 8B (2.0 h):* **Explain** **OWASP AISVS 1.0 Chapter C8** and indirect prompt injection via poisoned documents (a rogue PDF instructing the LLM to ignore rules or leak other chunks). **Demonstrate** document sanitisation, XML/structural context fencing, and cross-tenant isolation tests.
- **Guided Practical Lab (3.0 h):** *Lab RAG-08 — Access-Controlled & Citation-Verified RAG:* Add multi-role ACL filtering (`public`, `staff`, `compliance_officer`), abstention thresholds, and indirect-injection defences; verify zero unauthorized chunk leakage across 10 adversarial test queries.
- **Independent Study & Project Work (6.5 h):** Implement metadata ACL filtering, citation verification, and the AISVS C2/C5/C7/C8/C12 security checklist in the Specialist Project.
- **Deliverable:** `GitHub PR #8` — ACL-filtered grounded RAG pipeline + adversarial poison-document test suite.
- **Common Learner Difficulties & Prep Notes:** *Issue:* Model fabricating a plausible-looking `[doc_04:chunk_02]` citation that was not in the retrieved context. *Fix:* Enforce a deterministic Python validator that verifies every cited `chunk_id` exists in the retrieved top-$k$ set before returning the response.

### WEEK 9: Retrieval & Generation Evaluation: Dataset Design & Comparative Benchmarking (CD-01, CD-04)
- **Time:** 14.0 h (`4.0 h` Live | `3.0 h` Lab | `2.5 h` Independent | `4.5 h` Project)
- **Learning Objectives:** Execute the mandatory **CD-04 comparative retrieval benchmark** on a defined 35+ item evaluation dataset, computing deterministic IR metrics (`Recall@k`, `Precision@k`, `MRR@k`, `NDCG@k`), generation quality metrics (Citation Precision/Recall, Grounded Faithfulness, Answer Relevance, Abstention Accuracy), and stage-wise latency `[SRC-011]`.
- **Instructor-Led Content & Demos (4.0 h):**
  - *Session 9A (2.0 h):* **Explain** the mathematics and diagnostic meaning of `Recall@k`, Mean Reciprocal Rank (`MRR@k`), and Normalised Discounted Cumulative Gain (`NDCG@k`). **Demonstrate** running a comparative benchmark script across all 4 retrieval modes (`BM25` vs `Dense` vs `Hybrid RRF` vs `Hybrid RRF + Rerank`) and generating a reproducible Markdown comparison table.
  - *Session 9B (2.0 h):* **Explain** end-to-end RAG evaluation (`RAGAS` concepts: Context Precision, Faithfulness/Groundedness, Answer Relevance) and how to run lightweight deterministic + calibrated local judge evaluations without expensive API bills `[SRC-011, SRC-013]`. **Demonstrate** trace-based failure attribution (distinguishing *Retrieval Miss* vs *Reranker Drop* vs *Generator Hallucination*).
- **Guided Practical Lab (3.0 h):** *Lab RAG-09 — Comparative Benchmark Execution:* Run the 4-way retrieval benchmark on the project test dataset, log OpenTelemetry spans for every stage, and classify the top 5 failing queries by root cause.
- **Independent Study & Project Work (7.0 h):** Tune chunking/RRF/reranker parameters based on benchmark evidence and draft the **Comparative Retrieval & RAG Evaluation Report**.
- **Deliverable:** `GitHub PR #9` — Reproducible benchmark runner (`evals/benchmark_retrieval.py`) + raw JSON/CSV results + draft Comparative Evaluation Report.
- **Common Learner Difficulties & Prep Notes:** *Issue:* Evaluators changing chunk sizes without re-mapping ground-truth chunk IDs in the test dataset. *Fix:* Anchor ground-truth relevance labels to canonical `(doc_id, section_id / ground_truth_quote_substring)` so retrieval recall remains comparable across chunking experiments.

### WEEK 10: Production RAG Service, Caching, Failure Diagnosis & Track 2 Specialist Project Delivery
- **Time:** 14.0 h (`4.0 h` Live | `3.0 h` Lab | `2.0 h` Independent | `5.0 h` Project)
- **Learning Objectives:** Expose the hybrid RAG system via a typed `FastAPI` service with incremental index updates, query/embedding caching, Docker packaging, and complete the **Track 2 Specialist Project & Comparative Retrieval Evaluation Report** (Gate 3).
- **Instructor-Led Content & Demos (4.0 h):**
  - *Session 10A (2.0 h):* **Explain** incremental document re-indexing (handling document updates/deletions without rebuilding the entire vector store) and embedding cache optimisation. **Demonstrate** packaging the RAG API for integration with Track 1 (UI/Backend), Track 3 (MCP Knowledge Tool), and Track 4 (Local Edge RAG) in Week 11.
  - *Session 10B (2.0 h):* **Demonstrate** Track 2 project walkthroughs, oral defence questioning on `BM25`/`RRF`/reranker trade-offs, and final Gate 3 rubric checks.
- **Guided Practical Lab (3.0 h):** *Lab RAG-10 — Clean-Room Reproducibility & API Integration Test:* Verify one-command index build, API serving, and benchmark reproduction.
- **Project Deliverable (Gate 3 — Track 2 Specialist Project Package):**
  1. **Production Hybrid RAG Repository** (Ingestion pipeline, `BM25` + `Qdrant` dense + `RRF` + Cross-Encoder Reranker + Query Transformation, Metadata ACL filtering, `FastAPI` endpoint, `Dockerfile`, `pytest` suite).
  2. **Comparative Retrieval & RAG Evaluation Report (Mandatory — CD-01, CD-04)** + **AISVS 1.0 C2/C5/C7/C8/C12 Security Verification Section (CD-02)**:
     - Defined test dataset ($\ge 35$ queries covering exact keywords, paraphrases, multi-hop, unanswerable/abstention, and cross-tenant ACL probes).
     - Side-by-side quantitative comparison table (`Recall@5`, `MRR@5`, `NDCG@5`, Faithfulness, Citation Accuracy, $p_{50}/p_{95}$ latency) across **1. BM25-only**, **2. Dense-only**, **3. Hybrid + RRF**, and **4. Hybrid + RRF + Cross-Encoder Reranking**.
- **Assessment Rubric (Gate 3 — 25% of Programme Grade):**
  - *Ingestion, Structure-Aware Chunking & Metadata Engineering:* 20%
  - *Hybrid Retrieval (`BM25` + Dense + `RRF`), Reranking & Query Transformation (CD-04):* 30%
  - *Comparative Retrieval Evaluation Report & OpenTelemetry Tracing (CD-01, CD-04):* 30%
  - *Metadata ACL Security (AISVS C8 — CD-02), Citation Verification & Code Quality:* 20%

---

## 6. Curated free learning resources (Track 2)

1. **Robertson & Zaragoza (2009), *The Probabilistic Relevance Framework: BM25 and Beyond*** — https://doi.org/10.1561/1500000019 `[SRC-008]`
2. **Cormack et al. (2009), *Reciprocal Rank Fusion Outperforms Condorcet and Individual Rank Learning Methods*** `[SRC-009]`
3. **Sentence-Transformers Documentation (Embeddings & Cross-Encoder Rerankers)** — https://sbert.net/ `[SRC-016]`
4. **Qdrant Local Mode & Hybrid Search Documentation** — https://qdrant.tech/documentation/ `[SRC-022]`
5. **RAGAS Evaluation Framework Documentation** — https://docs.ragas.io/ `[SRC-011]`
6. **OWASP AISVS 1.0 Chapter C8 (Memory, Embeddings & Vector Database Security) & OWASP LLM08:2025** `[SRC-001, SRC-002]`

---

## Change log

| Version | Date | Change |
|---|---|---|
| 0.1 | 2026-11-16 | Track 2 curriculum drafted incorporating CD-04 (Stage 4). |
| 0.2 | 2026-11-16 | Integrated full Stage 5 weekly lesson plans, RRF/reranking labs, and Gate 3 rubric (GD-02b). |
