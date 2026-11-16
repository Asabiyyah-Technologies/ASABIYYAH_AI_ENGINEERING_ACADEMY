# PROJECT BANK AND TECHNICAL RESOURCE LIBRARY
## Asabiyyah Technologies Global Applied AI Engineering Masterclass

| Field | Value |
|---|---|
| Document ID | ASB-PRJ-001 |
| Version | 0.1 Draft |
| Status | Draft – pending management review |
| Owner (role) | Lead Project Architect & Resource Curator (TBC) |
| Last updated | 2026-11-16 |
| Parent document | [MASTER_PROGRAMME_BLUEPRINT.md](../MASTER_PROGRAMME_BLUEPRINT.md) §§11–14, 21 |
| Related decisions | AD-01–03, CD-01–05, PD-03–05, PR-04–09 |
| Stage of origin | Stage 11 |

> **Engineering Standard:** Every project in this bank connects directly to measurable programme learning outcomes, enforces the 7-dimension assessment rubric (`04_ASSESSMENT/Assessment_Framework_and_Rubrics.md`), runs on the 8 GB RAM CPU-compatible baseline (`PR-06`), and requires empirical evaluation (`CD-01`) and proportionate **OWASP AISVS 1.0** security controls (`CD-02`).

---

## 1. Progressive Project Architecture Overview

Learners build three progressive tiers of production-structured repositories across the 14 weeks:
1. **Tier 1 — Common Core Foundation Projects (`PRJ-CC-01` & `PRJ-CC-02`, Weeks 1–4):** Individual projects mastering typed `FastAPI` backends, `ModelProviderAdapter`, 15+ item golden evaluation datasets (`CD-01`), and foundational `AISVS C2/C7` + `NDPA 2023` PII redaction (`CD-02`).
2. **Tier 2 — Track Specialist Projects (`PRJ-AAE/RAG/AGT/EDG`, Weeks 5–10):** Deep individual specialist systems fulfilling the mandatory track empirical deliverables (`CD-03` MCP, `CD-04` Hybrid RAG & RRF comparison, `CD-05` Edge Benchmark Report).
3. **Tier 3 — Cross-Functional Capstone Product Briefs (`PRJ-CAP-01` to `PRJ-CAP-05`, Weeks 11–14):** Integrated 10-person team products combining all four tracks with individual module ownership and oral defence.

---

## 2. Common Core Project Collection (Weeks 1–4)

### PRJ-CC-01: Multilingual Customer & Citizen Service Triage & Structured Extraction Service (Primary Gate 1 Project)
- **Learning Purpose & Outcomes:** Master `CC-01` through `CC-09` (`CC-LO-1` to `CC-LO-4`).
- **Problem Statement & Target Users:** Nigerian municipal service desks, fintech support teams, and telecom operators receive thousands of unstructured messages mixing English, Nigerian Pidgin, Hausa, Yoruba, and Igbo. Manual routing causes delays, while naive LLM wrappers hallucinate categories or leak customer PII (phone numbers, NINs, BVNs).
- **Difficulty & Prerequisites:** *Foundational–Intermediate* | Weeks 1–4 Common Core.
- **Functional Requirements:**
  1. `POST /v1/triage` endpoint accepting raw ticket text and metadata, returning a strict `Pydantic v2` `TriageDecision` schema (`category`, `urgency_score`, `detected_language`, `extracted_entities`, `redacted_summary`, `routing_queue`).
  2. Configuration-driven `ModelProviderAdapter` switching seamlessly between local `Ollama` (`qwen2.5:1.5b`) and a remote OpenAI-compatible API with 1-retry schema repair.
  3. Pre-inference **NDPA 2023 PII Redaction Middleware** masking Nigerian phone numbers, emails, NIN, and BVN patterns before model transit or trace logging.
- **Non-Functional Requirements:** $p_{95}$ latency $\le 3,500\text{ ms}$ on CPU; $\ge 85\%$ `pytest` pass rate; 100% schema conformance on valid inputs; runs offline with local model.
- **Suggested Architecture & Stack:** `FastAPI` $\rightarrow$ `PIIRedactor` $\rightarrow$ `TriageService` $\rightarrow$ `ModelProviderAdapter` (`Ollama`/`httpx`) + `SQLite` audit store + OpenTelemetry JSONL/`Arize Phoenix` tracer.
- **Development Milestones:** W1: Typed API & tests $\rightarrow$ W2: Provider adapter & schema validator $\rightarrow$ W3: 20-item golden dataset & OpenTelemetry traces (`CD-01`) $\rightarrow$ W4: Adversarial prompt-injection hardening & `AISVS C2/C5/C7/C12` checklist (`CD-02`).
- **Testing, Evaluation & Security Criteria:** 20-case golden dataset (15 functional + 5 adversarial prompt-injection/PII probes); automated `python -m evals.run_eval` scorecard; `Evaluation_and_Security_Report.md`.
- **Expected Deliverables & Extensions:** Complete GitHub repo, `Dockerfile`, Evaluation & Security Report. *Extension:* Add batch CSV processing with async concurrency control (`asyncio.Semaphore`).
- **Assessment Rubric:** Graded on the **Common Core Gate 1 Rubric (`D1`–`D7`)** in `04_ASSESSMENT/Assessment_Framework_and_Rubrics.md` §4.

### PRJ-CC-02 (Alternative Common Core Project): Structured Engineering Incident & Log Root-Cause Summariser
- **Overview:** Ingests multi-service application error logs and stack traces, masks secrets/tokens (`AISVS C4/C12`), extracts structured root-cause hypotheses (`component`, `severity`, `error_signature`, `suggested_runbook_step`) via `ModelProviderAdapter`, and evaluates accuracy on a 20-incident golden dataset (`CD-01`, `CD-02`).

---

## 3. Four Specialist Track Project Collections (Weeks 5–10 — Gate 3)

Each track provides a primary flagship project and a second domain alternative. Every project includes all 18 required specification elements and is graded on its corresponding **Gate 3 Rubric (`D1`–`D7`)** in `04_ASSESSMENT/Assessment_Framework_and_Rubrics.md` §5.

---

### 3.1 Track 1 Collection: AI Application Engineering (`SC-AAE`)

#### PRJ-AAE-01: Resilient Multi-Provider SME Financial & Operations Copilot Web Application
1. **Learning Purpose:** Master full-stack AI service engineering (`AAE-LO-1` to `AAE-LO-5`).
2. **Problem Statement & Target Users:** Nigerian SMEs and accounting clerks need an AI web application to extract invoice line items, reconcile bank narrations, and draft vendor responses—without failing when a cloud API hits rate limits or slow 3G connections drop.
3. **Difficulty & Prerequisites:** *Intermediate–Advanced* | Common Core Gate 1 pass.
4. **Functional Requirements:**
   - Multi-provider LLM gateway (`Ollama` local $\leftrightarrow$ remote API failover) with circuit breakers and tenant-isolated SQLite exact + semantic caching.
   - Stateful multi-turn workspace with rolling token-budget summarisation (`\le 2,048` context tokens) and 3 deterministic financial calculation tools.
   - Real-time `Server-Sent Events (SSE)` streaming web UI (`HTMX`/React) with user stream abort and slow-network reconnection.
   - JWT/RBAC authentication (`clerk`, `manager`, `auditor`) and per-user daily token-bucket rate limiting (**OWASP LLM10:2025**).
5. **Non-Functional Requirements:** Cache-hit latency $<25\text{ ms}$; `TTFT` $<1,200\text{ ms}$; 99.5% completion rate under 30% simulated upstream failure chaos test.
6. **Suggested Architecture & Stack:** `FastAPI`, `Pydantic v2`, `SQLite` (WAL mode), `SSE`, `HTMX`, `pytest`, `Docker`, `Arize Phoenix` / OpenTelemetry (`gen_ai.*`).
7. **Milestones:** W5: Failover gateway & cache $\rightarrow$ W6: Stateful tools $\rightarrow$ W7: Streaming UI $\rightarrow$ W8: RBAC, LLM10 quotas & AISVS hardening $\rightarrow$ W9: 30-case CI eval suite $\rightarrow$ W10: Docker build & defence.
8. **Testing, Evaluation (`CD-01`) & Security (`CD-02`):** 30-case golden dataset + CI regression runner; chaos failover test; **AISVS 1.0 Chapters C2, C4, C5, C6, C7, C12** verification report + NDPA PII redaction.
9. **Expected Deliverables & Extensions:** Full repository, `Dockerfile`, **Track 1 AI System Evaluation & Security Report**. *Extension:* Idempotent webhook ingestion for automated receipt processing.

#### PRJ-AAE-02 (Track 1 Alternative): Multi-Tenant Clinical Discharge & Referral Documentation Assistant
- Full-stack streaming web application for hospital clinicians featuring strict `Pydantic` ICD-10/SOAP note validation, multi-provider failover, clinician RBAC, `NDPA 2023` patient PII redaction, and a 30-case clinical accuracy & safety evaluation suite.

---

### 3.2 Track 2 Collection: RAG & Knowledge Engineering (`SC-RAG` — Enforcing `CD-04`)

#### PRJ-RAG-01: Nigerian Regulatory, Legal & Compliance Hybrid Knowledge Engine (NDPA 2023 & CBN Directives)
1. **Learning Purpose:** Master end-to-end hybrid retrieval, rank fusion, reranking, and comparative evaluation (`RAG-LO-1` to `RAG-LO-5` / **CD-04**).
2. **Problem Statement & Target Users:** Compliance officers, lawyers, and fintech engineers querying Nigerian regulations (NDPA 2023, CBN cybersecurity & payment guidelines, CAC rules) suffer severe errors with basic vector search, which misses exact statutory citations (`Section 37(1)(b)`) or leaks restricted internal audit memos across roles.
3. **Difficulty & Prerequisites:** *Intermediate–Advanced* | Common Core Gate 1 pass.
4. **Functional Requirements (Mandatory `CD-04` Stack):**
   - Idempotent ingestion and heading/clause-aware chunking of a 50+ document regulatory & internal policy corpus with rich provenance metadata (`doc_id`, `clause_id`, `effective_date`, `access_role`).
   - Implementation of **all four retrieval modes**:
     1. Lexical baseline (`BM25` via `rank_bm25` / `SQLite FTS5`) `[SRC-008]`.
     2. Dense semantic baseline (`BAAI/bge-small-en-v1.5` in local `Qdrant`) `[SRC-016, SRC-022]`.
     3. **Hybrid Retrieval with Reciprocal Rank Fusion (`RRF`, $k=60$)** `[SRC-009]`.
     4. **Hybrid + Cross-Encoder Reranking** (`cross-encoder/ms-marco-MiniLM-L-6-v2` reranking top-15 to top-5) + **Query Transformation** (rewriting/decomposition).
   - Pre-retrieval **Metadata ACL Filtering** (`public`, `analyst`, `chief_compliance_officer`), grounded generation with verified `[doc_id:clause_id]` citations, and deterministic abstention when confidence is below threshold.
5. **Non-Functional Requirements:** Total CPU reranked retrieval latency $p_{95} \le 450\text{ ms}$ on 8 GB laptop; **0.0% cross-tenant ACL leak rate**.
6. **Milestones:** W5: Structure-aware ingestion $\rightarrow$ W6: BM25 & Qdrant indexes $\rightarrow$ W7: Hybrid RRF, cross-encoder & query rewrite $\rightarrow$ W8: ACL pushdown & AISVS C8 security $\rightarrow$ W9: 35-query 4-way benchmark (`CD-04`) $\rightarrow$ W10: FastAPI packaging & defence.
7. **Testing, Evaluation (`CD-01`, `CD-04`) & Security (`CD-02`):**
   - **35+ query labelled test dataset** (exact section lookups, paraphrases, multi-hop questions, unanswerable abstention probes, poisoned-document indirect injection probes).
   - **Mandatory 4-Way Comparative Retrieval & RAG Evaluation Report (`ASB-ASM-002` Template 3)** comparing `BM25`, `Dense`, `Hybrid RRF`, and `Hybrid RRF + Rerank` on `Recall@3/5`, `MRR@5`, `NDCG@5`, Faithfulness, and Citation Precision `[SRC-011]`.
   - **OWASP AISVS 1.0 Chapters C2, C5, C7, C8 (Vector & Embedding Security), C12** verification `[SRC-001]`.
8. **Expected Deliverables & Extensions:** Full hybrid RAG repo, corpus manifest, reproducible benchmark script, and Comparative Evaluation Report. *Extension:* Temporal metadata filtering ("What rule applied as of June 2024 vs today?").

#### PRJ-RAG-02 (Track 2 Alternative): Clinical & Pharmaceutical Drug-Interaction and Treatment Guideline RAG System
- Hybrid `BM25 + Dense + RRF + Cross-Encoder` knowledge engine over WHO/Nigerian Standard Treatment Guidelines and drug formularies, where exact generic drug names/dosages require lexical match and symptom descriptions require semantic match, complete with a 35-query comparative retrieval benchmark (`CD-04`).

---

### 3.3 Track 3 Collection: Agentic AI Engineering (`SC-AGT` — Enforcing `CD-03`)

#### PRJ-AGT-01: MCP-Enabled IT & Cloud/Local Operations Incident Triage and Remediation Agent
1. **Learning Purpose:** Master bounded agent orchestration, stateful checkpointing, and practical **Model Context Protocol (`MCP`)** engineering (`AGT-LO-1` to `AGT-LO-5` / **CD-03**).
2. **Problem Statement & Target Users:** Engineering and DevOps teams need an automated incident triage agent that can inspect logs, query service databases, read runbook resources, and propose configuration fixes—through a standardised protocol (`MCP`) with strict least-privilege permissions and mandatory human approval before any state-mutating action.
3. **Difficulty & Prerequisites:** *Intermediate–Advanced* | Common Core Gate 1 pass.
4. **Functional Requirements (Mandatory `CD-03` Stack):**
   - Custom **MCP Server** built with the Python `mcp` SDK exposing:
     - 4 typed `Tools` (3 read-only diagnostics with `readOnlyHint=True`; 1 state-mutating remediation tool with `destructiveHint=True`),
     - 2 URI-templated `Resources` (`runbook://{service_name}`, `metrics://{host_id}`), and
     - 1 structured diagnostic `Prompt` template `[SRC-005]`.
   - Custom **MCP Client** supporting dynamic capability discovery (`server/discover` & initialization across `stdio` and HTTP, incorporating `2025-11-25` OAuth 2.1 scopes and `2026-07-28` stateless request headers) `[SRC-005]`.
   - Stateful `LangGraph` orchestrator backed by `SqliteSaver` with explicit `max_steps=6` loop breakers and a **Human-in-the-Loop (`interrupt_before`) approval gate** triggered before any `destructiveHint=True` MCP tool call `[SRC-019]`.
5. **Non-Functional Requirements:** 100% enforcement of HITL gate on write operations; graceful recovery from simulated MCP server timeouts; runs locally on 8 GB–16 GB hardware.
6. **Milestones:** W5: Pure Python ReAct loop $\rightarrow$ W6: LangGraph SQLite checkpointing & HITL $\rightarrow$ W7: Custom MCP Server & Client (`CD-03`) $\rightarrow$ W8: OAuth/scope permissions & AISVS C9/C10 sandboxing $\rightarrow$ W9: 25-scenario trajectory benchmark (`CD-01`) $\rightarrow$ W10: Packaging & defence.
7. **Testing, Evaluation (`CD-01`, `CD-03`) & Security (`CD-02`):**
   - **25+ multi-step evaluation scenarios** measuring Task Completion Rate, Tool Selection Precision, Trajectory Efficiency, and Loop-Breaker recovery (`ASB-ASM-002` Template 4).
   - **OWASP AISVS 1.0 Chapters C2, C5, C7, C9 (Orchestration & Agentic Security), C10 (MCP Security), C12** red-team suite testing indirect prompt injection via MCP Resources, confused-deputy scope escalation, and path/SQL traversal `[SRC-001]`.
8. **Expected Deliverables & Extensions:** Complete MCP Server + Client + Agent repo, protocol test suite, and **Agentic & MCP Evaluation and Security Report**. *Extension:* Add a bounded 2-role Supervisor $\rightarrow$ Specialist Worker handoff.

#### PRJ-AGT-02 (Track 3 Alternative): MCP-Enabled Supply-Chain Inventory, Procurement & Vendor Compliance Agent
- Stateful `LangGraph` agent + custom **MCP Server/Client** wrapping an SQLite inventory ledger, vendor compliance registry (`Resources`), and purchase-order generator (`destructiveHint=True` requiring manager HITL approval under `NDPA s.37` and `AISVS C9/C10`).

---

### 3.4 Track 4 Collection: Edge & Offline AI Engineering (`SC-EDG` — Enforcing `CD-05`)

#### PRJ-EDG-01: Offline-First Rural Primary Healthcare Triage & Local Medical Reference Node
1. **Learning Purpose:** Master `GGUF` quantisation, CPU memory/thread tuning, offline-first embedded RAG & delta sync, and reproducible edge benchmarking (`EDG-LO-1` to `EDG-LO-5` / **CD-05**).
2. **Problem Statement & Target Users:** Primary healthcare centres and mobile clinics in rural Nigeria frequently operate with zero internet connectivity, intermittent solar/inverter power, and modest 8 GB RAM CPU laptops. Clinicians need a 100% offline clinical intake structuring and guideline lookup assistant that syncs encrypted records only when connectivity returns.
3. **Difficulty & Prerequisites:** *Intermediate–Advanced* | Common Core Gate 1 pass.
4. **Functional Requirements (Mandatory `CD-05` Stack):**
   - Local inference engine (`llama.cpp` `llama-server` / `Ollama`) running quantised `GGUF` open-weight models (`Qwen2.5-1.5B-Instruct` / `Llama-3.2-3B-Instruct`) with explicit context (`-c 2048`) and physical thread pinning `[SRC-014, SRC-015]`.
   - Cryptographic `SHA-256` `ModelManifestVerifier` (`AISVS C3 & C6`) verifying model files before load.
   - Single-file embedded `SQLite` (WAL mode) containing local `FTS5` + CPU `ONNX` vector RAG (`<150 MB` RAM), `cryptography.fernet` encrypted patient PII columns (`NDPA 2023`), and an idempotent offline outbox sync queue.
   - Automated **CD-05 Edge Benchmark Runner (`evals/run_edge_benchmark.py`)** comparing **at least two model/quantisation configurations** (e.g., `Q4_K_M` vs `Q8_0`, or `1.5B Q4_K_M` vs `3B Q4_K_M`) under identical host conditions.
5. **Non-Functional Requirements:** Passes full `pytest` suite with all external network sockets blocked (`--disable-socket`); Peak `RSS` RAM $\le 3.5\text{ GB}$ on 8 GB host; survives simulated `kill -9` power loss without SQLite corruption.
6. **Milestones:** W5: GGUF inspector & local server $\rightarrow$ W6: Quantisation & KV-cache/thread sweep $\rightarrow$ W7: Offline SQLite RAG & delta sync $\rightarrow$ W8: SHA-256 verifier, local PII encryption & AISVS C3/C6 $\rightarrow$ W9: Full CD-05 comparative benchmark $\rightarrow$ W10: Crash recovery & defence.
7. **Testing, Evaluation (`CD-01`, `CD-05`) & Security (`CD-02`):**
   - **Mandatory Reproducible Edge AI Benchmark Report (`ASB-ASM-002` Template 5)** reporting hardware specs, disk footprint, cold-start time, idle/peak `RSS`, `TTFT`, prompt `t/s`, generation `t/s`, 25-item task quality %, schema validity %, 10-min thermal drift, and airplane-mode verification across $\ge 2$ configurations.
   - **OWASP AISVS 1.0 Chapters C2, C3, C4, C5, C6, C7, C12** verification.
8. **Expected Deliverables & Extensions:** Offline-first service repo, benchmark suite, and **Reproducible Edge AI Benchmark Report**. *Extension:* Add voice-note transcription via quantised `whisper.cpp` (`tiny.en`/`base` GGUF) on CPU.

#### PRJ-EDG-02 (Track 4 Alternative): Offline-First Agricultural Extension, Crop Disease Advisory & Field Inspection Logger
- 100% offline field laptop system combining local `GGUF` inference, embedded SQLite crop-management RAG, offline inspection queue with conflict-resilient sync, and a complete $\ge 2$-configuration **Edge AI Benchmark Report (`CD-05`)**.

---

## 4. Cross-Functional Capstone Project Briefs (Weeks 11–14 — Gate 4)

In Week 11, each 10-person cross-functional team selects one integrated Capstone Brief (or proposes a custom brief meeting identical architectural standards) combining Track 1 (Web/Gateway), Track 2 (Hybrid RRF/Reranked RAG — `CD-04`), Track 3 (MCP Server/Client & HITL Agent — `CD-03`), and Track 4 (Local Edge/Offline Runtime & Benchmark — `CD-05`), plus the mandatory **AI System Evaluation Report (`CD-01`)** and **OWASP AISVS 1.0 Security Verification Report (`CD-02`)**:

1. **PRJ-CAP-01: Unified Offline-Capable Clinical Triage, Formulary RAG & Referral Orchestration Platform**
2. **PRJ-CAP-02: Enterprise Nigerian Regulatory Compliance (NDPA / CBN / Tax) Audit & MCP Workflow Platform**
3. **PRJ-CAP-03: Multilingual Agricultural Extension, Co-operative Inventory MCP & Offline Field Advisory Platform**
4. **PRJ-CAP-04: Resilient SME Operations, Contract RAG & Human-Approved Financial Reconciliation Platform**
5. **PRJ-CAP-05: Public Infrastructure & Procurement Transparency RAG, Anomaly Triage & Offline Audit Platform**

---

## 5. Curated Technical Resource Library (100% Free / Open-Source Baseline)

All resources below were verified for availability on **2026-11-16** and require **zero paid subscriptions**:

| Resource ID | Title & Direct Link | Type | Provider | Cost | Difficulty | Relevant Track(s) | Last Verified |
|---|---|---|---|---|---|---|---|
| **LIB-01** | [OWASP AISVS 1.0 Official Project & Standard](https://owasp.org/www-project-artificial-intelligence-security-verification-standard/) `[SRC-001]` | Security Standard | OWASP | Free / Open | Intermediate–Adv | All Tracks & Capstone (`CD-02`) | 2026-11-16 |
| **LIB-02** | [OWASP Top 10 for LLM Applications (2025)](https://owasp.org/www-project-top-10-for-large-language-model-applications/) `[SRC-002]` | Security Standard | OWASP | Free / Open | Foundational | Common Core & All Tracks | 2026-11-16 |
| **LIB-03** | [Model Context Protocol (MCP) Specification (`2025-11-25` & `2026-07-28`)](https://modelcontextprotocol.io/specification) `[SRC-005]` | Protocol Spec & SDK | MCP / Linux Foundation | Free / Open | Intermediate–Adv | Track 3 Agentic & Capstone (`CD-03`) | 2026-11-16 |
| **LIB-04** | [Hugging Face Free Courses: LLM Course, AI Agents Course & MCP Course](https://huggingface.co/learn) `[SRC-016]` | Interactive Courses | Hugging Face | Free | Foundational–Adv | Core, Track 2, Track 3, Track 4 | 2026-11-16 |
| **LIB-05** | [OpenTelemetry GenAI Semantic Conventions (`semantic-conventions-genai`)](https://opentelemetry.io/docs/specs/semconv/gen-ai/) `[SRC-006]` | Telemetry Spec | CNCF / OpenTelemetry | Free / Open | Intermediate | Core & All Tracks (`CD-01`) | 2026-11-16 |
| **LIB-06** | [NIST AI RMF 1.0 (`AI 100-1`) & Generative AI Profile (`AI 600-1`)](https://doi.org/10.6028/NIST.AI.600-1) `[SRC-003, SRC-004]` | Risk Framework | NIST | Free / Public | Foundational–Int | Core & Capstone (`CD-01`, `CD-02`) | 2026-11-16 |
| **LIB-07** | [Nigeria Data Protection Act (NDPA) 2023 & NDPC Portal](https://ndpc.gov.ng/) `[SRC-007]` | Legal / Regulatory | Fed. Rep. of Nigeria | Free / Public | Foundational–Int | Core, Policies & Capstone | 2026-11-16 |
| **LIB-08** | [FastAPI & Pydantic v2 Official Documentation](https://fastapi.tiangolo.com/) `[SRC-018]` | Framework Docs | FastAPI / Pydantic | Free / MIT | Foundational–Adv | Core & Track 1 | 2026-11-16 |
| **LIB-09** | [Robertson & Zaragoza (2009) *BM25* & Cormack et al. (2009) *Reciprocal Rank Fusion (RRF)*](https://doi.org/10.1145/1571941.1572114) `[SRC-008, SRC-009]` | Foundational Papers | SIGIR / FnTIR | Free Access | Intermediate | Track 2 RAG (`CD-04`) | 2026-11-16 |
| **LIB-10** | [Sentence-Transformers (`bge-small-en-v1.5` & `ms-marco-MiniLM-L-6-v2` Reranker)](https://sbert.net/) `[SRC-016]` | Model & Library Docs | UKP Lab / Hugging Face | Free / Apache-2.0 | Intermediate | Track 2 RAG (`CD-04`) | 2026-11-16 |
| **LIB-11** | [Qdrant Local Mode Documentation & SQLite FTS5 Guide](https://qdrant.tech/documentation/) `[SRC-022]` | Database Docs | Qdrant / SQLite | Free / Open | Intermediate | Track 2 RAG & Track 4 Edge | 2026-11-16 |
| **LIB-12** | [`llama.cpp` Repository, GGUF Spec & `llama-bench` Documentation](https://github.com/ggml-org/llama.cpp) `[SRC-014]` | Engine & Benchmark | ggml-org | Free / MIT | Intermediate–Adv | Track 4 Edge (`CD-05`) | 2026-11-16 |
| **LIB-13** | [Ollama Local Model Runner & API Docs](https://ollama.com/) `[SRC-015]` | Local Model Runner | Ollama | Free / MIT | Foundational–Int | Core & All Tracks | 2026-11-16 |
| **LIB-14** | [Arize Phoenix Open-Source Tracing & Promptfoo CLI Docs](https://docs.arize.com/phoenix) `[SRC-020, SRC-021]` | Eval & Observability | Arize / Promptfoo | Free / Open | Intermediate | Core & All Tracks (`CD-01`, `CD-02`) | 2026-11-16 |
| **LIB-15** | [DeepLearning.AI Short Courses (RAG, LangGraph, LLMOps)](https://www.deeplearning.ai/courses/) `[SRC-017]` | Supplementary Video | DeepLearning.AI | Free Audit Tier | Foundational–Int | Optional Supplementary | 2026-11-16 |

---

## 6. Hardware and Infrastructure Alternatives Matrix (Zero-Cost Resilience)

| Learner Constraint Scenario | Local Software / Model Adjustment | Zero-Cost Cloud / Fallback Option |
|---|---|---|
| **8 GB RAM CPU-Only Laptop (Minimum Spec)** | Use `Qwen2.5-1.5B-Instruct Q4_K_M` (`~986 MB`) or `Llama-3.2-1B/3B Q4_K_M` with `-c 2048` context cap; embedded `SQLite` / local disk `Qdrant` (skip heavy Docker Desktop overhead). | Use `ModelProviderAdapter` pointed at free-tier OpenAI-compatible endpoints (Google AI Studio / Groq / GitHub Models) when testing 8B–70B model comparisons. |
| **Intermittent Internet / High Data Cost** | Download the weekly `<2 GB` Pre-Week Asset Manifest once during night/off-peak data bundles; set `HF_HUB_OFFLINE=1`; run 100% of labs and `pytest` suites offline. | Use `<60 MB` audio-only + Markdown session packs and the 24-hour PR outage grace window. |
| **Frequent Power Cuts (No Inverter)** | Enable `SQLite PRAGMA journal_mode=WAL` and `LangGraph SqliteSaver` checkpointing so interrupted benchmarks or agent runs resume from the last completed item. | Run heavy batch evaluations on a free GitHub Actions workflow or Kaggle CPU/T4 notebook triggered via a tiny `git push`. |

---

## Change log

| Version | Date | Change |
|---|---|---|
| 0.1 | 2026-11-16 | Created in Stage 11 covering the complete Project Bank, 18-point project specifications, verified Resource Library, and hardware alternatives. |
