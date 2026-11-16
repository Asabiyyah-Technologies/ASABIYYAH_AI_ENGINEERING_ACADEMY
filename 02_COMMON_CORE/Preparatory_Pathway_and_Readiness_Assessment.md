# PREPARATORY PATHWAY AND SPECIALISATION READINESS ASSESSMENT
## Asabiyyah Technologies Global Applied AI Engineering Masterclass

| Field | Value |
|---|---|
| Document ID | ASB-CC-002 |
| Version | 0.1 Draft |
| Status | Draft – pending management review |
| Owner (role) | Common Core Lead Instructor (TBC) |
| Last updated | 2026-11-16 |
| Parent document | [Common_Core_Curriculum_and_Syllabus.md](Common_Core_Curriculum_and_Syllabus.md) |
| Related decisions | AD-01, PD-04, PR-03 (R-01), OQ-04, OQ-15 |
| Stage of origin | Stage 3 |

---

## PART A: Optional 2-Week Self-Paced Preparatory Pathway (10–15 Hours)

### 1. Purpose and target learners (PD-04)

In accordance with **PD-04** and **PR-03 (R-01)**, the programme adopts an intermediate beginner-friendly entry baseline. Applicants who pass the Pre-Cohort Diagnostic proceed directly to Week 1. Applicants who score below `70%` on the diagnostic—or who want structured refresher practice—complete this **free, self-paced, offline-capable 2-week Preparatory Pathway (`13 hours`)** prior to Day 1 of Week 1.

### 2. Preparatory pathway syllabus (Weeks -2 to 0)

| Module | Topic | Learning Objectives | Practical Exercise (Offline-Capable) | Est. Hours |
|---|---|---|---|---|
| **Prep 1** | **Python 3.11+ Essentials for Systems Engineering** | Master variables, `list`/`dict`/`set` comprehensions, functions, keyword arguments, type hints (`typing`), custom exceptions, and virtual environments (`venv`/`uv`). | Write a typed CLI script `parse_logs.py` that reads a 500-line server log file, filters errors, computes summary counts, and handles corrupt lines gracefully. | **3.5 h** |
| **Prep 2** | **Command Line (CLI) & Git/GitHub Fundamentals** | Navigate directories, manage environment variables (`.env`), initialise a Git repository, create branches, make atomic commits, resolve a simple merge conflict, and open a GitHub Pull Request. | Push `parse_logs.py` on a feature branch `feat/log-parser`, open a PR against `main`, and pass a basic GitHub Actions linter check. | **3.0 h** |
| **Prep 3** | **JSON, HTTP APIs & Asynchronous Basics** | Understand HTTP verbs (`GET`, `POST`), status codes (`200`, `400`, `401`, `429`, `500`), headers, JSON serialisation (`json` module), and making client requests with `httpx`. | Write a client script that queries a provided local mock HTTP server (`mock_server.py`), handles pagination and simulated `429` retries, and saves validated JSON output. | **3.5 h** |
| **Prep 4** | **Data Handling, SQLite & Environment Verification** | Read/write CSV and JSONL datasets, run basic `SELECT`/`INSERT` queries using Python's built-in `sqlite3` module, install `Ollama`, and run the hardware/environment verification script. | Load 100 sample records into SQLite, export a filtered `dataset.jsonl`, and run `python verify_env.py` confirming Python 3.11+, `pytest`, and local disk/RAM readiness. | **3.0 h** |
| **Total** | **Self-Paced Preparatory Pathway** | — | **Complete Prep Portfolio Repo + Verified Local Environment** | **13.0 h** |

### 3. Pre-Cohort Entry Diagnostic (Self-Assessment Gate)

Applicants complete a 45-minute automated diagnostic before Week 1:
1. **Task 1 (Python & Data Structures — 30 pts):** Transform a nested list of dictionaries representing transactions into a deduplicated summary dictionary filtered by status.
2. **Task 2 (Error Handling & File I/O — 25 pts):** Read a `JSONL` file containing 2 malformed lines out of 20, log the line numbers of malformed entries, and return valid records.
3. **Task 3 (HTTP & JSON — 25 pts):** Send a `POST` request with a JSON body and bearer token header using `httpx` or `urllib`, checking status codes.
4. **Task 4 (Git & CLI — 20 pts):** Clone the starter repo, create a branch, run `pytest`, and push commits.

*Routing Rule:* Score $\ge 70/100 \rightarrow$ Cleared for Week 1. Score $< 70/100 \rightarrow$ Automatically enrolled in the 2-week Preparatory Pathway with mentor office-hour support before retaking the diagnostic.

---

## PART B: End-of-Week-4 Specialisation Readiness Assessment & Track Selection Guide

### 1. Purpose of the Week 4 Readiness Assessment

At the end of Week 4 (Common Core), every learner completes the **Specialisation Readiness Assessment** (part of Assessment Gate 1) to verify that they possess the programming, API, evaluation (CD-01), and security (CD-02) competence required for their chosen Week 5–10 Specialisation Track.

### 2. Structure of the Practical Readiness Assessment (90 Minutes, Open-Book / Local Machine)

Learners are given a partially implemented `FastAPI` + `ModelProviderAdapter` micro-repository and must complete four practical engineering tasks offline:

1. **Task A — Schema & Endpoint Fix (25%):** Fix a broken `Pydantic v2` response schema and `FastAPI` route so invalid model outputs are caught and retried once.
2. **Task B — Evaluation Dataset & Metric Runner (25% — CD-01):** Add 5 golden test cases (including 1 edge case and 1 Nigerian multilingual/Pidgin input) and compute exact-match accuracy and $p_{95}$ latency.
3. **Task C — Trace Diagnosis (25% — CD-01):** Inspect a provided `traces.jsonl` file containing 10 recorded OpenTelemetry `gen_ai.*` spans, identify the 2 failing spans (one token-limit truncation, one tool-schema mismatch), and write a 1-paragraph root-cause fix.
4. **Task D — Security & Privacy Patch (25% — CD-02):** Patch an input handler vulnerable to a supplied prompt-injection payload and add regex redaction for Nigerian phone/NIN patterns prior to trace logging (AISVS C2, C7, C12; NDPA 2023).

### 3. Track Selection Matrix (Helping Learners Choose Their Week 5–10 Specialisation)

Each learner selects **one** primary specialisation track for Weeks 5–10 (AD-01, AD-02). To maintain balanced cross-functional capstone teams in Week 11 (PR-04), each track accommodates roughly **10–15 learners** per 50-learner cohort.

| Specialisation Track | Best Suited For Learners Who Want To... | Key Track Mandate | Strongly Recommended Strengths from Common Core |
|---|---|---|---|
| **Track 1: AI Application Engineering** | Build complete, scalable backend/fullstack AI web products with streaming, caching, auth, and multi-provider resilience. | Production AI web application with provider failover & CI eval pipeline. | Strong score on `FastAPI`, async I/O, and API testing (Week 1 & Week 2). |
| **Track 2: RAG & Knowledge Engineering** | Ground AI systems in complex PDFs, policies, and databases with high retrieval accuracy and citations. | **CD-04:** Hybrid retrieval (`BM25` + dense + `RRF` + reranking) benchmarked on a defined test dataset. | Comfort with data structures, SQLite/JSONL processing, and quantitative evaluation metrics (Week 3). |
| **Track 3: Agentic AI Engineering** | Build controlled, tool-using workflows and standardised protocol integrations that act safely on external systems. | **CD-03:** Practical **Model Context Protocol (`MCP`)** server & client integration with AISVS C9/C10 security. | Strong grasp of JSON schemas, state machines, async functions, and security boundaries (Week 2 & Week 4). |
| **Track 4: Edge & Offline AI Engineering** | Optimize open-weight models (`GGUF`, `llama.cpp`, `Ollama`) to run fast and reliably on constrained CPUs and offline devices. | **CD-05:** Reproducible **Edge AI Benchmark Report** comparing $\ge 2$ configurations on identical hardware. | Interest in systems performance, memory/CPU profiling, CLI tooling, and offline persistence (Week 2 & Week 3). |

---

## Change log

| Version | Date | Change |
|---|---|---|
| 0.1 | 2026-11-16 | Created in Stage 3 covering the PD-04 preparatory pathway and Week 4 specialisation readiness gate. |
