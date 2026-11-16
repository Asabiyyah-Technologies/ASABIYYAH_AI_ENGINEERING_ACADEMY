# TRACK 1: AI APPLICATION ENGINEERING — CURRICULUM, SYLLABUS AND WEEKLY LESSON PLANS (WEEKS 5–10)
## Asabiyyah Technologies Global Applied AI Engineering Masterclass

| Field | Value |
|---|---|
| Document ID | ASB-AAE-001 |
| Version | 0.2 Draft (Stage 4 Curriculum + Stage 5 Expanded Lesson Plans) |
| Status | Draft – pending management review |
| Owner (role) | Track 1 Lead Instructor — AI Application Engineering (TBC) |
| Last updated | 2026-11-16 |
| Parent document | [MASTER_PROGRAMME_BLUEPRINT.md](../../MASTER_PROGRAMME_BLUEPRINT.md) §12.1 |
| Related decisions | AD-01, AD-02, CD-01, CD-02, PD-03, PD-04, PD-05, GD-02 |
| Stage of origin | Stage 4 (Specialisation Curriculum) and Stage 5 (Weekly Lesson Plans) |

---

## 1. Track overview and target engineering role

- **Track Focus:** Engineering complete, resilient, provider-independent AI web applications and backend services that operate reliably under real-world traffic, latency, cost, and security constraints.
- **Target Engineering Role:** *Applied AI Application Engineer / Full-Stack AI Systems Engineer / Backend GenAI Engineer.*
- **Prerequisites:** Successful completion of the Common Core (Weeks 1–4) and passing Gate 1 ($\ge 65\%$).

---

## 2. Competency framework and learning outcomes (`SC-AAE`)

| Outcome ID | Measurable Learning Outcome | Bloom Level | Mapped Competencies | Assessment Verification |
|---|---|---|---|---|
| **AAE-LO-1** | Design and implement a multi-provider LLM gateway with circuit breakers, exponential backoff, semantic/exact caching, and automatic failover between local (`Ollama`) and remote APIs. | Apply / Create | `CC-03`, `CC-05`, `SC-AAE` | Week 5 Lab PR & failover integration test |
| **AAE-LO-2** | Enforce complex nested structured outputs, multi-turn conversation state compression, and deterministic tool/function execution behind asynchronous `FastAPI` endpoints. | Apply / Analyse | `CC-01`, `CC-05`, `SC-AAE` | Week 6 Lab PR & schema validation suite |
| **AAE-LO-3** | Build a responsive streaming user interface (`Server-Sent Events` / WebSockets + lightweight frontend) with real-time token streaming, cancellation, citation/artifact rendering, and graceful degradation on slow 3G/edge links. | Apply / Create | `CC-03`, `SC-AAE` | Week 7 Streaming UI & low-bandwidth test |
| **AAE-LO-4** | Secure the application with JWT/role-based access control (RBAC), per-user token/cost rate limiting (mitigating OWASP LLM10:2025 Unbounded Consumption), PII redaction (NDPA 2023), and OWASP AISVS 1.0 C2/C4/C5/C7 controls (CD-02). | Analyse / Evaluate | `CC-07`, `SC-AAE` | Week 8 Security Hardening & AISVS audit |
| **AAE-LO-5** | Instrument full-stack OpenTelemetry GenAI traces, build a CI regression evaluation pipeline (`pytest` + `Promptfoo` / `Arize Phoenix`), containerise the service (`Docker`), and deliver a production-ready AI application with documented limitations (CD-01). | Evaluate / Create | `CC-06`, `CC-08`, `CC-09`, `SC-AAE` | Weeks 9–10 Specialist Project & Evaluation Report (Gate 3) |

---

## 3. Tools, technical requirements, and low-cost accessibility

- **Primary Stack:** Python 3.11+, `FastAPI`, `Pydantic v2`, `httpx`, `SQLite` (with WAL mode for local state, semantic cache, and token ledger), `Server-Sent Events (SSE)`, `HTMX` or lightweight React/Streamlit frontend, `pytest`, `Docker`, `Arize Phoenix` / OpenTelemetry, and `Ollama` (`qwen2.5:1.5b` / `llama3.2:3b`) `[SRC-006, SRC-015, SRC-018, SRC-020]`.
- **Zero-Cost / Constrained Hardware Design:** All caching, rate-limiting, and conversation state persistence use embedded `SQLite` (zero external Redis/Postgres server required on 8 GB laptops). Multi-provider failover is tested locally by simulating primary endpoint failures between two local `Ollama` model profiles or a local mock server and a free-tier remote endpoint.

---

## 4. Six-week workload allocation (Weeks 5–10)

Per **PD-03** (`12–15 hours/week`, `72–90 hours total`):

| Week | Title | Live Instructor-Led | Guided Labs | Independent Study | Project Dev & Assessment | Weekly Total |
|---|---|---|---|---|---|---|
| **Week 5** | Multi-Provider Gateway, Failover Routing & Caching | 4.0 h | 3.0 h | 2.5 h | 4.0 h | **13.5 h** |
| **Week 6** | Advanced Structured Outputs, Function Calling & State Management | 4.0 h | 3.0 h | 2.5 h | 4.0 h | **13.5 h** |
| **Week 7** | Real-Time Streaming (`SSE`), UX Resilience & Frontend Integration | 4.0 h | 3.0 h | 2.5 h | 4.0 h | **13.5 h** |
| **Week 8** | Auth, Token Rate Limiting (LLM10), Security (AISVS) & NDPA Privacy | 4.0 h | 3.0 h | 2.5 h | 4.0 h | **13.5 h** |
| **Week 9** | Full-Stack Observability, CI Evaluation Pipelines & Regression Testing | 4.0 h | 3.0 h | 2.5 h | 4.5 h | **14.0 h** |
| **Week 10** | Containerisation, Production Readiness & Specialist Project Defence | 4.0 h | 3.0 h | 2.0 h | 5.0 h | **14.0 h** |
| **Total** | **Track 1 Specialisation (6 Weeks)** | **24.0 h** | **18.0 h** | **14.5 h** | **25.5 h** | **82.0 h** *(within 72–90 h)* |

---

## 5. Detailed Weekly Syllabus and Stage 5 Instructor Lesson Plans (Weeks 5–10)

### WEEK 5: Multi-Provider Gateway, Failover Routing & Caching Architecture
- **Time:** 13.5 h (`4.0 h` Live | `3.0 h` Lab | `2.5 h` Independent | `4.0 h` Project)
- **Learning Objectives:** Implement a provider-independent routing gateway with health checks, circuit breakers, exact + embedding-similarity caching, and token cost accounting.
- **Instructor-Led Content & Demos (4.0 h):**
  - *Session 5A (2.0 h):* **Explain** gateway patterns (primary/secondary failover, timeout cascades, idempotency keys). **Demonstrate** building a `ResilientModelGateway` that detects HTTP `429`/`503` or timeout $>4\text{s}$ on a primary provider and fails over transparently to local `Ollama`.
  - *Session 5B (2.0 h):* **Explain** exact-hash caching vs cosine-similarity semantic caching in SQLite. **Demonstrate** cutting repeat query latency from `1,800 ms` to `12 ms` and logging cache-hit metrics.
- **Guided Practical Lab (3.0 h):** *Lab AAE-05 — Failover & Cache Gateway:* Build and test a 2-tier model gateway with fault injection (`pytest` chaos fixture simulating 30% upstream failures) achieving 99.5% successful response completion.
- **Independent Study & Project Work (6.5 h):** Read OWASP AISVS C4/C12 resilience guidelines `[SRC-001]`; implement the gateway layer for the Track 1 Specialist Project.
- **Deliverable:** `GitHub PR #5` — Multi-provider gateway with SQLite cache and chaos test suite.
- **Common Learner Difficulties & Prep Notes:** *Issue:* Caching user-specific responses across different tenants (data leakage). *Fix:* Enforce composite cache keys `(tenant_id, model_id, prompt_hash)`.

### WEEK 6: Advanced Structured Outputs, Function Calling & Conversation State Management
- **Time:** 13.5 h (`4.0 h` Live | `3.0 h` Lab | `2.5 h` Independent | `4.0 h` Project)
- **Learning Objectives:** Design hierarchical `Pydantic v2` output schemas, deterministic single/parallel tool calling, and sliding-window + summary conversation memory that respects strict context-window token budgets.
- **Instructor-Led Content & Demos (4.0 h):**
  - *Session 6A (2.0 h):* **Explain** grammar-constrained decoding vs tool-call schemas. **Demonstrate** extracting complex multi-item invoices/medical intake records with confidence flags and automatic repair loops.
  - *Session 6B (2.0 h):* **Explain** context window exhaustion and conversation state management. **Demonstrate** a SQLite-backed conversation store using token counting + rolling summarisation to keep context under `2,048` tokens on 8 GB laptops.
- **Guided Practical Lab (3.0 h):** *Lab AAE-06 — Stateful Function-Calling Service:* Implement a multi-turn financial/operations assistant API that calls 3 typed Python tools (currency/tariff lookup, fee calculator, ticket creator) and persists bounded session history.
- **Independent Study & Project Work (6.5 h):** Implement conversation memory and structured tool handlers in the Track 1 Specialist Project.
- **Deliverable:** `GitHub PR #6` — Stateful tool-calling backend with context-window budget enforcement.
- **Common Learner Difficulties & Prep Notes:** *Issue:* Tool arguments hallucinated by smaller 1.5B–3B models. *Fix:* Keep tool parameter schemas flat, use explicit `Literal`/`Enum` types, and return clear validation error messages to the retry loop.

### WEEK 7: Real-Time Streaming (`SSE`), UX Resilience & Low-Bandwidth Frontend Integration
- **Time:** 13.5 h (`4.0 h` Live | `3.0 h` Lab | `2.5 h` Independent | `4.0 h` Project)
- **Learning Objectives:** Implement asynchronous token and status streaming via `Server-Sent Events (SSE)`, client-side stream cancellation, structured partial UI updates, and offline/slow-network request queuing.
- **Instructor-Led Content & Demos (4.0 h):**
  - *Session 7A (2.0 h):* **Explain** why `SSE` over HTTP is simpler and more firewall-friendly than WebSockets for LLM streaming. **Demonstrate** `FastAPI` `StreamingResponse` yielding typed JSON event frames (`token`, `tool_status`, `validation_complete`, `error`).
  - *Session 7B (2.0 h):* **Explain** perceived latency (Time-to-First-Token `TTFT`) and low-bandwidth UI design. **Demonstrate** a lightweight `HTMX`/vanilla-JS web interface that renders streaming tokens, allows user abort (`AbortController`), and gracefully recovers from dropped connections.
- **Guided Practical Lab (3.0 h):** *Lab AAE-07 — Streaming AI Web Interface:* Add an `SSE` streaming endpoint and lightweight frontend to the Week 6 backend, measuring `TTFT` and total completion time under simulated 3G throttling.
- **Independent Study & Project Work (6.5 h):** Build the user-facing frontend and streaming pipeline for the Specialist Project.
- **Deliverable:** `GitHub PR #7` — End-to-end streaming UI + `TTFT` latency benchmark.
- **Common Learner Difficulties & Prep Notes:** *Issue:* Validating structured JSON while streaming raw tokens. *Fix:* Teach dual-mode UX—stream status events/markdown to the user while validating structured JSON payloads on complete chunks before committing state.

### WEEK 8: Authentication, Token Rate Limiting (LLM10), AISVS Security (CD-02) & NDPA Privacy
- **Time:** 13.5 h (`4.0 h` Live | `3.0 h` Lab | `2.5 h` Independent | `4.0 h` Project)
- **Learning Objectives:** Implement JWT/API-key authentication, RBAC, token-bucket rate limiting per user/tenant (OWASP LLM10:2025), input/output sanitisation (AISVS C2, C5, C7), and NDPA 2023 PII protection `[SRC-001, SRC-002, SRC-007]`.
- **Instructor-Led Content & Demos (4.0 h):**
  - *Session 8A (2.0 h):* **Explain** OWASP LLM10:2025 (Unbounded Consumption) and AISVS C5 (Access Control). **Demonstrate** building a token-budget middleware in `FastAPI` that enforces daily input/output token quotas per user and rejects oversized prompts before inference.
  - *Session 8B (2.0 h):* **Explain** AISVS C2 (Input Validation), C7 (Output Control — preventing XSS/Markdown injection in streamed UIs), and NDPA 2023 s.24/s.37. **Demonstrate** red-teaming the web app with `Promptfoo` adversarial test cases `[SRC-021]`.
- **Guided Practical Lab (3.0 h):** *Lab AAE-08 — Hardening & Quota Enforcement:* Add RBAC, per-user token budgets, output HTML sanitisation, and PII redaction to the streaming web app; run a 15-case adversarial security suite.
- **Independent Study & Project Work (6.5 h):** Complete the AISVS 1.0 security controls matrix (C2, C4, C5, C6, C7, C12) for the Track 1 Specialist Project.
- **Deliverable:** `GitHub PR #8` — Security middleware + automated red-team test results.
- **Common Learner Difficulties & Prep Notes:** *Issue:* Counting tokens only *after* generation finishes, allowing attackers to exhaust CPU/API quota. *Fix:* Enforce pre-request character/token estimation caps and `max_tokens` generation ceilings on every call.

### WEEK 9: Full-Stack Observability (CD-01), CI Evaluation Pipelines & Regression Testing
- **Time:** 14.0 h (`4.0 h` Live | `3.0 h` Lab | `2.5 h` Independent | `4.5 h` Project)
- **Learning Objectives:** Instrument end-to-end OpenTelemetry GenAI traces across API, cache, tool calls, and model providers; build an automated CI evaluation gate that fails builds when quality drops or $p_{95}$ latency exceeds budget (CD-01) `[SRC-006, SRC-020]`.
- **Instructor-Led Content & Demos (4.0 h):**
  - *Session 9A (2.0 h):* **Explain** multi-span trace correlation (propagating `trace_id` from frontend request through gateway, cache, and LLM call) and user feedback collection (thumbs up/down linked to `span_id`). **Demonstrate** live trace debugging in `Arize Phoenix`.
  - *Session 9B (2.0 h):* **Explain** regression evaluation in CI/CD. **Demonstrate** configuring a 30-case golden evaluation suite (`evals/`) that computes task accuracy, schema pass rate, cache hit rate, $p_{50}/p_{95}$ latency, and cost per 1,000 requests.
- **Guided Practical Lab (3.0 h):** *Lab AAE-09 — CI Evaluation & Trace Correlation:* Wire end-to-end OpenTelemetry tracing and build the automated regression evaluation script for the Specialist Project.
- **Independent Study & Project Work (7.0 h):** Execute full evaluation runs across $\ge 30$ test cases; perform failure analysis on all failing/high-latency traces and document fixes.
- **Deliverable:** `GitHub PR #9` — 30-case evaluation suite, OpenTelemetry trace export, and baseline vs improved metrics table.
- **Common Learner Difficulties & Prep Notes:** *Issue:* Running slow LLM evaluations on every unit-test commit. *Fix:* Separate fast deterministic `pytest -m unit` checks (using recorded fixtures) from `pytest -m eval` golden dataset runs.

### WEEK 10: Containerisation, Production Readiness & Track 1 Specialist Project Delivery
- **Time:** 14.0 h (`4.0 h` Live | `3.0 h` Lab | `2.0 h` Independent | `5.0 h` Project)
- **Learning Objectives:** Package the application in a multi-stage `Dockerfile`, write an operational runbook and architecture decision records (ADRs), finalise the AI System Evaluation & AISVS Security Report, and defend the Track 1 Specialist Project (Gate 3).
- **Instructor-Led Content & Demos (4.0 h):**
  - *Session 10A (2.0 h):* **Explain** production readiness checklists (container security, non-root Docker users, environment secret injection, graceful shutdown, health/readiness probes). **Demonstrate** `docker compose` packaging of the `FastAPI` app + local `Ollama` link.
  - *Session 10B (2.0 h):* **Demonstrate** live Specialist Project presentations, code walkthroughs, and preparation for Week 11 cross-functional capstone integration (defining the API contracts Track 1 engineers will expose to RAG, Agent, and Edge teammates).
- **Guided Practical Lab (3.0 h):** *Lab AAE-10 — Container Build & Clean-Room Verification:* Build and test the containerised project from a clean clone, verifying reproducible startup and evaluation execution.
- **Project Deliverable (Gate 3 — Track 1 Specialist Project Package):**
  1. Complete **Production AI Web Application Repository** (multi-provider gateway, SQLite state/cache, streaming UI, RBAC & token quotas, `Dockerfile`, $\ge 80\%$ test coverage).
  2. **Track 1 AI System Evaluation & Security Report** (30-item dataset results, $p_{50}/p_{95}$ latency, token cost analysis, trace failure taxonomy, AISVS C2/C4/C5/C6/C7/C12 verification table with non-certification disclaimer).
- **Assessment Rubric (Gate 3 — 25% of Programme Grade):**
  - *Gateway Resilience, Caching & State Management:* 25%
  - *Streaming UX, API Design & Code Quality:* 25%
  - *Evaluation Dataset, Metrics & OpenTelemetry Tracing (CD-01):* 25%
  - *Security Controls (RBAC, LLM10 Quotas, AISVS Profile — CD-02) & Container Reproducibility:* 25%

---

## 6. Curated free learning resources (Track 1)

1. **FastAPI Advanced User Guide (Streaming, Middleware, Security)** — https://fastapi.tiangolo.com/advanced/ `[SRC-018]`
2. **OpenTelemetry GenAI Semantic Conventions Repository** — https://github.com/open-telemetry/semantic-conventions-genai `[SRC-006]`
3. **Arize Phoenix Open-Source Tracing & Evaluation Docs** — https://docs.arize.com/phoenix `[SRC-020]`
4. **Promptfoo Open-Source Evaluation & Red-Teaming Guide** — https://www.promptfoo.dev/docs/intro/ `[SRC-021]`
5. **OWASP AISVS 1.0 (Chapters C2, C4, C5, C7, C12)** — https://owasp.org/www-project-artificial-intelligence-security-verification-standard/ `[SRC-001]`

---

## Change log

| Version | Date | Change |
|---|---|---|
| 0.1 | 2026-11-16 | Track 1 curriculum drafted (Stage 4). |
| 0.2 | 2026-11-16 | Integrated full Stage 5 weekly lesson plans, labs, and Gate 3 rubric (GD-02b). |
