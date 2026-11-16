# GLOBAL RESEARCH AND CURRICULUM BENCHMARKING REPORT
## Asabiyyah Technologies Global Applied AI Engineering Masterclass

| Field | Value |
|---|---|
| Document ID | ASB-RES-001 |
| Version | 0.1 Draft |
| Status | Draft – pending management review |
| Owner (role) | Curriculum Research Lead (TBC) |
| Last updated | 2026-11-16 |
| Parent document | [DECISION_REGISTER.md](../DECISION_REGISTER.md) |
| Related decisions | AD-01–03, CD-01–05, PD-03–05 |
| Stage of origin | Stage 1 |

> **Governance note:** All recommendations in this report are evidence-based proposals. None take effect until approved in [DECISION_REGISTER.md](../DECISION_REGISTER.md). All source citations (`[SRC-nnn]`) resolve to [Source_Register.md](Source_Register.md).

---

## 1. Executive summary

The global AI engineering market has shifted decisively from isolated prompt crafting and notebook prototypes toward **production software systems engineering**. Employers and technical standards bodies now expect AI engineers to build provider-independent backends, enforce strict schema validation, ground generation in hybrid retrieval pipelines, orchestrate bounded tool-calling agents via standard protocols, instrument applications with open telemetry, and verify security controls against formal frameworks `[SRC-001, SRC-005, SRC-006, SRC-018]`.

Benchmarking the **Asabiyyah Technologies Global Applied AI Engineering Masterclass** against global offerings from DeepLearning.AI, Hugging Face, Stanford, Linux Foundation, and cloud hyperscalers `[SRC-016, SRC-017, SRC-023, SRC-024]` confirms two strategic advantages:
1. **Systems integration over fragmented micro-courses:** While leading platforms offer strong 1–10 hour courses on single topics, very few integrate software engineering, evaluation, security verification, and offline-capable edge execution into a unified product-engineering lifecycle.
2. **Constraint-resilient engineering:** Global curricula routinely assume high-bandwidth fiber internet, paid commercial API keys, and dedicated Apple Silicon or NVIDIA GPUs. Designing explicitly for Nigerian and resource-constrained environments—using CPU-compatible quantised open-weight models (`GGUF` via `llama.cpp` / Ollama), local SQLite/Qdrant stores, and provider abstraction—teaches stronger systems discipline than cloud-dependent courses `[SRC-014, SRC-015, SRC-022]`.

**Key findings on the 14-week baseline (AD-01, PD-03):**
At 12–15 hours per week (168–210 total hours), the 14-week architecture is **achievable but tightly constrained**. It succeeds only if:
- The optional 2-week preparatory pathway (PD-04) is strongly recommended via a pre-entry diagnostic so Week 1 does not stall on elementary Python syntax or Git setup.
- Capstone product integration begins in **Week 11** (Integration & Product Engineering), with evaluation datasets (CD-01) and threat models (CD-02) built incrementally from Week 5 rather than compressed into Weeks 13–14.
- Framework proliferation is strictly prevented: each track teaches core concepts in raw Python first, followed by **at most one** primary orchestration or serving abstraction.

---

## 2. Current global AI engineering competency map

Industry role definitions across 2025–2026 distinguish **Applied AI Systems Engineers** from traditional Machine Learning Scientists. Whereas ML Scientists train or fine-tune foundation weights, Applied AI Engineers design, integrate, evaluate, secure, and operate applications built around pre-trained foundation and open-weight models.

| Competency Domain | Core Engineering Capabilities Expected in Industry | Maturity Classification |
|---|---|---|
| **1. Software & API Engineering** | Typed Python (3.11+), asynchronous I/O (`asyncio`), REST/streaming APIs (`FastAPI`, SSE), strict data validation (`Pydantic v2`), Git workflows, containerisation (`Docker`), automated testing (`pytest`) `[SRC-018]`. | **Established practice** |
| **2. Provider-Independent Model Integration** | Unified message schemas, structured JSON/schema enforcement, tool/function calling, retry/backoff, context-window budgeting, fallback routing between local and hosted APIs `[SRC-015, SRC-018]`. | **Established practice** |
| **3. RAG & Knowledge Engineering (CD-04)** | Document parsing, structure-aware chunking, lexical search (`BM25`), dense embeddings, hybrid retrieval via Reciprocal Rank Fusion (`RRF`), cross-encoder reranking, metadata access filtering, citation enforcement `[SRC-008, SRC-009, SRC-010, SRC-022]`. | **Established practice** |
| **4. Agentic AI & Interoperability (CD-03)** | Explicit reasoning/execution loops (`ReAct`), deterministic state graphs, bounded step budgets, human-in-the-loop approval gates, Model Context Protocol (`MCP`) client/server implementation `[SRC-005, SRC-012, SRC-019]`. | **Established / Emerging standard** |
| **5. Evaluation & Observability (CD-01)** | Golden dataset curation, deterministic assertions, reference-free/grounded RAG metrics (`RAGAS`), calibrated LLM-as-a-judge, OpenTelemetry GenAI tracing (`gen_ai.*`), latency/cost budgets `[SRC-006, SRC-011, SRC-013, SRC-020, SRC-021]`. | **Established practice** |
| **6. AI Security, Privacy & Governance (CD-02)** | Threat modelling, OWASP LLM Top 10 (2025) defences, OWASP AISVS 1.0 verification controls, least-privilege tool sandboxing, PII redaction, NDPA 2023 compliance (s.24, s.28 DPIA, s.37 automated decisions) `[SRC-001, SRC-002, SRC-003, SRC-004, SRC-007]`. | **Established / Emerging standard** |
| **7. Edge, Quantisation & Offline AI (CD-05)** | Open-weight model selection (0.5B–8B), `GGUF` k-quants (`Q4_K_M`, `Q8_0`), KV-cache memory budgeting, CPU/hybrid serving (`llama.cpp`, `Ollama`), offline-first sync queues, reproducible hardware benchmarking `[SRC-014, SRC-015]`. | **Established practice** |

---

## 3. Benchmark of relevant global programmes and courses

| Provider & Programme | Format & Duration | Primary Strengths | Gaps Relative to Asabiyyah Mission |
|---|---|---|---|
| **DeepLearning.AI** Short Courses & Specialisations `[SRC-017]` | Self-paced micro-courses (1–4 h each) and specialisations (15–30 h) | Direct instruction from framework creators; strong coverage of RAG evaluation, agent patterns, and prompt safety. | Fragmented; relies heavily on hosted commercial APIs (OpenAI) and ephemeral cloud notebooks; lacks unified software architecture, AISVS security verification, and offline constraints. |
| **Hugging Face** Learn (`LLM Course`, `Agents Course`, `MCP Course`) `[SRC-016]` | Free, open-source self-paced units (15–40 h per course) | Strong open-weight focus; dedicated units on `smolagents`, `LangGraph`, and an official Anthropic-partnered MCP Course. | Self-paced without live mentorship, team product integration, or Nigerian regulatory/infrastructure adaptations. Excellent free supplementary reading. |
| **Stanford Online** (`CS224N`, `CS324`) `[SRC-023]` | University quarter courses (10 weeks, 100+ h) | Rigorous mathematical foundations, transformer internals, scaling laws, and empirical research methodology. | Academic ML focus; requires calculus/linear algebra depth not matched to an applied systems baseline; minimal coverage of FastAPI, MCP, or edge product engineering. |
| **Microsoft Learn / AWS / Google Cloud** GenAI Tracks `[SRC-024]` | Vendor-specific modules & certifications | Strong enterprise architecture patterns, IAM, and deployment pipelines. | High vendor lock-in (Azure AI Foundry, Bedrock, Vertex AI); requires paid cloud credits or credit-card verification unavailable to many Nigerian learners. |
| **OWASP & NIST** Reference Publications `[SRC-001, SRC-002, SRC-003, SRC-004]` | Standards & verification frameworks | Authoritative security controls (AISVS 1.0) and risk taxonomies (AI RMF / AI 600-1). | Pure reference standards, not instructional curricula; require translation into teachable checklists and lab exercises. |

---

## 4. Technical developments and curriculum relevance

To protect learners from hype and tutorial churn (Principle 9), technologies are filtered by engineering maturity and instructional value:

| Technology / Trend | Classification | Curriculum Decision & Rationale |
|---|---|---|
| **OWASP AISVS 1.0** (Released June 2026; 12 chapters C1–C12 + 3 appendices) `[SRC-001]` | **Established standard** | **Adopt (CD-02).** Provides testable verification controls across input validation (C2), access control (C5), RAG/vector stores (C8), agent orchestration (C9), MCP security (C10), and logging (C12). Must be applied *proportionately* to capstone architecture. |
| **Model Context Protocol (MCP)** (`2025-03-26` Streamable HTTP / OAuth 2.1 through `2026-07-28` stateless architecture & `server/discover`) `[SRC-005]` | **Established / rapidly evolving standard** | **Adopt (CD-03).** Teach the stable core primitives (`Tools`, `Resources`, `Prompts`, JSON-RPC message lifecycle, stdio and HTTP transports) and explicitly cover the 2025–2026 evolution from stateful session handshakes to stateless per-request metadata and OAuth 2.1 resource-server permissions. |
| **OpenTelemetry GenAI Semantic Conventions** (`open-telemetry/semantic-conventions-genai`, spun out June 2026) `[SRC-006]` | **Emerging but credible** (Status: *Development*) | **Adopt with abstraction (CD-01).** Teach vendor-neutral span attributes (`gen_ai.provider.name`, `gen_ai.operation.name`, `gen_ai.usage.input_tokens`, `gen_ai.usage.output_tokens`) and opt-in privacy rules, while warning learners that attribute names remain in *Development* status. |
| **Hybrid Retrieval (`BM25` + Dense Embeddings + `RRF` + Cross-Encoder Reranking)** `[SRC-008, SRC-009, SRC-016]` | **Established practice** | **Adopt (CD-04).** Pure vector search fails on exact identifiers, Nigerian legal/medical codes, and product SKUs. Hybrid retrieval with RRF ($k=60$) and compact local rerankers (`ms-marco-MiniLM-L-6-v2`) runs efficiently on CPU. |
| **`GGUF` Quantisation & `llama.cpp` / `Ollama` Local Serving** `[SRC-014, SRC-015]` | **Established practice** | **Adopt (CD-05).** Industry standard for local CPU/hybrid inference. Enables 1.5B–3B models on 8 GB RAM laptops and 7B–8B models on 16 GB RAM laptops at zero API cost. |
| **Autonomous Multi-Agent Swarms (3+ unconstrained conversing agents)** | **Experimental / Marketing hype** | **Restrict.** Unconstrained multi-agent chatter multiplies latency, token consumption (LLM10), and compounding hallucinations. Teach deterministic single-agent loops and supervisor-worker handoffs (at most 2 roles) only where justified. |
| **Heavyweight End-to-End LLM Frameworks hiding prompts/HTTP** | **High maintenance burden** | **Avoid in foundations.** Teach raw HTTP/SDK calls and Pydantic validation first (Principle 8) before introducing targeted libraries (`LangGraph` for state graphs, `MCP Python SDK` for protocol integration). |

---

## 5. Common Core gap analysis (Weeks 1–4)

The Common Core has **48–60 total learner hours** (PD-03) to prepare learners for any of the four tracks.

| Area | Potential Gap / Risk | Required Curriculum Action |
|---|---|---|
| **Entry Baseline Variance** | Learners with weak Python or Git fluency will stall in Week 1 when encountering virtual environments, typing, and JSON APIs. | **R-01 (High):** Publish a self-paced **2-week Preparatory Pathway (10–15 h)** and a mandatory **Pre-Cohort Diagnostic** covering Python functions/dicts, CLI, Git basics, and HTTP JSON requests (PD-04, OQ-04). |
| **Software Engineering Rigor** | Many AI courses skip project packaging, typing, and `pytest`, leading to fragile notebook code that cannot be integrated in Week 11. | Dedicate Week 1 to clean Python packaging, `Pydantic v2` models, `FastAPI` basics, `pytest`, and Git PR workflows `[SRC-018]`. |
| **Provider Abstraction** | Hardcoding a single vendor SDK breaks when free-tier rate limits hit or internet drops. | Introduce a thin **Model Provider Adapter pattern** in Week 2 that switches via configuration between local `Ollama` (`qwen2.5:1.5b` / `llama3.2:3b`) and free-tier hosted OpenAI-compatible endpoints `[SRC-015]`. |
| **Foundational Eval & Security** | Waiting until Week 13 to introduce CD-01 and CD-02 guarantees superficial capstone compliance. | Embed a **Golden Evaluation Dataset (15+ test cases)**, basic latency/token logging, and an **OWASP LLM Top 10 (2025) / AISVS C2 & C7 input-output checklist** directly into the Week 4 Common Core mini-application `[SRC-001, SRC-002]`. |

---

## 6. Track-by-track gap analysis (Weeks 5–10)

### 6.1 Track 1: AI Application Engineering
- **Core focus:** Production-grade backend and full-stack AI service engineering.
- **Identified gaps to prevent:** Treating the track as "basic prompt wrappers." It must require asynchronous streaming (`SSE`), strict structured output validation (`Pydantic`), resilient retry/circuit-breaker patterns, semantic/exact caching (SQLite/Redis), role-based authentication, cost/token rate limiting (mitigating OWASP LLM10:2025 Unbounded Consumption), and regression evaluation in CI `[SRC-002, SRC-018, SRC-021]`.
- **CD-01 & CD-02 alignment:** Continuous trace inspection (latency percentiles $p_{50}, p_{95}$, token cost, schema failure rate) and AISVS Chapters C2 (Input Validation), C4 (Deployment), C5 (Access Control), C7 (Output Control), and C12 (Logging) `[SRC-001]`.

### 6.2 Track 2: RAG & Knowledge Engineering (Incorporating CD-04)
- **Core focus:** Verifiable, access-controlled knowledge grounding over messy real-world corpora.
- **Implementation of CD-04:**
  1. **Lexical baseline:** `BM25` (`rank_bm25` or SQLite `FTS5`) `[SRC-008, SRC-022]`.
  2. **Semantic retrieval:** CPU-friendly dense embeddings (e.g., `BAAI/bge-small-en-v1.5` or `all-MiniLM-L6-v2` via `sentence-transformers`) stored in local `Qdrant` or `Chroma` `[SRC-016, SRC-022]`.
  3. **Hybrid fusion:** Reciprocal Rank Fusion (`RRF`, $k=60$) combining lexical and dense rankings `[SRC-009]`.
  4. **Reranking & Query Transformation:** Lightweight cross-encoder reranking (`ms-marco-MiniLM-L-6-v2`) and query rewriting/decomposition.
  5. **Metadata & Access Filtering:** Pre-retrieval document-level ACL filtering to prevent cross-tenant leakage (OWASP LLM08:2025; AISVS Chapter C8) `[SRC-001, SRC-002]`.
  6. **Comparative Evaluation Deliverable:** Learners construct a labelled retrieval evaluation dataset ($\ge 30$ query-document-answer triples) and report quantitative comparisons (`Recall@k`, `MRR@k`, `NDCG@k`, faithfulness, and latency) across **BM25-only vs Dense-only vs Hybrid+RRF vs Hybrid+RRF+Rerank** `[SRC-011]`.

### 6.3 Track 3: Agentic AI Engineering (Incorporating CD-03)
- **Core focus:** Bounded, auditable, permissioned tool-using agents and standardized context integrations.
- **Implementation of CD-03 (MCP):**
  - Teach MCP architecture (`Hosts`, `Clients`, `Servers`) and core primitives (`Tools`, `Resources`, `Prompts`) using the official Python `mcp` SDK (`FastMCP` / low-level server) `[SRC-005, SRC-016]`.
  - Address **protocol currency**: cover local `stdio` transport, `Streamable HTTP`, OAuth 2.1 Resource Server permissions (`2025-03-26` to `2025-11-25`), and the `2026-07-28` stateless request headers and `server/discover` pattern so learners understand both deployed SDKs and the latest specification `[SRC-005]`.
  - **Security & AISVS alignment:** Apply AISVS **Chapter C9 (Orchestration & Agentic Security)** and **Chapter C10 (Model Context Protocol Security)**—enforcing tool-level JSON schema validation, read-only vs destructive tool annotations, human-in-the-loop approval for state-mutating actions, step/token budgets, and indirect prompt-injection defences `[SRC-001, SRC-002]`.

### 6.4 Track 4: Edge & Offline AI Engineering (Incorporating CD-05)
- **Core focus:** Resource-constrained inference, quantisation trade-offs, local RAG/services, and offline-first synchronisation.
- **Implementation of CD-05 (Standard Edge AI Benchmark Report):**
  - Because learner hardware varies across the cohort (OQ-06), **comparability is defined within-host**: each learner benchmarks **at least two distinct model/quantisation configurations** (e.g., `Q4_K_M` vs `Q8_0`, or 1.5B vs 3B parameter models) on the **exact same machine, OS state, thread count, and fixed prompt/evaluation suite** `[SRC-014]`.
  - Required metrics:
    1. **Task quality** on a fixed 25-item evaluation dataset (exact match / rubric score) plus optional perplexity (`llama-perplexity`).
    2. **Latency & throughput:** Time-to-First-Token (`TTFT` ms), prompt processing speed (`tokens/sec`), token generation speed (`tokens/sec`) via `llama-bench` or instrumented runner `[SRC-014]`.
    3. **Memory & footprint:** Disk size (MB), peak resident set size (`RSS` MB), KV-cache allocation at fixed context (`-c 2048` vs `-c 4096`).
    4. **Hardware & thermal/battery profile:** Exact CPU model, physical/logical cores, RAM speed, GPU/iGPU status, and sustained 10-minute stability.
    5. **Offline behaviour:** Cold-start load time and zero-network verification (airplane-mode / firewall test).

---

## 7. Assessment and capstone recommendations

1. **Proportionate Application of OWASP AISVS 1.0 (CD-02):**
   AISVS 1.0 contains 12 chapters covering the entire AI lifecycle, including foundation model training (C1, C11) `[SRC-001]`. Since learners build applied systems rather than pre-training foundation models, capstones must use a **Proportionate AISVS Verification Profile**:
   - **Mandatory for all capstones:** C2 (Input Validation), C4 (Infrastructure & Config), C5 (Access Control & Identity), C6 (Supply Chain / Model Provenance), C7 (Output Control & Safety), C12 (Monitoring & Logging).
   - **Track-specific mandatory chapters:** C8 (Memory, Embeddings & Vector DB Security) for Track 2 / RAG; C9 (Orchestration & Agentic Security) and C10 (MCP Security) for Track 3 / Agents; C3 (Lifecycle & Serialization Integrity) for Track 4 / Edge.
   - **Mandatory disclaimer:** Every report must state that the AISVS checklist is an *internal educational engineering verification against selected controls* and does **not** constitute certification, accreditation, or an independent security audit (CD-02).
2. **Hybrid Team / Individual Capstone Accountability (Resolving OQ-01 & OQ-02):**
   - Weeks 5–10 operate in **single-track mentor pods of 6–7 learners** (8 mentors for 50 learners) so mentors provide deep track-specific code review.
   - Weeks 11–14 assemble **5 cross-functional product teams of ~10 learners** (combining Application, RAG, Agentic, and Edge specialists) to build an end-to-end capstone product.
   - **Individual competence gate:** Every learner must own a named module with traceable Git commits, submit an individual section of the AI System Evaluation Report (CD-01) and AISVS Security Assessment (CD-02), and pass an **individual 15-minute oral technical defence**.

---

## 8. Nigerian and resource-constrained delivery considerations

### 8.1 Learner Hardware Specification (Resolving OQ-06)
Based on `llama.cpp` `GGUF` memory formulas ($\text{Weight RAM} \approx 0.55\text{–}0.6\text{ GB per billion parameters at } Q4\_K\_M$ plus 1.5–3 GB KV cache and 3.5 GB OS overhead) `[SRC-014]`:

| Tier | CPU | System RAM | Storage | Local Model Ceiling (`Q4_K_M`, `-c 2048`) | Fallback Provision |
|---|---|---|---|---|---|
| **Minimum Baseline** | 64-bit x86_64 or ARM64, 4 physical cores (e.g., Intel Core i5 8th Gen / Ryzen 5 3500U) | **8 GB RAM** | 25 GB free SSD | **0.5B – 3B models** (e.g., `Qwen2.5-1.5B-Instruct`, `Llama-3.2-3B-Instruct` ~2.0 GB weights) | Free-tier cloud inference (Groq / Google AI Studio / GitHub Models / HF Serverless) or Kaggle/Colab CPU/T4 for 7B+ comparisons. |
| **Recommended Spec** | 6–8+ physical cores (Intel i5/i7 11th Gen+, Ryzen 5/7 5000+, or Apple M1–M4) | **16 GB+ RAM** | 50 GB+ free NVMe SSD | **3B – 8B models** (e.g., `Llama-3.1-8B-Instruct`, `Qwen2.5-7B-Instruct` ~4.8 GB weights) | Full local execution across all four tracks. |

### 8.2 Power, Bandwidth, and Regulatory Realities
- **Offline-first lab packaging:** Model weights (1–2 GB) and embedding models (`~90–130 MB`) must be listed in a **Pre-Week Download Manifest** so learners can fetch them once during off-peak/cheap data windows or via local peer USB distribution, then run all labs completely offline.
- **Asynchronous parity (OQ-05):** Live sessions must be recorded at low bitrate (720p/360p + audio-only + Markdown transcripts) so power or ISP outages do not penalise learners who submit verified GitHub labs and async check-ins.
- **Nigeria Data Protection Act (NDPA) 2023 `[SRC-007]`:** Learners building systems for Nigerian healthcare, fintech, legal, or public services must apply NDPA **Section 24** (data minimisation, purpose limitation), **Section 28** (Data Privacy Impact Assessment trigger for AI/profiling), and **Section 37** (prohibition on solely automated decisions with legal/significant effect without explicit consent/contract and human-intervention safeguards).

---

## 9. Recommended tools and learning resources

To uphold Principles 8–13, each layer standardises on **one primary open-source tool** and one lightweight alternative:

| Layer | Primary Standard Tool | Lightweight / Constrained Alternative | Rationale |
|---|---|---|---|
| **Language & Packaging** | Python 3.11+ with `uv` or `venv` + `pip` | Standard `venv` | Fast, reproducible dependency lockfiles. |
| **Backend & Validation** | `FastAPI` + `Pydantic v2` + `httpx` `[SRC-018]` | Standard library + `Pydantic` | Industry standard for typed async Python AI services. |
| **Local Inference & Edge** | `Ollama` + `llama.cpp` (`llama-bench`, `llama-server`) `[SRC-014, SRC-015]` | `ONNX Runtime` (CPU) | Runs `GGUF` models on CPU with an OpenAI-compatible local API. |
| **Embeddings & Reranking** | `sentence-transformers` (`bge-small-en-v1.5`, `ms-marco-MiniLM-L-6-v2`) `[SRC-016]` | `FastEmbed` (ONNX CPU) | Small (<150 MB), fast on CPU, no API keys required. |
| **Lexical & Vector Search** | `rank-bm25` + `Qdrant` (local mode / embedded disk) `[SRC-022]` | `SQLite FTS5` + `Chroma` local | Zero-server local persistence; supports metadata filtering and RRF. |
| **Agent Orchestration & MCP** | Raw Python ReAct loop → `LangGraph` + Official `mcp` Python SDK `[SRC-005, SRC-019]` | `smolagents` `[SRC-016]` | Teaches state machines explicitly before graph abstractions; official MCP SDK ensures spec compliance. |
| **Evaluation & Observability** | `pytest` + `Arize Phoenix` (local OpenTelemetry collector) + `RAGAS` `[SRC-006, SRC-011, SRC-020]` | `Promptfoo` CLI + JSONL trace logger `[SRC-021]` | Runs 100% locally without cloud SaaS accounts. |

---

## 10. Risks, obsolete material, and emerging technologies to monitor

- **Obsolete / Deprecated patterns to exclude:**
  - Legacy LangChain `Chain` classes (`LLMChain`, `RetrievalQA`)—superseded by direct SDKs, runnable pipelines, or `LangGraph`.
  - Deprecated OpenTelemetry attribute `gen_ai.system`—use `gen_ai.provider.name` `[SRC-006]`.
  - Treating MCP as purely stateful SSE—teach `stdio`, `Streamable HTTP`, and the `2026-07-28` stateless request/discovery evolution `[SRC-005]`.
- **Emerging technologies to monitor (optional enrichment, not core dependencies):**
  - Multimodal vision-language edge models (`Qwen2.5-VL-3B`, `Llama-3.2-Vision`).
  - GraphRAG (include only as an advanced optional pattern due to high token/indexing cost on constrained hardware).

---

## 11. Prioritised recommendations register

| ID | Recommendation | Urgency | Affected Document(s) | Type | Rationale & Sources |
|---|---|---|---|---|---|
| **R-01** | Establish a 2-week self-paced Preparatory Pathway (10–15 h) with a mandatory pre-cohort diagnostic test. | **High** | `MASTER_PROGRAMME_BLUEPRINT.md`, `02_COMMON_CORE/` | Necessary correction | Protects the 48–60 h Common Core from stalling on basic Python/Git gaps (PD-04, OQ-04). |
| **R-02** | Define a **Proportionate AISVS 1.0 Profile** (core chapters C2, C4, C5, C6, C7, C12 + track chapters C8/C9/C10/C3) for capstones. | **High** | `MASTER_PROGRAMME_BLUEPRINT.md`, `04_ASSESSMENT/` | Necessary correction | Aligns CD-02 with the verified 12-chapter structure of OWASP AISVS 1.0 (June 2026) `[SRC-001]`. |
| **R-03** | Adopt a two-phase cohort grouping: single-track mentor pods (6–7 learners) in W5–10; cross-track product teams (~10 learners) with individual module ownership and oral defence in W11–14. | **High** | `MASTER_PROGRAMME_BLUEPRINT.md`, Stage 4 & 5 plans | Necessary correction | Resolves the structural tension between 4 tracks, 1:6–7 mentorship, and 5 teams of 10 (OQ-01, OQ-02). |
| **R-04** | Initiate capstone architecture, evaluation dataset construction (CD-01), and AISVS threat modelling (CD-02) in **Week 11**, reserving Weeks 13–14 for hardening, benchmarking, documentation, and defence. | **High** | `MASTER_PROGRAMME_BLUEPRINT.md`, Stage 5 plans | Necessary correction | 24–30 hours in Weeks 13–14 is insufficient to build and verify a production system from scratch (OQ-03). |
| **R-05** | Specify the dual-tier hardware baseline (8 GB RAM minimum running 1.5B–3B `Q4_K_M` models; 16 GB recommended running 7B–8B) + Model Provider Adapter fallback + Pre-Week Download Manifests. | **High** | `MASTER_PROGRAMME_BLUEPRINT.md`, all track syllabi | Suggested improvement | Resolves OQ-06 using empirical `llama.cpp` memory sizing `[SRC-014, SRC-015]`. |
| **R-06** | Teach MCP core primitives (`Tools`, `Resources`, `Prompts`) alongside both OAuth 2.1 permissions and the `2026-07-28` stateless discovery architecture. | **Medium** | `03_SPECIALISATION_TRACKS/AGENTIC_AI_ENGINEERING/` | Suggested improvement | Ensures CD-03 reflects verified 2025–2026 MCP specification releases `[SRC-005]`. |
| **R-07** | Embed Nigeria Data Protection Act (NDPA) 2023 requirements (s.24, s.28 DPIA, s.37 automated decisions) into Common Core Week 4 and Capstone readiness checks. | **Medium** | `MASTER_PROGRAMME_BLUEPRINT.md`, `02_COMMON_CORE/` | Suggested improvement | Grounds responsible AI in enforceable Nigerian law `[SRC-007]`. |

---

## Change log

| Version | Date | Change |
|---|---|---|
| 0.1 | 2026-11-16 | Completed Stage 1 research and benchmarking report. |
