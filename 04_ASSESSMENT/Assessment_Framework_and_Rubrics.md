# PROGRAMME ASSESSMENT FRAMEWORK, RUBRICS, MODERATION POLICY AND TECHNICAL DEFENCE GUIDE
## Asabiyyah Technologies Global Applied AI Engineering Masterclass

| Field | Value |
|---|---|
| Document ID | ASB-ASM-001 |
| Version | 0.1 Draft |
| Status | Draft – pending management review |
| Owner (role) | Lead Assessment Architect & Programme Director (TBC) |
| Last updated | 2026-11-16 |
| Parent document | [MASTER_PROGRAMME_BLUEPRINT.md](../MASTER_PROGRAMME_BLUEPRINT.md) §17 |
| Related decisions | AD-01–03, CD-01–05, PD-03–05, GD-01–02 |
| Stage of origin | Stage 6 |

> **Governance note:** This document defines the authoritative assessment framework, the 7-dimension assessment weighting, moderation/reassessment policies, technical defence protocol, and criterion-referenced rubrics for the Common Core, the four active Specialisation Tracks, and the Capstone. Companion file [Evaluation_Security_and_Benchmark_Templates.md](Evaluation_Security_and_Benchmark_Templates.md) (`ASB-ASM-002`) contains the executable templates for `CD-01` through `CD-05`.

---

## 1. Assessment philosophy and anti-superficiality standard

Assessment in the Asabiyyah Technologies Global Applied AI Engineering Masterclass measures **verifiable engineering competence**: a learner's ability to design, implement, test, evaluate, secure, document, and orally defend working AI software systems under realistic constraints.

- **Evidence over attendance or memorisation:** No credit is awarded for multiple-choice trivia, passive attendance, or unverified screenshots. Every major submission requires a reproducible GitHub repository, automated `pytest` tests, quantitative evaluation outputs (CD-01), security verification checks (CD-02), and traceable Git commit history.
- **Anti-Superficiality Gate:** Any submission that relies on hardcoded mock responses in place of working logic, omits its evaluation dataset, copies unattributed tutorial code, or claims security compliance without executing test cases is marked **Incomplete — Resubmission Required**.

---

## 2. Standard 7-dimension assessment weighting (Validated against Blueprint)

Every major project and capstone assessment across the programme is graded against the seven standard engineering dimensions defined in Stage 6 (totalling **100%**):

| # | Assessment Dimension | Weight | Mapped Blueprint Competencies | Required Observable Evidence |
|---|---|---:|---|---|
| **D1** | **Functional Correctness** | **20%** | `CC-01`, `CC-03`, `CC-05`, `SC-*` | Working end-to-end features passing automated unit/integration `pytest` suites; zero unhandled crashes on valid or malformed inputs. |
| **D2** | **Architecture & Code Quality** | **15%** | `CC-01`, `CC-02`, `CC-05`, `CC-08` | Modular separation of concerns, strict `Pydantic v2` typing, provider-independent adapter pattern, clean Git commit/PR history, no hardcoded secrets. |
| **D3** | **AI Output Quality & Evaluation (CD-01)** | **20%** | `CC-06`, `SC-RAG` (CD-04), `SC-AGT`, `SC-EDG` (CD-05) | Representative golden evaluation dataset ($\ge 15$ items in Core; $\ge 25\text{–}35$ items in Tracks/Capstone), baseline vs improved metrics, OpenTelemetry `gen_ai.*` trace analysis, documented failure taxonomy. |
| **D4** | **Security, Privacy & Reliability (CD-02)** | **15%** | `CC-07`, `SC-*` | Threat model, proportionate **OWASP AISVS 1.0** control verification (`C2, C4, C5, C6, C7, C12` + track chapters `C3/C8/C9/C10`), adversarial red-team test results, **NDPA 2023** PII protection, retry/fallback resilience, mandatory non-certification disclaimer. |
| **D5** | **Performance, Resource & Cost Efficiency** | **10%** | `CC-04`, `CC-06`, `SC-EDG` (CD-05) | Latency percentiles ($p_{50}, p_{95}$, `TTFT`), token/compute cost tracking, RAM/KV-cache budgeting on 8 GB–16 GB hardware, caching/rate-limiting (`LLM10`). |
| **D6** | **Documentation & Reproducibility** | **10%** | `CC-08`, `CC-09` | Architecture diagram, lockfile/`Dockerfile`, one-command local/offline setup guide, honest limitation and risk register. |
| **D7** | **Demonstration & Technical Defence** | **10%** | `CC-09`, `PLO-5` | Live working system demonstration + individual oral technical defence answering code-level, evaluation, and security trade-off questions. |
| | **TOTAL** | **100%** | | |

### Alignment with the Four Programme Progression Gates (Blueprint §17)

The 7 dimensions apply consistently across the four chronological programme gates:
- **Gate 1 — Common Core & Readiness Assessment (End of Week 4 — 20% of overall programme grade):** Graded across D1–D7 (with D7 verified via the 90-minute practical readiness test & mentor code walkthrough). Minimum pass: **65%**.
- **Gate 2 — Weekly Specialisation Labs (Weeks 5–9 — 20% of overall programme grade):** 6 progressive weekly GitHub PRs graded on D1–D6. Minimum pass: **at least 5 of 6 labs accepted ($\ge 65\%$) Triggers early mentor intervention if 2 labs fall behind**.
- **Gate 3 — Track Specialist Project & Mandatory Empirical Report (End of Week 10 — 25% of overall programme grade):** Graded across D1–D7 using the track-specific rubric below. Minimum pass: **70%**.
- **Gate 4 — Integrated Capstone Package & Individual Oral Defence (End of Week 14 — 35% of overall programme grade):** Graded across D1–D7 using the Capstone Rubric below. Minimum pass: **70% on both team artefacts and individual defence**.

---

## 3. Performance band descriptors

All rubrics use four observable performance bands:
- **Distinction (`85–100%`):** Production-grade engineering; clean modular code; comprehensive dataset and trace-backed evaluation; all adversarial security tests pass; reproducible offline/container build; fluent oral defence of trade-offs.
- **Merit / Competent Pass (`70–84%`):** Solid working system meeting all mandatory functional, evaluation (CD-01), security (CD-02), and track-specific (CD-03/04/05) requirements with minor non-critical gaps.
- **Threshold Pass (`65–69%` — valid for Gate 1 & Gate 2 only; Gates 3 & 4 require $\ge 70\%$):** Core functionality and baseline evaluation/security checks work, but edge-case handling or documentation needs refinement.
- **Incomplete / Resubmit (`<65%` in Gates 1–2, or `<70%` in Gates 3–4):** Missing mandatory deliverables, broken build, absent evaluation dataset/report, unpatched critical vulnerability, or inability to explain submitted code during oral defence.

---

## 4. Common Core Assessment Rubric (Gate 1 — End of Week 4)

| Dimension | Weight | Distinction (85–100%) | Competent Pass (65–84%) | Incomplete / Resubmit (<65%) |
|---|---:|---|---|---|
| **D1. Functional Correctness** | 20% | `FastAPI` service & `pytest` suite ($\ge 15$ tests) pass 100%; handles valid, edge, and malformed multilingual inputs cleanly. | All core endpoints work; $\ge 80\%$ of unit/integration tests pass; structured errors returned. | Service crashes on startup or fails core functional tests. |
| **D2. Architecture & Provider Adapter** | 15% | Clean 3-layer package; strict `Pydantic v2` models; `ModelProviderAdapter` switches seamlessly between local `Ollama` and remote API with retry-repair. | Modular Python package; working `ModelProviderAdapter` with local model and `Pydantic` validation. | Monolithic script/notebook; hardcoded single vendor SDK; no schema validation. |
| **D3. AI Evaluation & Tracing (CD-01)** | 20% | Golden dataset ($\ge 20$ cases); automated runner comparing 2+ prompt/model revisions; OpenTelemetry `gen_ai.*` traces (`Arize Phoenix`/JSONL) with root-cause failure analysis. | Golden dataset ($\ge 15$ cases); automated metric table; working trace logs and basic failure summary. | $<15$ test cases; manual inspection only; no trace telemetry. |
| **D4. Security & Privacy (CD-02)** | 15% | Blocks all 5 adversarial prompt-injection payloads; masks Nigerian PII (NIN/BVN/phone/email) under NDPA 2023; complete AISVS C2/C5/C7/C12 table + non-certification disclaimer. | Implements input/output validation, PII redaction, and completed AISVS foundational checklist with disclaimer. | Vulnerable to basic prompt injection; logs raw PII; omits AISVS checklist or disclaimer. |
| **D5. Performance & Cost** | 10% | Tracks $p_{50}/p_{95}$ latency, input/output token counts, and enforces timeout/max-token caps on 8 GB RAM budget. | Reports average latency and token usage with configured request timeouts. | No latency or token measurement; unbounded generation length. |
| **D6. Documentation & Reproducibility** | 10% | Clear `README.md`, architecture diagram, lockfile/`Dockerfile`, offline setup instructions, and honest limitations section. | Working setup instructions, dependency lockfile, and limitation notes. | Cannot be installed/run from instructions on a clean environment. |
| **D7. Readiness Test & Code Walkthrough** | 10% | Scores $\ge 85\%$ on the 90-minute Week 4 Practical Readiness Test and explains every module clearly to mentor. | Scores $\ge 65\%$ on the Practical Readiness Test and demonstrates working code. | Scores $<65\%$ or cannot explain submitted code. |

---

## 5. Four Track-Specific Specialist Project Rubrics (Gate 3 — End of Week 10)

All four tracks apply the standard **D1–D7 weights (`20 / 15 / 20 / 15 / 10 / 10 / 10`)** with specialist observable indicators:

### 5.1 Track 1 Rubric: AI Application Engineering (`ASB-AAE-001`)

| Dimension (Weight) | Track 1 Observable Indicators for Merit / Distinction ($\ge 70\%$) |
|---|---|
| **D1. Functional Correctness (20%)** | Working full-stack/backend AI application with real-time `SSE` streaming, multi-turn state compression, and deterministic tool calling passing $\ge 85\%$ `pytest` coverage. |
| **D2. Architecture & Code Quality (15%)** | Multi-provider gateway with automatic failover (`Ollama` $\leftrightarrow$ remote API), circuit breakers, SQLite exact/semantic cache keyed by tenant, clean async `FastAPI` design. |
| **D3. AI Output Quality & Evaluation — CD-01 (20%)** | Automated CI regression evaluation suite ($\ge 30$ golden cases) + full-stack correlated OpenTelemetry `gen_ai.*` traces + **AI System Evaluation Report** analysing schema pass rate and failure modes. |
| **D4. Security & Reliability — CD-02 (15%)** | JWT/RBAC authentication, per-user token-bucket rate limiting (**OWASP LLM10:2025**), XSS-safe streamed output sanitisation, NDPA PII masking, **AISVS 1.0 Chapters C2, C4, C5, C6, C7, C12** checklist + disclaimer. |
| **D5. Performance & Cost (10%)** | Quantified `TTFT`, $p_{50}/p_{95}$ latency, cache hit-rate savings, and cost per 1,000 requests under simulated 3G/slow network throttling. |
| **D6. Documentation & Reproducibility (10%)** | Multi-stage `Dockerfile`, ADRs, API specification (`OpenAPI`), and documented operational runbook + limitations. |
| **D7. Demonstration & Technical Defence (10%)** | Live demonstration of streaming UX and simulated primary-provider failover, plus oral defence of gateway, caching, and quota design. |

### 5.2 Track 2 Rubric: RAG & Knowledge Engineering (`ASB-RAG-001` — Enforcing CD-04)

| Dimension (Weight) | Track 2 Observable Indicators for Merit / Distinction ($\ge 70\%$) |
|---|---|
| **D1. Functional Correctness (20%)** | Working hybrid RAG pipeline with idempotent multi-format ingestion, structure-aware chunking, query transformation, grounded generation, and verified `[doc_id:chunk_id]` citations + abstention on unanswerable queries. |
| **D2. Architecture & Code Quality (15%)** | Clean modular implementation of **all 4 retrieval modes (`BM25`, `Dense Vector`, `Hybrid + RRF`, `Hybrid + RRF + Cross-Encoder Reranking`)** (CD-04) behind a typed `FastAPI` service `[SRC-008, SRC-009]`. |
| **D3. AI Output Quality & Evaluation — CD-01 & CD-04 (20%)** | Labelled retrieval evaluation dataset ($\ge 35$ queries) + **Comparative Retrieval & RAG Evaluation Report** reporting `Recall@k`, `MRR@k`, `NDCG@k`, Faithfulness, Answer Relevance, and Citation Accuracy across all 4 retrieval modes `[SRC-011]`. |
| **D4. Security & Reliability — CD-02 & CD-04 (15%)** | Pre-retrieval **Metadata & Role-Based ACL Filtering** (zero cross-tenant leakage), indirect prompt-injection defences against poisoned documents, **AISVS 1.0 Chapters C2, C5, C7, C8 (Vector & Embedding Security), C12** + disclaimer `[SRC-001]`. |
| **D5. Performance & Cost (10%)** | Stage-wise latency breakdown (`BM25` ms, `Dense` ms, `RRF` ms, `Cross-Encoder Rerank` ms, `LLM Generation` ms) running within CPU memory budget on 8 GB–16 GB hardware. |
| **D6. Documentation & Reproducibility (10%)** | Reproducible index build script, corpus manifest, `Dockerfile`, and analysis of chunking/RRF/reranking trade-offs and limitations. |
| **D7. Demonstration & Technical Defence (10%)** | Live query demo showing where Hybrid+RRF+Rerank beats BM25-only and Dense-only, plus oral defence of RRF math, ACL filtering, and failure taxonomy. |

### 5.3 Track 3 Rubric: Agentic AI Engineering (`ASB-AGT-001` — Enforcing CD-03)

| Dimension (Weight) | Track 3 Observable Indicators for Merit / Distinction ($\ge 70\%$) |
|---|---|
| **D1. Functional Correctness (20%)** | Working stateful agent (`LangGraph` + SQLite checkpointing) integrated with a **custom, working Model Context Protocol (`MCP`) Server and Client** exposing `Tools`, `Resources`, and `Prompts` (CD-03) `[SRC-005, SRC-019]`. |
| **D2. Architecture & Code Quality (15%)** | Clean separation between orchestrator state graph and MCP Server; dynamic capability discovery (`server/discover` & initialization); explicit `max_steps` budgets, loop detection, and human-in-the-loop (`interrupt_before`) approval gates. |
| **D3. AI Output Quality & Evaluation — CD-01 & CD-03 (20%)** | 25+ scenario agent benchmark measuring **Task Completion Rate**, **Tool Selection Accuracy**, **Trajectory Efficiency**, and **Invalid Tool Call Rate**, backed by step-level OpenTelemetry `gen_ai.agent.*` and MCP spans. |
| **D4. Security & Reliability — CD-02 & CD-03 (15%)** | Scoped MCP authentication/authorization (OAuth 2.1 Resource Server patterns), `readOnlyHint`/`destructiveHint` enforcement, path/SQL sandboxing, indirect prompt-injection resilience, **AISVS 1.0 Chapters C2, C5, C7, C9 (Agentic), C10 (MCP Security), C12** + disclaimer `[SRC-001, SRC-005]`. |
| **D5. Performance & Cost (10%)** | Token and latency accounting per agent step; bounded step budgets preventing runaway token consumption (**OWASP LLM10:2025**). |
| **D6. Documentation & Reproducibility (10%)** | MCP tool/resource schema catalogue, protocol version compatibility notes (`2025-11-25` & `2026-07-28`), `Dockerfile`, and failure-recovery documentation. |
| **D7. Demonstration & Technical Defence (10%)** | Live demo of MCP Inspector discovery, human-approval interrupt/resume, and blocked unauthorized tool call, plus oral defence of agent security boundaries. |

### 5.4 Track 4 Rubric: Edge & Offline AI Engineering (`ASB-EDG-001` — Enforcing CD-05)

| Dimension (Weight) | Track 4 Observable Indicators for Merit / Distinction ($\ge 70\%$) |
|---|---|
| **D1. Functional Correctness (20%)** | Working local AI & embedded SQLite RAG service (`llama.cpp`/`Ollama`) passing automated integration tests with **external network access completely disabled (airplane-mode test)** and working delta sync upon reconnection. |
| **D2. Architecture & Code Quality (15%)** | Clean local serving architecture, explicit context/thread/batch configuration, SQLite WAL crash-safe persistence, idempotent outbox sync queue, and `HF_HUB_OFFLINE=1` enforcement. |
| **D3. AI Output Quality & Evaluation — CD-01 & CD-05 (20%)** | 25-item evaluation dataset comparing task accuracy, schema validity %, and quantization quality degradation across **$\ge 2$ model/quantisation configurations under identical host conditions** (CD-05) `[SRC-014]`. |
| **D4. Security & Reliability — CD-02 (15%)** | Cryptographic `SHA-256` model manifest verification, zero unsafe `pickle` weights, `127.0.0.1` loopback binding, encrypted local PII storage (NDPA 2023), crash/power-loss recovery test (`kill -9`), **AISVS 1.0 Chapters C2, C3 (Lifecycle), C4, C5, C6 (Supply Chain), C7, C12** + disclaimer `[SRC-001]`. |
| **D5. Performance & Cost — CD-05 (10%)** | Complete **Reproducible Edge AI Benchmark Report** measuring Cold-Start Load Time, `TTFT` ($p_{50}/p_{95}$), Prompt `tokens/sec`, Generation `tokens/sec`, Disk Size (MB), Idle/Peak `RSS` RAM (MB), KV-cache budget, and 10-minute sustained thermal stability. |
| **D6. Documentation & Reproducibility (10%)** | Exact hardware/OS disclosure, one-command benchmark reproduction script (`run_edge_benchmark.py`), offline asset manifest, and hardware deployment recommendation (8 GB vs 16 GB). |
| **D7. Demonstration & Technical Defence (10%)** | Live airplane-mode execution and memory profiler demonstration, plus oral defence of quantisation (`Q4_K_M` vs `Q8_0`), KV-cache sizing, and sync conflict resolution. |

---

## 6. Capstone Assessment Rubric (Gate 4 — End of Week 14, 35% of Programme Grade)

The Capstone Package combines **Team Product Delivery (70% of Gate 4 score)** and **Individual Module, Report Section & Oral Technical Defence Accountability (30% of Gate 4 score)** across all 12 required capstone items:

| Dimension | Weight | Distinction (85–100%) | Competent Pass (70–84%) | Incomplete / Resubmit (<70%) |
|---|---:|---|---|---|
| **D1. Functional Correctness (Working System & Tests)** | **20%** | Integrated cross-track product (App UI/API + Hybrid RAG + MCP Agent + Edge/Offline mode) works end-to-end; automated `pytest` unit/integration suite passes $\ge 85\%$; each team member has traceable module commits. | Integrated product works across core user journeys; automated tests pass $\ge 75\%$; verified individual code commits for every learner. | Broken integration, mocked core features, failing tests, or learners with zero meaningful code commits. |
| **D2. Architecture & Code Quality** | **15%** | Clean mono-repo contract boundaries (`Pydantic v2`, `MCP`), provider-independent model routing, resilient error/fallback handling, production-grade Git history and code reviews. | Modular architecture with clear service contracts, typed schemas, and clean repository structure. | Tightly coupled spaghetti code, hardcoded vendor keys, or missing schema validation. |
| **D3. AI Output Quality & Evaluation Report (CD-01, CD-04)** | **20%** | Comprehensive **AI System Evaluation Report** on $\ge 30$ end-to-end + adversarial test cases; compares baseline Alpha vs final Release Candidate; includes hybrid retrieval comparison (CD-04) and correlated OpenTelemetry `gen_ai.*` trace root-cause analysis. | Complete **AI System Evaluation Report** ($\ge 30$ cases) with baseline vs final quality metrics, trace inspection examples, and failure analysis. | Missing Evaluation Report, $<30$ test cases, no baseline comparison, or absent trace evidence. |
| **D4. Security Verification & Reliability (CD-02, CD-03)** | **15%** | Complete **OWASP AISVS 1.0 Security Verification Report** covering all applicable chapters (`C2–C10, C12`), architecture threat model, cross-team red-team test logs with verified code patches, NDPA 2023 compliance, and mandatory non-certification disclaimer. | Complete AISVS 1.0 verification checklist for core + track chapters, documented adversarial tests and remediations, NDPA privacy controls, and non-certification disclaimer. | Missing AISVS report, unpatched critical prompt-injection/ACL/MCP vulnerabilities, raw PII leakage, or false certification claims. |
| **D5. Performance, Resource & Edge Analysis (CD-05)** | **10%** | End-to-end latency waterfall ($p_{50}/p_{95}$, `TTFT`), token/cost budget analysis, and reproducible **Edge AI Benchmark / Resource Profile** proving operation within 8 GB–16 GB RAM constraints. | Reports end-to-end latency, token costs, memory usage, and local/edge execution metrics. | No latency, memory, or cost measurements; crashes with OOM on target hardware. |
| **D6. Documentation, Runbook & Reproducibility** | **10%** | Complete architecture diagram, setup instructions, environment/dependency lockfiles (`Docker` + offline manifest), operational runbook, and honest **Limitations & Known Risks Register**. | Complete setup guide, architecture diagram, dependency lockfiles, and documented limitations; builds cleanly from clone. | Missing setup/architecture docs, undocumented dependencies, or fails clean-room build check. |
| **D7. Live Demonstration & Individual Technical Defence** | **10%** | Seamless 15-min team demo (live trace + failover/offline mode) AND learner answers all code, evaluation, and AISVS security questions accurately during their **15-min Individual Oral Defence**. | Working team demo AND learner satisfactorily explains their owned module, evaluation metrics, and security controls in the Individual Oral Defence. | Demo fails to run OR learner cannot explain their own committed code, metrics, or security controls. |

---

## 7. Technical Defence Guide (15-Minute Individual Oral Defence Protocol)

To guarantee that no learner hides behind a 10-person capstone team (Principle 3, OQ-02), every learner completes a **recorded 15-minute Individual Oral Technical Defence** in Week 14 before a 2-assessor panel (1 Lead Track Instructor + 1 Senior Mentor):

1. **Minutes 0–3 — Individual Module & Commit Walkthrough:**
   - The panel opens the learner's GitHub commit log and asks the learner to trace a specific function, `Pydantic` schema, `MCP` tool handler, retrieval ranker, or quantisation script they authored, explaining *why* it was designed that way and what happens if an upstream dependency fails.
2. **Minutes 3–7 — Live Modification or Trace Diagnosis Exercise:**
   - The panel points to one recorded OpenTelemetry `gen_ai.*` trace or evaluation failure in the team's `AI_System_Evaluation_Report.md` and asks the learner to diagnose the span latency or failure mode and state the exact code change required to fix or mitigate it.
3. **Minutes 7–11 — Specialist Track Deep-Dive (CD-03 / CD-04 / CD-05 / Gateway):**
   - *Track 1 (App Eng):* Explain gateway failover thresholds, SSE backpressure, or token-bucket rate limiting (`LLM10`).
   - *Track 2 (RAG — CD-04):* Explain why `RRF` ($k=60$) improved or changed rankings over `BM25` and `Dense` on a specific query in their test set, and how metadata ACL pushdown prevents cross-tenant leakage (`AISVS C8`).
   - *Track 3 (Agentic — CD-03):* Explain the JSON-RPC flow of their `MCP` server, how `destructiveHint` / HITL interrupts work, and how they prevented confused-deputy / indirect prompt injection (`AISVS C9/C10`).
   - *Track 4 (Edge — CD-05):* Explain the RAM/KV-cache math and `TTFT`/quality trade-off between Configuration A and Configuration B in their benchmark report, and how offline delta sync handles reconnection.
4. **Minutes 11–15 — OWASP AISVS 1.0 Security & Limitations Questioning (CD-02):**
   - The learner explains one threat from their `OWASP_AISVS_Security_Verification_Report.md`, demonstrates the test case verifying its mitigation, and states one residual limitation of the system.

---

## 8. Moderation, Late Submission, and Reassessment Policy Draft

1. **Internal Calibration & Double-Marking:**
   - Before grading Gate 1 (Week 4), Gate 3 (Week 10), and Gate 4 (Week 14), all instructors and mentors calibrate by independently grading 2 benchmark submissions and resolving any scoring variance $>5\%$.
   - Every Gate 3 and Gate 4 submission scoring `<70%` (borderline fail) or `>=90%` (high distinction), plus a random `20%` sample of all submissions, is second-marked by the Programme Director or Lead Assessment Architect.
2. **Power & Connectivity Grace Window (Nigerian Context Resilience):**
   - Standard weekly GitHub PR deadlines include an automatic **24-hour asynchronous grace window** without penalty when a learner logs a power/ISP outage notification via SMS/low-bandwidth community check-in prior to the deadline.
3. **Structured Reassessment (One Guided Remediation Attempt):**
   - Engineering competence is iterative. A learner who scores below the pass threshold on Gate 1 (`<65%`), Gate 3 (`<70%`), or Gate 4 (`<70%`) receives a written **Technical Remediation Action Plan** specifying the exact failing rubric dimensions and test cases, and is granted **one reassessment submission within 7 days** (capped at the threshold pass score of `65%` for Gate 1 or `70%` for Gates 3–4).
   - Cases involving suspected academic dishonesty or fabricated benchmark/evaluation logs are routed to the Academic Integrity Policy (`09_ADMINISTRATION/Policy_Manual.md`).

---

## Change log

| Version | Date | Change |
|---|---|---|
| 0.1 | 2026-11-16 | Created in Stage 6 covering the assessment framework, 7-dimension weighting, rubrics, defence guide, and moderation policy. |
