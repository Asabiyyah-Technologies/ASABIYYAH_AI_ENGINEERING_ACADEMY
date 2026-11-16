# COMMON CORE CURRICULUM, SYLLABUS AND WEEKLY LESSON PLANS (WEEKS 1–4)
## Asabiyyah Technologies Global Applied AI Engineering Masterclass

| Field | Value |
|---|---|
| Document ID | ASB-CC-001 |
| Version | 0.2 Draft (Stage 3 Curriculum + Stage 5 Expanded Lesson Plans) |
| Status | Draft – pending management review |
| Owner (role) | Common Core Lead Instructor (TBC) |
| Last updated | 2026-11-16 |
| Parent document | [MASTER_PROGRAMME_BLUEPRINT.md](../MASTER_PROGRAMME_BLUEPRINT.md) §11 |
| Related decisions | AD-01, CD-01, CD-02, PD-03, PD-04, PD-05, GD-02 |
| Stage of origin | Stage 3 (Curriculum & Syllabus) and Stage 5 (Weekly Lesson Plans) |

> **Governance note (GD-02b):** To prevent duplicate source-of-truth files (OQ-12), this authoritative document integrates the Stage 3 Common Core Curriculum and Syllabus with the Stage 5 Weekly Instructor Lesson Plans for Weeks 1–4. Companion documents in this folder provide the **Optional Preparatory Pathway & Readiness Assessment** (`Preparatory_Pathway_and_Readiness_Assessment.md`).

---

## 1. Common Core purpose and design boundaries

The four-week Common Core (`48–60 learner hours`) establishes the shared software, API, model-integration, evaluation (CD-01), and security (CD-02) baseline required to enter any of the four specialisations in Week 5.

- **What the Common Core teaches:** Clean typed Python 3.11+ packaging, `Pydantic v2` schema enforcement, asynchronous `FastAPI` backends, Git/GitHub PR workflows, LLM mechanics, a provider-independent **Model Provider Adapter** (switching cleanly between local `Ollama` GGUF models and free-tier hosted endpoints), deterministic + golden-dataset evaluation (`pytest` + trace logging), and foundational OWASP AISVS 1.0 (C2 Input Validation, C7 Output Control) + NDPA 2023 privacy engineering `[SRC-001, SRC-006, SRC-007, SRC-015, SRC-018]`.
- **What is strictly deferred to Specialisations (Weeks 5–10):** Vector databases, BM25/RRF hybrid search, and cross-encoder reranking (deferred to Track 2 RAG); multi-step state graphs and MCP client/server builds (deferred to Track 3 Agentic); deep GGUF quantisation sweeps and offline sync engines (deferred to Track 4 Edge); full-stack multi-provider caching and RBAC web apps (deferred to Track 1 App Eng).

---

## 2. Common Core learning outcomes and competency mapping

| Outcome ID | Measurable Learning Outcome | Bloom Level | Mapped Blueprint Competency | Verification Method |
|---|---|---|---|---|
| **CC-LO-1** | Package a modular, type-annotated Python 3.11+ service with `Pydantic v2` validation, `FastAPI` endpoints, automated `pytest` tests, and clean Git history. | Apply / Analyse | `CC-01`, `CC-02`, `CC-03`, `CC-08` | Week 1 Lab PR & automated `pytest` suite |
| **CC-LO-2** | Implement a configuration-driven **Model Provider Adapter** that calls both a local quantised model (`Ollama`) and an OpenAI-compatible remote API, enforcing structured JSON schemas, retries, and timeout budgets. | Apply / Create | `CC-04`, `CC-05` | Week 2 Lab PR & schema validation test |
| **CC-LO-3** | Construct a 15-item Golden Evaluation Dataset, execute reproducible quality/latency/token-cost evaluations, and record OpenTelemetry-aligned execution traces (`gen_ai.*`) to diagnose failure modes (CD-01). | Analyse / Evaluate | `CC-06`, `CC-08` | Week 3 Evaluation Harness & Trace Log |
| **CC-LO-4** | Threat-model a foundational AI service against OWASP LLM Top 10 (2025) and OWASP AISVS 1.0 (C2, C7), implement input/output guardrails and NDPA 2023 PII redaction, and pass the Specialisation Readiness Gate (CD-02). | Evaluate / Create | `CC-07`, `CC-09` | Week 4 Mini-Project, Basic Eval & Security Report, Readiness Gate |

---

## 3. Required software, hardware, and low-bandwidth provisions

- **Hardware Baseline:** Minimum 8 GB RAM, 4-core CPU, 25 GB free SSD (runs `qwen2.5:1.5b-instruct-q4_K_M` ~1.0 GB or `llama3.2:3b-instruct-q4_K_M` ~2.0 GB via `Ollama`); 16 GB RAM recommended (runs `llama3.1:8b-instruct-q4_K_M` ~4.8 GB) `[SRC-014, SRC-015]`.
- **Core Open-Source Software Stack:** Python 3.11+, `uv` (or `venv` + `pip`), Git, `FastAPI`, `Uvicorn`, `Pydantic v2`, `httpx`, `pytest`, `Ollama` (local runner), and `Arize Phoenix` (or lightweight JSONL OpenTelemetry span exporter) `[SRC-006, SRC-018, SRC-020]`.
- **Pre-Week Download Manifest (Offline Resilience):** Before Week 2 begins, learners download a single 1.1 GB model weight file (`qwen2.5:1.5b`) and wheel cache during off-peak hours; 100% of Common Core labs execute offline once cached.

---

## 4. Workload summary (Weeks 1–4)

Per **PD-03** (`12–15 hours/week`, `48–60 hours total`; assignments counted inside independent/project hours per OQ-13):

| Week | Title | Live Instructor-Led | Guided Labs | Independent Study & Exercises | Project Dev & Assessment | Weekly Total |
|---|---|---|---|---|---|---|
| **Week 1** | Software Engineering, Typed APIs & Testing for AI | 4.0 h | 3.0 h | 2.5 h | 3.5 h | **13.0 h** |
| **Week 2** | LLM Mechanics, Local Inference & Provider Abstraction | 4.0 h | 3.0 h | 2.5 h | 4.0 h | **13.5 h** |
| **Week 3** | AI Application Architecture, Evaluation & Observability (CD-01) | 4.0 h | 3.0 h | 2.5 h | 4.0 h | **13.5 h** |
| **Week 4** | Foundational AI Security (CD-02), NDPA Privacy & Readiness Gate | 4.0 h | 3.0 h | 2.5 h | 5.0 h | **14.5 h** |
| **Total** | **Common Core (4 Weeks)** | **16.0 h** | **12.0 h** | **10.0 h** | **16.5 h** | **54.5 h** *(within 48–60 h)* |

---

## 5. Detailed Weekly Syllabus and Stage 5 Instructor Lesson Plans

Each week follows the Stage 5 instructional sequence: **Explain → Demonstrate → Guided Practice → Independent Practice → Assessment → Reflection**.

---

### WEEK 1: Software Engineering, Typed APIs & Testing Foundations for AI Systems

- **Estimated Time:** 13.0 hours (`4.0 h` Live | `3.0 h` Guided Lab | `2.5 h` Independent | `3.5 h` Project/Assessment)
- **Learning Objectives:**
  1. Structure a clean Python 3.11+ repository with virtual environments (`uv`/`venv`), `pyproject.toml`, type annotations, and structured logging (`CC-01`).
  2. Enforce nested data contracts using `Pydantic v2` models, custom validators, and explicit error serialisation (`CC-01`, `CC-03`).
  3. Build and test asynchronous `FastAPI` endpoints with dependency injection, health checks, and `pytest` fixtures (`CC-03`, `CC-08`).
  4. Execute collaborative Git workflows (`branch`, atomic `commit`, `Pull Request`, peer code review) (`CC-02`).
- **Topics & Subtopics:**
  - *1.1 Production Python vs Notebooks:* Why untyped notebooks fail in production; package layout (`src/`, `tests/`, `configs/`).
  - *1.2 Data Contracts with Pydantic v2:* `BaseModel`, `Field` constraints, `model_validator`, strict mode, JSON Schema export `[SRC-018]`.
  - *1.3 Async Backend Fundamentals:* Event loops (`asyncio`), non-blocking I/O (`httpx.AsyncClient`), `FastAPI` routing, status codes, and structured error envelopes.
  - *1.4 Automated Testing & Git Discipline:* `pytest`, parameterised tests, mocking external calls, Git feature branches, and PR templates.
- **Instructor-Led Sessions (4.0 h — 2 × 2.0 h):**
  - *Session 1A (2.0 h):* **Explain** why AI engineering is 80% software systems engineering. **Demonstrate** live refactoring of a fragile Jupyter script into a typed Python package with `Pydantic v2` schemas and `pytest`.
  - *Session 1B (2.0 h):* **Explain** async concurrency for I/O-bound model calls. **Demonstrate** building a `FastAPI` service with dependency-injected configuration, request ID middleware, and GitHub PR checks.
- **Guided Practical Lab (3.0 h):**
  - *Lab 01 — Typed Document Intake & Triage API:* Learners build a local `FastAPI` service (`POST /v1/tickets/validate`) that validates messy support tickets (including Nigerian multilingual/Pidgin text samples), normalises fields via `Pydantic v2`, logs structured JSON events, and passes a 10-test `pytest` suite.
- **Independent Study & Exercises (2.5 h):**
  - Read selected sections of FastAPI & Pydantic v2 documentation `[SRC-018]`; complete 5 parameterised `pytest` edge-case exercises (malformed JSON, missing fields, boundary lengths).
- **Project Work & Deliverables (3.5 h):**
  - **Deliverable W1 (`GitHub PR #1`):** Repository scaffold for the **Common Core Mini-Application** (a structured Triage & Summarisation Service) with working `/health` and `/v1/intake` endpoints and $\ge 85\%$ test pass rate.
- **Assessment Method:** Automated `pytest` check + Mentor Pod PR review rubric.
- **Common Learner Difficulties & Mitigations:**
  - *Difficulty:* Confusing `async def` vs blocking `def` in FastAPI or misconfiguring Python `PATH` on Windows.
  - *Mitigation:* Provide a cross-platform `Makefile` / PowerShell runner script (`run.ps1`) and a visual trace showing how blocking calls freeze the event loop.
- **Instructor Preparation Notes:** Verify starter repo runs cleanly on Windows PowerShell and Linux/macOS with zero internet access once wheels are installed.

---

### WEEK 2: LLM Mechanics, Local Inference & Provider-Independent Model Integration

- **Estimated Time:** 13.5 hours (`4.0 h` Live | `3.0 h` Guided Lab | `2.5 h` Independent | `4.0 h` Project/Assessment)
- **Learning Objectives:**
  1. Explain tokenisation (BPE), context-window memory scaling, temperature/top-p sampling, and why autoregressive models confabulate (`CC-04`).
  2. Run a quantised open-weight model locally on CPU via `Ollama` (`qwen2.5:1.5b` or `llama3.2:3b`) and inspect raw HTTP request/response payloads (`CC-04`, `CC-05`).
  3. Design and implement a **Model Provider Adapter** in Python that abstracts local (`Ollama`) and remote OpenAI-compatible APIs behind a single interface (`CC-05`).
  4. Enforce deterministic structured outputs (JSON Schema / Pydantic validation with retry-on-validation-error) and single-step tool/function schemas (`CC-05`).
- **Topics & Subtopics:**
  - *2.1 Inside the LLM Call:* Tokens, prompt templates (system/user/assistant roles), context truncation, sampling determinism (`temperature=0.0`, seeds).
  - *2.2 Local CPU Inference vs Hosted APIs:* How `GGUF` and `Ollama` serve models over `localhost:11434`; latency vs privacy/cost trade-offs `[SRC-014, SRC-015]`.
  - *2.3 The Provider Adapter Pattern:* Designing a `LLMProvider` protocol (`generate_text`, `generate_structured`) with exponential backoff, timeout budgets, and automatic fallback.
  - *2.4 Structured Outputs & Tool Schemas:* Constraining outputs with JSON Schema / grammar sampling; repairing malformed JSON; declaring tool definitions without external agent frameworks.
- **Instructor-Led Sessions (4.0 h — 2 × 2.0 h):**
  - *Session 2A (2.0 h):* **Explain** tokenisation, context limits, and quantisation fundamentals. **Demonstrate** live inspection of token counts, logprobs, and `Ollama` CPU memory consumption on an 8 GB budget.
  - *Session 2B (2.0 h):* **Explain** provider lock-in risks. **Demonstrate** coding a 90-line `ModelProviderAdapter` that switches between `Ollama` and a remote endpoint via `.env` and validates responses into a `Pydantic` model with automatic retry feedback.
- **Guided Practical Lab (3.0 h):**
  - *Lab 02 — Provider-Independent Structured Extractor:* Learners implement `ModelProviderAdapter`, connect it to their Week 1 `FastAPI` service, and extract structured fields (`category`, `urgency`, `entities`, `action_required`) from 20 unstructured customer/citizen messages in offline CPU mode.
- **Independent Study & Exercises (2.5 h):**
  - Compare tokenisation fertility across English, Nigerian Pidgin, Hausa, Yoruba, and Igbo strings; document how higher token-per-word ratios impact context limits and latency.
- **Project Work & Deliverables (4.0 h):**
  - **Deliverable W2 (`GitHub PR #2`):** Integrated `ModelProviderAdapter` + Structured Output Validator in the Common Core Mini-App, including mock-provider unit tests and a live local-model integration test.
- **Assessment Method:** `pytest` validation of adapter interface, retry behaviour on simulated HTTP 429/500, and 100% schema conformance across 10 test inputs.
- **Common Learner Difficulties & Mitigations:**
  - *Difficulty:* Small 1.5B–3B local models occasionally emit markdown fences around JSON or drop required keys.
  - *Mitigation:* Teach explicit JSON-schema constrained decoding (`format` parameter in Ollama / `response_format`) plus a 1-retry validation error-feedback loop.
- **Instructor Preparation Notes:** Distribute the `qwen2.5:1.5b` GGUF download manifest 48 hours before Week 2; prepare a recorded offline response cassette (`pytest-recording` / JSON fixtures) for any learner whose machine is mid-setup.

---

### WEEK 3: AI Application Architecture, Evaluation & Observability (CD-01)

- **Estimated Time:** 13.5 hours (`4.0 h` Live | `3.0 h` Guided Lab | `2.5 h` Independent | `4.0 h` Project/Assessment)
- **Learning Objectives:**
  1. Architect a clean 3-layer AI service (API Layer $\rightarrow$ Domain/Orchestration Layer $\rightarrow$ Model/Storage Adapter Layer) with SQLite persistence (`CC-03`, `CC-05`).
  2. Construct a **Golden Evaluation Dataset** combining normal, edge, multilingual, and adversarial cases with explicit pass/fail criteria (`CC-06` / **CD-01**).
  3. Implement an automated evaluation runner measuring exact/fuzzy match, schema validity rate, latency percentiles ($p_{50}, p_{95}$), and token usage (`CC-06` / **CD-01**).
  4. Instrument LLM calls with **OpenTelemetry GenAI** semantic conventions (`gen_ai.provider.name`, `gen_ai.request.model`, `gen_ai.usage.input_tokens`, `gen_ai.usage.output_tokens`) and inspect traces locally (`CC-06` / **CD-01**) `[SRC-006, SRC-020]`.
- **Topics & Subtopics:**
  - *3.1 Why Traditional Unit Tests Are Not Enough:* Deterministic code tests vs statistical evaluation of non-deterministic outputs.
  - *3.2 Golden Dataset Engineering (CD-01):* Curating representative test cases, ground-truth labels, deterministic assertions (regex, schema, keyword inclusion/exclusion), and when (not) to use LLM-as-a-judge `[SRC-013]`.
  - *3.3 Observability & Tracing (CD-01):* Spans, traces, and metrics; OpenTelemetry GenAI attributes (`open-telemetry/semantic-conventions-genai`, noting its *Development* status and opt-in prompt capture for privacy) `[SRC-006]`.
  - *3.4 Failure Taxonomy & Root-Cause Analysis:* Categorising failures (schema failure, hallucinated entity, wrong classification, timeout, context overflow) from trace logs.
- **Instructor-Led Sessions (4.0 h — 2 × 2.0 h):**
  - *Session 3A (2.0 h):* **Explain** CD-01 evaluation methodology. **Demonstrate** building a 20-case `golden_dataset.jsonl` and a Python evaluation harness that outputs a Markdown scorecard comparing two prompt/model versions.
  - *Session 3B (2.0 h):* **Explain** distributed tracing for AI calls. **Demonstrate** instrumenting `ModelProviderAdapter` with OpenTelemetry spans viewed in local `Arize Phoenix` (and a zero-dependency JSONL trace viewer fallback) `[SRC-020]`.
- **Guided Practical Lab (3.0 h):**
  - *Lab 03 — Evaluation Harness & Trace Inspector:* Learners instrument their Mini-App with telemetry spans, run a 15-item evaluation dataset across two prompt revisions, inspect traces for the 3 slowest/failing cases, and improve task accuracy by $\ge 10\%$ through evidence-based prompt/schema refinement.
- **Independent Study & Exercises (2.5 h):**
  - Read NIST AI 600-1 sections on measurement and confabulation `[SRC-004]`; annotate 5 real trace logs to identify the exact span where a failure originated.
- **Project Work & Deliverables (4.0 h):**
  - **Deliverable W3 (`GitHub PR #3`):** `evals/golden_dataset.jsonl` ($\ge 15$ cases), `evals/run_eval.py`, telemetry instrumentation, and a draft baseline scorecard table.
- **Assessment Method:** Automated execution of `python -m evals.run_eval` producing a valid JSON/Markdown report + verification of emitted `gen_ai.*` trace attributes.
- **Common Learner Difficulties & Mitigations:**
  - *Difficulty:* Writing weak evaluation assertions (e.g., only checking `len(output) > 0`) that pass even when the model hallucinates.
  - *Mitigation:* Require every golden test case to include at least one field-level semantic assertion (exact enum match, ground-truth entity match, or forbidden-term check).
- **Instructor Preparation Notes:** Provide both the `Arize Phoenix` local UI workflow and a 40-line standard-library `trace_summary.py` script so 8 GB RAM laptops never struggle with UI overhead.

---

### WEEK 4: Foundational AI Security (CD-02), NDPA 2023 Privacy & Specialisation Readiness Gate

- **Estimated Time:** 14.5 hours (`4.0 h` Live | `3.0 h` Guided Lab | `2.5 h` Independent | `5.0 h` Project/Assessment)
- **Learning Objectives:**
  1. Map architectural threats using the **OWASP Top 10 for LLM Applications (2025)** and **OWASP AISVS 1.0** foundational chapters (**C2 Input Validation**, **C5 Access Control**, **C7 Output Control & Safety**, **C12 Logging**) (`CC-07` / **CD-02**) `[SRC-001, SRC-002]`.
  2. Implement defensive controls against Direct and Indirect Prompt Injection (LLM01), System Prompt Leakage (LLM07), Improper Output Handling (LLM05), and Unbounded Consumption (LLM10) (`CC-07`).
  3. Apply **Nigeria Data Protection Act (NDPA) 2023** requirements (s.24 data minimisation, s.28 DPIA triggers, s.37 human-intervention safeguards for automated decisions) and build a PII redaction filter before external model calls (`CC-07`) `[SRC-007]`.
  4. Deliver the complete **Common Core Mini-Application**, **Basic AI System Evaluation & Security Report**, and pass the **Specialisation Readiness Assessment** (`CC-01`–`CC-09`).
- **Topics & Subtopics:**
  - *4.1 Threat Modelling AI Applications (CD-02):* Trust boundaries, untrusted user vs untrusted retrieved data, OWASP LLM Top 10 (2025) overview, and how OWASP AISVS 1.0 structures verification requirements `[SRC-001, SRC-002]`.
  - *4.2 Defensive Engineering Controls:* Structural separation of system instructions and untrusted data delimiters; input length/token caps; API key isolation; output sanitisation (preventing XSS/SQLi from model text); rate limiting.
  - *4.3 Privacy & Nigerian Regulatory Context:* NDPA 2023 s.24, s.28, s.37; regex + entity-based PII redaction (Nigerian phone numbers, BVN/NIN patterns, emails) prior to logging or remote API transit `[SRC-007]`.
  - *4.4 Specialisation Track Orientation & Readiness Gate:* Technical preview of Tracks 1–4 and completion of the timed practical readiness check.
- **Instructor-Led Sessions (4.0 h — 2 × 2.0 h):**
  - *Session 4A (2.0 h):* **Explain** OWASP LLM Top 10 (2025) and AISVS 1.0 C2/C7 controls. **Demonstrate** live red-teaming of an unprotected endpoint (prompt injection overriding classification + system prompt extraction) and live patching with structural input fencing, output validation, and rate limits.
  - *Session 4B (2.0 h):* **Explain** NDPA 2023 obligations for AI engineers. **Demonstrate** building a pre-inference PII redaction middleware (masking Nigerian NIN/BVN/phone numbers in prompts and OpenTelemetry traces) and walking through the Gate 1 submission checklist.
- **Guided Practical Lab (3.0 h):**
  - *Lab 04 — Red-Teaming, Hardening & PII Redaction:* Learners add 5 adversarial prompt-injection and PII-leakage test cases to their golden dataset, implement input/output guardrails and NDPA PII masking middleware, and verify that all 5 attacks are blocked or safely handled.
- **Independent Study & Exercises (2.5 h):**
  - Complete the AISVS 1.0 C2/C5/C7/C12 self-check table for the Common Core Mini-App; review the Track Selection Guide (`Preparatory_Pathway_and_Readiness_Assessment.md`).
- **Project Work & Deliverables (5.0 h):**
  - **Deliverable W4 — Gate 1 Common Core Submission Package:**
    1. Complete Common Core Mini-Application repository (`FastAPI` + `ModelProviderAdapter` + `SQLite` + `pytest` + `Dockerfile`).
    2. `Evaluation_and_Security_Report.md` (20-item golden dataset results: 15 functional + 5 adversarial; latency/token table; AISVS C2/C5/C7/C12 checklist with mandatory non-certification disclaimer; NDPA 2023 privacy check).
    3. Completion of the **Specialisation Readiness Assessment**.
- **Assessment Method:** Gate 1 Rubric (20% of overall programme grade; minimum 65% pass standard required to enter Week 5 specialisation).
- **Common Learner Difficulties & Mitigations:**
  - *Difficulty:* Relying solely on "Do not follow user instructions" prompt text to stop prompt injection.
  - *Mitigation:* Demonstrate why prompt-only defences fail and enforce architectural mitigations: strict enum/schema validation on output, zero privileged actions in the classification call, and deterministic post-processing checks.
- **Instructor Preparation Notes:** Prepare the 5-item automated adversarial grading script (`evals/redteam_check.py`) and ensure mentor pods complete Gate 1 grading within 48 hours so learners confirm their Week 5 track placement smoothly.

---

## 6. Gate 1 (Common Core) assessment rubric

| Criterion | Weight | Exemplary (85–100%) | Competent / Pass (65–84%) | Needs Remediation (<65%) |
|---|---|---|---|---|
| **1. Software Architecture, Typing & Tests (`CC-01`, `CC-02`, `CC-03`, `CC-08`)** | **25%** | Clean modular package, strict `Pydantic v2` schemas, async `FastAPI`, $\ge 85\%$ `pytest` coverage, atomic Git PR history. | Working modular `FastAPI` service with `Pydantic` validation and passing unit/integration tests. | Monolithic script/notebook, missing type validation, or failing tests. |
| **2. Provider-Independent Model Adapter (`CC-04`, `CC-05`)** | **25%** | Seamless switch between local `Ollama` and remote API, structured output validation with retry repair, timeout/backoff handling. | Adapter works with local model and validates structured JSON outputs on standard inputs. | Hardcoded vendor SDK, unstructured raw text parsing, or crashes on malformed output. |
| **3. Golden Dataset, Evaluation & Tracing (`CC-06` / CD-01)** | **25%** | $\ge 20$ well-designed test cases, automated scorecard comparing baselines, OpenTelemetry GenAI traces (`gen_ai.*`), clear failure taxonomy. | $\ge 15$ test cases with automated runner, baseline latency/accuracy table, and working trace logs. | Manual "vibe check" screenshots only, $<15$ test cases, or no latency/trace metrics. |
| **4. Foundational Security & NDPA Privacy (`CC-07`, `CC-09` / CD-02)** | **25%** | Passes all 5 adversarial injection tests, masks PII (NIN/BVN/phone/email) before model/trace logging, accurate AISVS C2/C5/C7/C12 checklist + non-certification disclaimer. | Implements input/output validation, PII redaction, and completed AISVS foundational checklist with disclaimer. | Vulnerable to trivial prompt injection, logs raw PII, or omits AISVS security checks. |

---

## 7. Curated free learning resources (Common Core)

1. **FastAPI Official Tutorial & User Guide** — https://fastapi.tiangolo.com/tutorial/ `[SRC-018]`
2. **Pydantic v2 Documentation** — https://docs.pydantic.dev/latest/ `[SRC-018]`
3. **Hugging Face LLM Course (Chapters 1–4, Free)** — https://huggingface.co/learn/llm-course `[SRC-016]`
4. **Ollama Model Library & API Reference** — https://github.com/ollama/ollama/blob/main/docs/api.md `[SRC-015]`
5. **OpenTelemetry GenAI Semantic Conventions** — https://opentelemetry.io/docs/specs/semconv/gen-ai/ `[SRC-006]`
6. **OWASP Top 10 for Large Language Model Applications (2025) & OWASP AISVS 1.0** — https://owasp.org/ `[SRC-001, SRC-002]`
7. **Nigeria Data Protection Act (NDPA) 2023 Full Text (NDPC)** — https://ndpc.gov.ng/ `[SRC-007]`

---

## Change log

| Version | Date | Change |
|---|---|---|
| 0.1 | 2026-11-16 | Initial Common Core curriculum and syllabus drafted (Stage 3). |
| 0.2 | 2026-11-16 | Integrated full Stage 5 weekly instructor lesson plans, demonstrations, labs, and learner difficulty mitigations (GD-02b). |
