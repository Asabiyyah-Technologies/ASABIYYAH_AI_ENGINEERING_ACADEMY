# MANDATORY EVALUATION, SECURITY AND BENCHMARK REPORT TEMPLATES (CD-01 TO CD-05)
## Asabiyyah Technologies Global Applied AI Engineering Masterclass

| Field | Value |
|---|---|
| Document ID | ASB-ASM-002 |
| Version | 0.1 Draft |
| Status | Draft – pending management review |
| Owner (role) | Lead Assessment Architect (TBC) |
| Last updated | 2026-11-16 |
| Parent document | [Assessment_Framework_and_Rubrics.md](Assessment_Framework_and_Rubrics.md) |
| Related decisions | CD-01, CD-02, CD-03, CD-04, CD-05 |
| Stage of origin | Stage 6 |

> **Usage instruction:** Learners copy the relevant Markdown template below into their project repository (`docs/`) for Gate 1 (Week 4), Gate 3 (Week 10), and Gate 4 (Week 14 Capstone). Every section must be populated with reproducible empirical data and linked to runnable scripts in `evals/` or `security/`.

---

## TEMPLATE 1: AI System Evaluation Report Template (Mandatory for All Capstones & Track Projects — CD-01)

```markdown
# AI SYSTEM EVALUATION REPORT (CD-01)
**Project Title:** [Name]  |  **Repository Commit SHA:** [git rev-parse HEAD]
**Team / Learner Name(s):** [Names & Track Roles]  |  **Date:** [YYYY-MM-DD]

## 1. System Under Test & Evaluation Objectives
- **System Purpose & Target User Workflow:** [1-paragraph summary]
- **Model(s) & Provider Configuration Tested:** [e.g., Local Ollama `qwen2.5:1.5b-instruct-q4_K_M` vs Fallback API; temperature, max_tokens]
- **Reproduction Command:** `python -m evals.run_eval --dataset evals/golden_dataset.jsonl --output evals/results.json`

## 2. Evaluation Dataset Design
- **Total Test Cases:** [Minimum 15 for Core; 25–35+ for Track/Capstone]
- **Dataset Composition Breakdown:**
  | Category | Case Count | Description & Ground-Truth Source |
  |---|---:|---|
  | Standard Functional Cases | [e.g., 15] | Representative domain inputs with verified ground-truth outputs |
  | Edge & Boundary Cases | [e.g., 6] | Long inputs, missing fields, ambiguous queries, unanswerable/abstention cases |
  | Nigerian / Multilingual Context | [e.g., 5] | Nigerian Pidgin, local entity names, regulatory/currency formats |
  | Adversarial & Safety Probes | [e.g., 5] | Direct/indirect prompt injection, PII leakage probes, schema-breaking inputs |

## 3. Baseline vs Final Quantitative Scorecard
| Metric | Baseline (v0.1 Alpha) | Final Release (v1.0 RC) | Delta | Target Threshold | Pass/Fail |
|---|---:|---:|---:|---:|---|
| Task Accuracy / Groundedness (%) | [%] | [%] | [+/- %] | >= 80% | [Pass/Fail] |
| Schema Validity Rate (`Pydantic` %) | [%] | [%] | [+/- %] | >= 98% | [Pass/Fail] |
| Abstention / Refusal Accuracy (%) | [%] | [%] | [+/- %] | >= 90% | [Pass/Fail] |
| Latency p50 / p95 (ms) | [p50 / p95] | [p50 / p95] | [ms] | <= [budget] ms | [Pass/Fail] |
| Time-to-First-Token `TTFT` p50 (ms) | [ms] | [ms] | [ms] | <= [budget] ms | [Pass/Fail] |
| Avg Input / Output Tokens per Call | [in / out] | [in / out] | [tokens] | <= [budget] | [Pass/Fail] |
| Estimated Cost per 1,000 Requests ($) | [$0.00 local / $X API] | [$] | [$] | <= $[budget] | [Pass/Fail] |

## 4. OpenTelemetry Trace Inspection & Failure Taxonomy (`gen_ai.*`)
- **Telemetry Backend Used:** [Arize Phoenix local / OpenTelemetry JSONL span exporter]
- **Observed Failure Modes Breakdown:**
  | Failure Category | Count (Baseline -> Final) | Example `trace_id` / `span_id` | Root Cause Identified in Trace | Engineering Mitigation Applied |
  |---|---|---|---|---|
  | Schema / JSON Formatting Error | [e.g., 4 -> 0] | `[trace_id]` | Model wrapped JSON in markdown fences | Added constrained decoding + 1-step validator retry |
  | Retrieval Miss / Wrong Context | [e.g., 5 -> 1] | `[trace_id]` | Exact section code missed by dense search | Enabled Hybrid BM25 + Dense + RRF (k=60) |
  | Tool / Timeout Error | [e.g., 2 -> 0] | `[trace_id]` | Upstream timeout at 5,000ms | Added circuit breaker + local fallback |

## 5. Documented System Limitations & Operational Boundaries
1. **Known Input Limitations:** [Where accuracy degrades—e.g., scanned handwritten PDFs, >4,096 context tokens on 8GB RAM]
2. **Monitoring & Drift Triggers:** [What runtime metrics trigger human review]
```

---

## TEMPLATE 2: OWASP AISVS 1.0 Proportionate Security Verification Checklist & Report (Mandatory — CD-02)

```markdown
# OWASP AISVS 1.0 SECURITY VERIFICATION REPORT (CD-02)
**Project Title:** [Name]  |  **Commit SHA:** [SHA]  |  **Date:** [YYYY-MM-DD]

> **MANDATORY NON-CERTIFICATION DISCLAIMER (CD-02):**
> This report documents an internal, risk-proportionate engineering assessment referencing selected controls from the **OWASP Artificial Intelligence Security Verification Standard (AISVS) Version 1.0 (June 2026)** and the **OWASP Top 10 for LLM Applications (2025)**. Completion of this verification checklist is for educational and engineering quality assurance only; it **does not** constitute formal certification, accreditation, compliance endorsement, or an independent third-party security audit.

## 1. Architecture Threat Model & Trust Boundaries
- **Data Flow & Trust Boundaries:** [Link or embed diagram showing User -> API -> Orchestrator -> MCP Server -> Vector Store -> Local/Remote LLM]
- **High-Value Assets & Sensitive Data (NDPA 2023 Screening):**
  - Processes Personal Data under Nigeria Data Protection Act (NDPA) 2023? [Yes/No — specify categories: names, phone, NIN/BVN, health/financial records]
  - Triggers NDPA s.28 DPIA or s.37 Automated Decision Safeguards? [Explain human-in-the-loop controls]

## 2. Proportionate OWASP AISVS 1.0 Control Verification Matrix
| AISVS 1.0 Chapter | Verification Requirement | Applicable to Project? | Implementation Evidence (`file:line`) | Verification Test (`pytest` / `promptfoo`) | Status |
|---|---|---|---|---|---|
| **C2: Input Validation** | Structural separation of system instructions and untrusted user/document data; strict length/token caps (LLM01) | **Mandatory (All)** | `[e.g., src/security/input_guard.py:L15-L60]` | `tests/security/test_prompt_injection.py` | [Pass/Remediated] |
| **C4: Infrastructure, Config & Deployment** | Zero hardcoded API keys; `.env` isolation; loopback `127.0.0.1` binding for local inference; non-root container | **Mandatory (All)** | `[Dockerfile:L18; src/config.py]` | `tests/security/test_config_hardening.py` | [Pass/Remediated] |
| **C5: Access Control & Identity** | Authenticated endpoints (JWT/API key); tenant isolation; per-user token/rate quotas (LLM10 Unbounded Consumption) | **Mandatory (All)** | `[src/api/auth.py:L22-L85]` | `tests/security/test_auth_and_quotas.py` | [Pass/Remediated] |
| **C6: Supply Chain Security for Models** | Pinned dependency lockfile; verified model provenance & SHA-256 digests; no unsafe `pickle` weights (LLM03) | **Mandatory (All)** | `[src/edge/manifest_verifier.py]` | `tests/security/test_model_sha256.py` | [Pass/Remediated] |
| **C7: Model Behavior, Output Control & Safety** | Strict `Pydantic v2` output validation; HTML/SQL/shell sanitisation before downstream execution (LLM05, LLM07) | **Mandatory (All)** | `[src/schemas/outputs.py]` | `tests/security/test_output_sanitisation.py` | [Pass/Remediated] |
| **C8: Memory, Embeddings & Vector DB Security** | Pre-retrieval metadata ACL filtering; indirect prompt-injection fencing on retrieved chunks (LLM08) | **Mandatory (RAG / Capstone)** | `[src/rag/retriever.py:L44-L92]` | `tests/security/test_cross_tenant_acl.py` | [Pass/N-A] |
| **C9: Orchestration & Agentic Security** | Bounded `max_steps`; loop breakers; mandatory Human-in-the-Loop approval gate for state-mutating actions (LLM06) | **Mandatory (Agentic / Capstone)** | `[src/agent/graph.py:L50-L110]` | `tests/security/test_agent_bounds_hitl.py` | [Pass/N-A] |
| **C10: Model Context Protocol (MCP) Security** | Scoped MCP server permissions; `readOnlyHint`/`destructiveHint` enforcement; path/SQL parameter allowlists; `stderr`-only logging | **Mandatory (Agentic / Capstone)** | `[src/mcp_server/server.py]` | `tests/security/test_mcp_permissions.py` | [Pass/N-A] |
| **C3: Model Lifecycle & Serialization Integrity** | Immutable GGUF/safetensors loading; versioned model config; crash-safe SQLite WAL & encrypted local PII store | **Mandatory (Edge / Capstone)** | `[src/edge/storage.py]` | `tests/security/test_local_encryption.py` | [Pass/N-A] |
| **C12: Monitoring, Logging & Anomaly Detection** | Audit trail of auth/tool/HITL events; opt-in prompt logging with automatic PII redaction (NDPA 2023 s.24) | **Mandatory (All)** | `[src/telemetry/pii_redactor.py]` | `tests/security/test_pii_redaction.py` | [Pass/Remediated] |

## 3. Adversarial Red-Team Testing & Remediation Log
| Attack ID | Attack Vector (OWASP LLM Top 10 / AISVS) | Payload Summary | Initial Result | Code Remediation Applied | Post-Fix Verification |
|---|---|---|---|---|---|
| RT-01 | Direct Prompt Injection / System Prompt Leak (LLM01, LLM07, C2) | `[Summary]` | [Blocked / Vulnerable] | `[Commit SHA & fix]` | PASS |
| RT-02 | Indirect Injection via Poisoned RAG Chunk / MCP Resource (C8, C10) | `[Summary]` | [Blocked / Vulnerable] | `[Commit SHA & fix]` | PASS |
| RT-03 | Cross-Tenant Vector Retrieval Probe (LLM08, C5, C8) | `[Summary]` | [Blocked / Vulnerable] | `[Commit SHA & fix]` | PASS |
| RT-04 | Unauthorized Destructive MCP Tool Call (LLM06, C9, C10) | `[Summary]` | [Blocked / Vulnerable] | `[Commit SHA & fix]` | PASS |
| RT-05 | NDPA 2023 PII Leakage into Logs/Traces (LLM02, C12) | `[Summary]` | [Blocked / Vulnerable] | `[Commit SHA & fix]` | PASS |

## 4. Residual Risks & Known Security Limitations
- [List any remaining architectural risks and operational safeguards required in production]
```

---

## TEMPLATE 3: RAG Comparative Retrieval & Grounding Evaluation Template (Mandatory for Track 2 & RAG Capstones — CD-04)

```markdown
# RAG COMPARATIVE RETRIEVAL & GROUNDING EVALUATION REPORT (CD-04)
**Corpus Summary:** [Doc count, total chunks, chunking strategy, overlap]
**Embedding Model:** `[e.g., BAAI/bge-small-en-v1.5 (384-d)]`  |  **Reranker:** `[e.g., cross-encoder/ms-marco-MiniLM-L-6-v2]`
**RRF Constant:** `k = 60`  |  **Test Dataset Size:** `[N >= 35 queries]` (`evals/rag_eval_dataset.jsonl`)

## 1. Four-Way Comparative Retrieval Benchmark (CD-04 Mandatory Table)
| Retrieval Mode | Recall@3 | Recall@5 | MRR@5 | NDCG@5 | Retrieval p50 Latency (ms) | Retrieval p95 Latency (ms) |
|---|---:|---:|---:|---:|---:|---:|
| **1. Lexical Baseline (`BM25` only)** | [0.XX] | [0.XX] | [0.XX] | [0.XX] | [ms] | [ms] |
| **2. Semantic Baseline (`Dense Vector` only)** | [0.XX] | [0.XX] | [0.XX] | [0.XX] | [ms] | [ms] |
| **3. Hybrid Search (`BM25 + Dense + RRF k=60`)** | [0.XX] | [0.XX] | [0.XX] | [0.XX] | [ms] | [ms] |
| **4. Hybrid + Cross-Encoder Reranking (`Top-15 -> Top-5`)** | [0.XX] | [0.XX] | [0.XX] | [0.XX] | [ms] | [ms] |

## 2. QueryTransformation & End-to-End Grounded Generation Metrics
| Pipeline Configuration | Faithfulness / Groundedness (%) | Answer Relevance (%) | Verbatim Citation Precision (%) | Unanswerable Abstention Accuracy (%) | Cross-Tenant ACL Leak Rate (%) |
|---|---:|---:|---:|---:|---:|
| Dense Baseline (No Rerank) | [%] | [%] | [%] | [%] | 0.0% |
| Hybrid + RRF + Reranker + Query Rewrite | [%] | [%] | [%] | [%] | 0.0% |

## 3. Diagnostic Case Analysis (Where Each Method Succeeded or Failed)
1. **Query where `BM25` beat `Dense`:** `[Query ID & text — e.g., exact statute/SKU match]`
2. **Query where `Dense` beat `BM25`:** `[Query ID & text — e.g., conceptual paraphrase]`
3. **Query where `RRF + Cross-Encoder Reranking` corrected top-1 ranking:** `[Query ID, before/after rank positions, latency cost]`
```

---

## TEMPLATE 4: Agentic AI & MCP Integration Evaluation Template (Mandatory for Track 3 & Agentic Capstones — CD-03)

```markdown
# AGENTIC AI & MCP INTEGRATION EVALUATION REPORT (CD-03)
**Orchestrator:** `[e.g., LangGraph + SqliteSaver]`  |  **MCP SDK & Spec Version:** `[Python mcp SDK; 2025-11-25 / 2026-07-28]`
**Benchmark Scenarios:** `[N >= 25 multi-step scenarios]` (`evals/agent_scenarios.jsonl`)

## 1. MCP Server Capability & Protocol Compliance Inventory (CD-03)
| Primitive Type | Name / URI Template | Annotations (`readOnlyHint` / `destructiveHint`) | Required Auth Scope | Input/Output Schema Validation | HITL Approval Required? |
|---|---|---|---|---|---|
| `Tool` | `[e.g., lookup_account]` | `readOnlyHint=True` | `mcp:tools:read` | `Pydantic v2` strict | No |
| `Tool` | `[e.g., execute_adjustment]` | `destructiveHint=True` | `mcp:tools:write` | `Pydantic v2` strict | **Yes (`interrupt_before`)** |
| `Resource` | `[e.g., policy://{doc_id}]` | Read-only context | `mcp:resources:read` | URI allowlist | No |
| `Prompt` | `[e.g., audit_triage_template]` | Template | `mcp:prompts:read` | Parameter check | No |

## 2. Agent Trajectory & Execution Benchmark Results
| Metric | Measured Result | Target Threshold | Notes / Trace Evidence |
|---|---:|---:|---|
| End-to-End Task Completion Rate (%) | [%] | >= 80% | Across 25 benchmark scenarios |
| Tool Selection Precision / Recall (%) | [% / %] | >= 90% | Correct MCP tool + valid JSON arguments |
| Trajectory Efficiency (`Optimal Steps / Actual Steps`) | [0.XX] | >= 0.80 | Penalises redundant tool loops |
| Loop-Breaker & Timeout Recovery Success (%) | [100%] | 100% | Tested under simulated MCP server timeout/500 error |
| Destructive-Action HITL Gate Compliance (%) | [100%] | 100% | Zero unapproved state mutations |
| Avg Steps / Avg Tokens / p95 Latency per Task | `[steps / tokens / ms]` | Within budget | Logged via OpenTelemetry `gen_ai.agent.*` spans |
```

---

## TEMPLATE 5: Standard Reproducible Edge AI Benchmark Report Template (Mandatory for Track 4 & Edge Capstones — CD-05)

```markdown
# STANDARD EDGE AI BENCHMARK REPORT (CD-05)
**Learner / Team:** [Name]  |  **Date:** [YYYY-MM-DD]  |  **Commit SHA:** [SHA]
**Reproduction Command:** `python -m evals.run_edge_benchmark --config configs/edge_bench.yaml`

## 1. Controlled Host Hardware & Software Environment
| Parameter | Exact Host Specification (Controlled Across All Runs) |
|---|---|
| **CPU Model & Architecture** | `[e.g., Intel Core i5-10210U (x86_64) — 4 Physical Cores / 8 Logical Threads]` |
| **System RAM & Speed** | `[e.g., 8.0 GB DDR4 @ 2667 MHz (4.6 GB available pre-load)]` |
| **GPU / NPU Status** | `[e.g., Integrated Intel UHD only — 100% CPU Inference (`n_gpu_layers=0`)]` |
| **Storage Type** | `[e.g., 256 GB NVMe SSD]` |
| **OS, Runtime & Power State** | `[e.g., Windows 11 / Ubuntu 24.04; llama.cpp build bXXXX / Ollama vX.Y; AC Power plugged in]` |
| **Pinned Benchmark Parameters** | `threads = [4]`, `ctx_size (-c) = 2048`, `temperature = 0.0`, `batch_size = 512`, `Network = Airplane Mode / Disabled` |

## 2. Comparative Model & Quantisation Benchmark Table ($\ge 2$ Configurations on Identical Host — CD-05)
| Benchmark Metric | Configuration A (`[e.g., Qwen2.5-1.5B-Instruct Q4_K_M]`) | Configuration B (`[e.g., Qwen2.5-1.5B-Instruct Q8_0]`) | Configuration C (Optional: `[e.g., Llama-3.2-3B-Instruct Q4_K_M]`) |
|---|---:|---:|---:|
| **GGUF File SHA-256 (first 12 chars)** | `[sha256]` | `[sha256]` | `[sha256]` |
| **Quantisation Scheme & Bits/Weight** | `Q4_K_M (~4.5 bpw)` | `Q8_0 (~8.5 bpw)` | `Q4_K_M (~4.5 bpw)` |
| **Model Disk Footprint (MB)** | `[e.g., 986 MB]` | `[e.g., 1,650 MB]` | `[e.g., 2,020 MB]` |
| **Cold-Start Model Load Time (ms)** | `[ms]` | `[ms]` | `[ms]` |
| **Idle Process RSS Memory Loaded (MB)** | `[MB]` | `[MB]` | `[MB]` |
| **Peak RSS Memory at `-c 2048` (MB)** | `[MB]` | `[MB]` | `[MB]` |
| **Time-to-First-Token `TTFT` p50 / p95 (ms)** | `[p50 / p95 ms]` | `[p50 / p95 ms]` | `[p50 / p95 ms]` |
| **Prompt Processing Speed (`tokens/sec`)** | `[t/s ± std]` | `[t/s ± std]` | `[t/s ± std]` |
| **Token Generation Speed (`tokens/sec`)** | `[t/s ± std]` | `[t/s ± std]` | `[t/s ± std]` |
| **Task Quality Score (25-Item Dataset %)** | `[%]` | `[%]` | `[%]` |
| **JSON Schema Validity Rate (%)** | `[%]` | `[%]` | `[%]` |
| **Offline Verification (Airplane Mode Test)** | `PASS (0 external sockets)` | `PASS (0 external sockets)` | `PASS (0 external sockets)` |
| **10-Min Sustained Run Throughput Drift (%)** | `[e.g., -4.2%]` | `[e.g., -6.1%]` | `[e.g., -8.5%]` |

## 3. Pareto Trade-Off Analysis & Engineering Selection Decision
- **Quality vs Memory/Latency Analysis:** [Explain whether `Q8_0` or the larger `3B` model yielded enough accuracy gain to justify the extra RAM and slower `TTFT` on an 8 GB machine]
- **Selected Production Configuration:** [State which configuration is chosen for 8 GB minimum-spec deployments vs 16 GB deployments and why]
```

---

## Change log

| Version | Date | Change |
|---|---|---|
| 0.1 | 2026-11-16 | Created in Stage 6 providing the five standardised templates required by CD-01 through CD-05. |
