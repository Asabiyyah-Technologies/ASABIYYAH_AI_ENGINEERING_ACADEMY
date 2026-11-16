# TRACK 4: EDGE & OFFLINE AI ENGINEERING — CURRICULUM, SYLLABUS AND WEEKLY LESSON PLANS (WEEKS 5–10)
## Asabiyyah Technologies Global Applied AI Engineering Masterclass

| Field | Value |
|---|---|
| Document ID | ASB-EDG-001 |
| Version | 0.2 Draft (Stage 4 Curriculum + Stage 5 Expanded Lesson Plans) |
| Status | Draft – pending management review |
| Owner (role) | Track 4 Lead Instructor — Edge & Offline AI Engineering (TBC) |
| Last updated | 2026-11-16 |
| Parent document | [MASTER_PROGRAMME_BLUEPRINT.md](../../MASTER_PROGRAMME_BLUEPRINT.md) §12.4 |
| Related decisions | AD-01, AD-02, CD-01, CD-02, **CD-05**, PD-03, PD-04, PD-05, GD-02 |
| Stage of origin | Stage 4 (Specialisation Curriculum) and Stage 5 (Weekly Lesson Plans) |

> **Mandatory Curriculum Decision (CD-05):** This track enforces a consistent, reproducible **Edge AI Benchmark Methodology**. Learners measure model quality, latency (`TTFT` and total latency), throughput (`prompt tokens/sec`, `generation tokens/sec`), memory usage (peak `RSS` and KV-cache allocation), model disk footprint, quantisation level, exact hardware configuration, offline behaviour, and sustained reliability. Every learner must compare **at least two distinct model/quantisation configurations under comparable (identical host) conditions** and submit a reproducible **Edge AI Benchmark Report** `[SRC-014, SRC-015]`.

---

## 1. Track overview and target engineering role

- **Track Focus:** Engineering high-efficiency, local-first, and offline-resilient AI systems that execute reliably on resource-constrained CPU/edge hardware and under intermittent electricity and internet connectivity.
- **Target Engineering Role:** *Edge & Local AI Systems Engineer / On-Device & Offline-First AI Engineer / AI Performance & Quantisation Engineer.*
- **Prerequisites:** Common Core completion (Weeks 1–4) and passing Gate 1 ($\ge 65\%$).

---

## 2. Competency framework and learning outcomes (`SC-EDG`)

| Outcome ID | Measurable Learning Outcome | Bloom Level | Mapped Competencies | Assessment Verification |
|---|---|---|---|---|
| **EDG-LO-1** | Select appropriate open-weight model families (0.5B–8B parameters) from Hugging Face, inspect tensor architectures and binary `GGUF` metadata, and execute local inference via `llama.cpp` and `Ollama` `[SRC-014, SRC-015, SRC-016]`. | Apply / Analyse | `CC-04`, `CC-05`, `SC-EDG` | Week 5 Local Engine & GGUF Inspector PR |
| **EDG-LO-2** | Quantise and evaluate models across `GGUF` k-quant precisions (`Q4_K_M`, `Q5_K_M`, `Q8_0`), calculate weight + KV-cache RAM budgets, and tune CPU thread counts, batch sizes, and context caps (`-c`) to eliminate swap thrashing `[SRC-014]`. | Apply / Evaluate | `CC-04`, `SC-EDG` | Week 6 Quantisation & Memory Profiling Lab |
| **EDG-LO-3** | Architect and build an **Offline-First Local AI & Embedded RAG Service** (`llama-server`/`Ollama` + embedded `SQLite FTS5`/`Qdrant` + `ONNX`/`FastEmbed` CPU embeddings) with local write-ahead queues and deterministic conflict-resilient sync when connectivity returns. | Apply / Create | `CC-03`, `CC-05`, `SC-EDG` | Week 7 Offline-First Local RAG & Sync Engine |
| **EDG-LO-4** | Secure local model weights, local inference endpoints, and offline data caches against **OWASP AISVS 1.0 Chapters C3 (Model Lifecycle & Serialization Integrity), C4 (Deployment), C6 (Supply Chain / SHA-256 verification), and C12 (Local Logging)** plus **NDPA 2023** at-rest data protection (CD-02) `[SRC-001, SRC-007]`. | Analyse / Evaluate | `CC-07`, `SC-EDG` | Week 8 Edge Supply-Chain & Offline Security Audit |
| **EDG-LO-5** | Execute the standard **CD-05 Edge AI Benchmark Methodology** comparing $\ge 2$ model/quantisation configurations under identical host conditions and author a fully reproducible **Edge AI Benchmark Report** alongside a packaged Edge AI Product (CD-01, CD-05). | Evaluate / Create | `CC-06`, `CC-08`, `CC-09`, `SC-EDG` | Weeks 9–10 Specialist Project & Reproducible Edge AI Benchmark Report (Gate 3) |

---

## 3. Tools, technical requirements, and low-cost accessibility

- **Primary CPU-First Open-Source Stack:**
  - *Inference Engines:* `llama.cpp` (`llama-cli`, `llama-server`, `llama-bench`, `llama-perplexity`, `llama-quantize`) and `Ollama` `[SRC-014, SRC-015]`.
  - *Compact Open-Weight Reference Models (8 GB RAM Safe):* `Qwen2.5-0.5B-Instruct`, `Qwen2.5-1.5B-Instruct`, `Llama-3.2-1B-Instruct`, `Llama-3.2-3B-Instruct` (weights `0.4 GB – 2.0 GB` at `Q4_K_M`, `0.6 GB – 3.2 GB` at `Q8_0`) `[SRC-014, SRC-016]`. *(16 GB RAM learners may additionally benchmark 7B–8B models.)*
  - *CPU Embeddings & Local Storage:* `FastEmbed` / `ONNX Runtime` (CPU) or `sentence-transformers` (`all-MiniLM-L6-v2`), `SQLite` (WAL mode + `FTS5`), embedded `Qdrant`.
  - *Hardware & Memory Profiling:* `psutil` (Python RSS/CPU profiler), `llama-bench`, and OpenTelemetry local JSONL trace spans `[SRC-006, SRC-014]`.
- **Within-Host Comparability Rule (CD-05):** Because learners own different laptops, benchmark scores are never graded by raw speed across different students. Instead, every learner compares **Configuration A vs Configuration B (and optionally C)** on **their own machine under controlled conditions** (identical OS state, pinned physical thread count, fixed context window `-c 2048`, airplane-mode offline verification, and the same 25-prompt test suite).

---

## 4. Six-week workload allocation (Weeks 5–10)

Per **PD-03** (`12–15 hours/week`, `72–90 hours total`):

| Week | Title | Live Instructor-Led | Guided Labs | Independent Study | Project Dev & Assessment | Weekly Total |
|---|---|---|---|---|---|---|
| **Week 5** | Open-Weight Model Architecture, Hugging Face Ecosystem & `GGUF` / `llama.cpp` Foundations | 4.0 h | 3.0 h | 2.5 h | 4.0 h | **13.5 h** |
| **Week 6** | Quantisation (`Q4_K_M`, `Q5_K_M`, `Q8_0`), KV-Cache Memory Budgeting & CPU Thread Tuning | 4.0 h | 3.0 h | 2.5 h | 4.5 h | **14.0 h** |
| **Week 7** | Local Serving, Embedded Offline RAG & Intermittent-Connectivity Sync Architecture | 4.0 h | 3.0 h | 2.5 h | 4.5 h | **14.0 h** |
| **Week 8** | Edge Supply-Chain Security (AISVS C3 & C6), Safe Serialization & Local Data Protection (CD-02) | 4.0 h | 3.0 h | 2.5 h | 3.5 h | **13.0 h** |
| **Week 9** | Standard Edge AI Benchmarking Methodology & Reproducible Execution (CD-01, CD-05) | 4.0 h | 3.0 h | 2.5 h | 4.5 h | **14.0 h** |
| **Week 10** | Packaging, Crash Recovery, Power-Loss Resilience & Track 4 Specialist Project Delivery | 4.0 h | 3.0 h | 2.0 h | 5.0 h | **14.0 h** |
| **Total** | **Track 4 Specialisation (6 Weeks)** | **24.0 h** | **18.0 h** | **14.5 h** | **26.0 h** | **82.5 h** *(within 72–90 h)* |

---

## 5. Detailed Weekly Syllabus and Stage 5 Instructor Lesson Plans (Weeks 5–10)

### WEEK 5: Open-Weight Models, Hugging Face Ecosystem & `GGUF` / `llama.cpp` Foundations
- **Time:** 13.5 h (`4.0 h` Live | `3.0 h` Lab | `2.5 h` Independent | `4.0 h` Project)
- **Learning Objectives:** Navigate the Hugging Face model ecosystem (licenses, model cards, `safetensors` vs `GGUF`), inspect `GGUF` binary headers (architecture, layer count, vocabulary, attention heads, context length), and run deterministic local inference via both `Ollama` and raw `llama-server` `[SRC-014, SRC-015, SRC-016]`.
- **Instructor-Led Content & Demos (4.0 h):**
  - *Session 5A (2.0 h):* **Explain** small language model (SLM) architectures (`Qwen2.5`, `Llama-3.2`, Grouped-Query Attention `GQA`) and why `GGUF` single-file memory-mapped (`mmap`) weights are ideal for edge/CPU deployment. **Demonstrate** writing a Python script to parse `GGUF` header metadata and verify model licenses.
  - *Session 5B (2.0 h):* **Explain** the architectural relationship between `llama.cpp` and `Ollama`. **Demonstrate** running `llama-server` directly with custom flags (`--ctx-size`, `--threads`, `--parallel`, `--mlock`) and exposing an OpenAI-compatible local endpoint.
- **Guided Practical Lab (3.0 h):** *Lab EDG-05 — GGUF Metadata Inspector & Local Server Runner:* Inspect two `GGUF` files (`1.5B` and `3B`), launch `llama-server` / `Ollama` with constrained context flags, and build a Python health/telemetry wrapper that records hardware specs and model load time.
- **Independent Study & Project Work (6.5 h):** Define the target offline/edge use case (e.g., rural clinic triage assistant, offline agricultural extension advisor, field inspection logger) for the Track 4 Specialist Project.
- **Deliverable:** `GitHub PR #5` — GGUF inspector + configured local inference service wrapper.
- **Common Learner Difficulties & Prep Notes:** *Issue:* Leaving default `num_ctx` unbounded on models supporting 32k–128k context, causing immediate RAM exhaustion on 8 GB laptops. *Fix:* Enforce explicit `-c 2048` or `num_ctx: 2048` in every Modelfile and launch script `[SRC-014]`.

### WEEK 6: Quantisation (`Q4_K_M`, `Q5_K_M`, `Q8_0`), KV-Cache Memory Budgeting & CPU Inference Tuning
- **Time:** 14.0 h (`4.0 h` Live | `3.0 h` Lab | `2.5 h` Independent | `4.5 h` Project)
- **Learning Objectives:** Calculate exact RAM requirements for model weights + KV cache, compare `GGUF` quantisation schemes (`Q4_K_M`, `Q5_K_M`, `Q8_0`), tune CPU physical thread allocation and prompt batching, and measure quality-vs-memory trade-offs `[SRC-014]`.
- **Instructor-Led Content & Demos (4.0 h):**
  - *Session 6A (2.0 h):* **Explain** post-training quantisation mechanics (block-wise k-quants, why `Q4_K_M` uses ~4.5 bits/weight preserving attention/output layers at higher precision) and the memory sizing equation:
    $$\text{Total Inference RAM} = \text{Weight RAM} + \text{KV Cache RAM}(n_{\text{ctx}}, n_{\text{layers}}, d_{\text{kv}}) + \text{Compute Buffer}$$
    **Demonstrate** live memory profiling (`psutil` peak `RSS`) of `Qwen2.5-1.5B` at `Q4_K_M` (`~1.0 GB`) vs `Q8_0` (`~1.65 GB`) and `Llama-3.2-3B` at `Q4_K_M` (`~2.0 GB`) `[SRC-014]`.
  - *Session 6B (2.0 h):* **Explain** CPU memory-bandwidth bottlenecks and why hyperthreading excess degrades token generation speed. **Demonstrate** sweeping thread counts (`-t 2, 4, 6, 8`) with `llama-bench` to find the hardware sweet spot on the instructor's laptop.
- **Guided Practical Lab (3.0 h):** *Lab EDG-06 — Quantisation & Thread Tuning Sweep:* Profile 2 quantisation levels (`Q4_K_M` vs `Q8_0` of the same 1.5B model, or `1.5B Q4_K_M` vs `3B Q4_K_M`) across 3 thread counts and 2 context lengths (`1024` vs `4096`), recording `TTFT`, `tokens/sec`, and peak `RSS`.
- **Independent Study & Project Work (7.0 h):** Select the two candidate model configurations for the Specialist Project and tune their serving parameters.
- **Deliverable:** `GitHub PR #6` — Memory budget calculator + automated thread/quantisation profiling script.
- **Common Learner Difficulties & Prep Notes:** *Issue:* Background browser/IDE processes skewing CPU benchmark numbers. *Fix:* Teach benchmark hygiene—close heavy apps, run 2 warm-up iterations, and record mean $\pm$ standard deviation over 5 measured runs.

### WEEK 7: Local Serving, Embedded Offline RAG & Intermittent-Connectivity Sync Architecture
- **Time:** 14.0 h (`4.0 h` Live | `3.0 h` Lab | `2.5 h` Independent | `4.5 h` Project)
- **Learning Objectives:** Build a 100% offline-capable application combining local LLM inference, ultra-lightweight local RAG (`SQLite FTS5` + CPU `ONNX` embeddings), an offline write-ahead outbox queue, and idempotent synchronisation when network connectivity resumes.
- **Instructor-Led Content & Demos (4.0 h):**
  - *Session 7A (2.0 h):* **Explain** offline-first system architecture for Nigerian field conditions (clinics, farms, schools, logistics depots with intermittent 2G/3G and power cuts). **Demonstrate** building an embedded local RAG pipeline inside a single `SQLite` database file (`FTS5` lexical + serialised 384-dim `MiniLM` vectors) requiring `<150 MB` RAM.
  - *Session 7B (2.0 h):* **Explain** eventual consistency, local outbox queues, UUIDv7/ULID idempotency keys, and conflict resolution when syncing field logs or knowledge base delta updates over spotty connections. **Demonstrate** disconnecting the network interface, executing 5 local AI triage/RAG operations, reconnecting, and syncing deltas cleanly to a central API.
- **Guided Practical Lab (3.0 h):** *Lab EDG-07 — Airplane-Mode AI Service & Delta Sync:* Build a local `FastAPI` service backed by `Ollama`/`llama-server` and `SQLite` that passes an automated integration test while all external network sockets are blocked (`socket` guard fixture), then syncs queued records upon reconnection.
- **Independent Study & Project Work (7.0 h):** Implement the offline-first storage, local RAG/inference pipeline, and sync queue for the Track 4 Specialist Project.
- **Deliverable:** `GitHub PR #7` — Offline-first service passing zero-network `pytest` verification + delta sync engine.
- **Common Learner Difficulties & Prep Notes:** *Issue:* Code silently attempting to reach `huggingface.co` at startup to check model Hub updates and crashing when offline. *Fix:* Enforce `HF_HUB_OFFLINE=1`, `TRANSFORMERS_OFFLINE=1`, and local file paths in all edge configurations.

### WEEK 8: Edge Supply-Chain Security (AISVS C3 & C6), Safe Serialization & Local Data Protection (CD-02)
- **Time:** 13.0 h (`4.0 h` Live | `3.0 h` Lab | `2.5 h` Independent | `3.5 h` Project)
- **Learning Objectives:** Apply **OWASP AISVS 1.0 Chapters C3 (Model Lifecycle & Change Control), C4 (Deployment Security), C6 (Supply Chain Security for Models), and C12 (Logging)** alongside **OWASP LLM03:2025 (Supply Chain)** and **NDPA 2023**: verify cryptographic `SHA-256` model digests, avoid unsafe Python `pickle` weights, bind local inference ports strictly to `127.0.0.1`, and encrypt/protect sensitive local SQLite data `[SRC-001, SRC-002, SRC-007]`.
- **Instructor-Led Content & Demos (4.0 h):**
  - *Session 8A (2.0 h):* **Explain** AI model supply-chain attacks (trojaned `pickle` `.pt`/`.bin` files executing arbitrary code on load vs safe `safetensors`/`GGUF` parsing bugs; tampered model downloads) mapped to **AISVS C3 & C6** `[SRC-001]`. **Demonstrate** building a mandatory `ModelManifestVerifier` that checks `SHA-256` checksums, file signatures, and allowed quantisation metadata before loading any model.
  - *Session 8B (2.0 h):* **Explain** edge device threat models: exposed `0.0.0.0:11434` Ollama ports on shared LANs, unencrypted PII on stolen field laptops (NDPA 2023 s.24/s.28), and prompt injection in compact 1.5B–3B models (which have weaker native safety alignment than 70B models). **Demonstrate** loopback binding, application-layer encryption for sensitive SQLite columns (`cryptography.fernet`), and strict deterministic input/output guardrails around small edge models.
- **Guided Practical Lab (3.0 h):** *Lab EDG-08 — Edge Supply-Chain & Device Hardening:* Add cryptographic `SHA-256` model verification, localhost port verification, encrypted local PII storage, and deterministic input/output validators (AISVS C2, C3, C4, C6, C7, C12) to the offline service.
- **Independent Study & Project Work (6.0 h):** Complete the AISVS security verification controls and adversarial tests for the Track 4 Specialist Project.
- **Deliverable:** `GitHub PR #8` — `ModelManifestVerifier` + encrypted local PII store + AISVS edge security checklist.
- **Common Learner Difficulties & Prep Notes:** *Issue:* Expecting a 1.5B `Q4_K_M` model to refuse clever jailbreaks via system prompt text alone. *Fix:* Compensate for smaller model safety capacity with strict external Python input filters, constrained grammar/JSON decoding, and zero unvalidated command execution.

### WEEK 9: Standard Edge AI Benchmarking Methodology & Reproducible Execution (CD-01, CD-05)
- **Time:** 14.0 h (`4.0 h` Live | `3.0 h` Lab | `2.5 h` Independent | `4.5 h` Project)
- **Learning Objectives:** Execute the mandatory **CD-05 Standard Edge AI Benchmark Methodology** comparing **at least two distinct model/quantisation configurations** under identical host conditions across all 8 required dimensions: (1) task quality on a 25-item evaluation dataset, (2) latency (`TTFT` ms, total response latency $p_{50}/p_{95}$), (3) throughput (`prompt tokens/sec`, `generation tokens/sec`), (4) memory usage (idle `RSS`, peak `RSS`, KV-cache delta), (5) disk footprint (MB), (6) quantisation & context configuration, (7) exact hardware/OS/thermal environment, and (8) offline reliability & cold-start load time `[SRC-014]`.
- **Instructor-Led Content & Demos (4.0 h):**
  - *Session 9A (2.0 h):* **Explain** the **Asabiyyah Standard Edge AI Benchmark Protocol (CD-05)**:
    - Controlled variables: same host machine, AC power vs battery state recorded, pinned thread count, fixed context window (`-c 2048`), `temperature=0.0`, airplane-mode offline state, 2 warm-up prompts + 25 evaluation prompts.
    - **Demonstrate** running the automated benchmark harness (`evals/run_edge_benchmark.py`) comparing Configuration A (`Qwen2.5-1.5B-Instruct-Q4_K_M`) vs Configuration B (`Qwen2.5-1.5B-Instruct-Q8_0` or `Llama-3.2-3B-Instruct-Q4_K_M`).
  - *Session 9B (2.0 h):* **Explain** how to interpret quality-vs-latency Pareto trade-offs and trace failure modes in quantised models (e.g., JSON syntax degradation or arithmetic/entity drops at extreme low bit-widths). **Demonstrate** generating the standardised Markdown & CSV **Edge AI Benchmark Report**.
- **Guided Practical Lab (3.0 h):** *Lab EDG-09 — Full Comparative Edge Benchmark Run (CD-05):* Execute the 25-item benchmark across $\ge 2$ configurations on the learner's machine, export raw JSONL telemetry + `llama-bench` logs, and populate the comparative tables.
- **Independent Study & Project Work (7.0 h):** Complete all benchmark runs (including a 10-minute sustained stress/reliability check and simulated power-loss recovery test) and write the **Reproducible Edge AI Benchmark Report**.
- **Deliverable:** `GitHub PR #9` — Automated benchmark suite (`evals/run_edge_benchmark.py`), raw telemetry logs, and complete draft of the **Edge AI Benchmark Report (CD-05)**.
- **Common Learner Difficulties & Prep Notes:** *Issue:* Thermal throttling on thin laptops during back-to-back runs making the second model appear artificially slower. *Fix:* Include an automated 60-second cooldown pause between configuration sweeps and log start-to-end throughput drift across the 25 prompts.

### WEEK 10: Packaging, Crash/Power-Loss Resilience & Track 4 Specialist Project Delivery
- **Time:** 14.0 h (`4.0 h` Live | `3.0 h` Lab | `2.0 h` Independent | `5.0 h` Project)
- **Learning Objectives:** Package the offline AI application for one-command local installation, verify SQLite WAL crash/power-loss recovery, define how Track 4's local inference/offline sync module integrates with Tracks 1–3 in Week 11, and defend the **Track 4 Specialist Project & Edge AI Benchmark Report** (Gate 3).
- **Instructor-Led Content & Demos (4.0 h):**
  - *Session 10A (2.0 h):* **Explain** sudden power-loss resilience (SQLite `PRAGMA synchronous=NORMAL/FULL` with WAL mode, atomic file writes, automatic service restart scripts) and Week 11 capstone integration (providing the local/offline fallback engine and benchmark suite for the 10-person product team).
  - *Session 10B (2.0 h):* **Demonstrate** Track 4 project defences, live airplane-mode execution checks, and Gate 3 rubric reviews.
- **Guided Practical Lab (3.0 h):** *Lab EDG-10 — Offline Clean-Room & Crash-Recovery Verification:* Verify that the packaged application starts from a local bundle with zero network access, survives an abrupt `kill -9` mid-queue without database corruption, and reproduces benchmark numbers within $\pm 10\%$.
- **Project Deliverable (Gate 3 — Track 4 Specialist Project Package):**
  1. **Offline-First Edge AI Service Repository** (Local `llama.cpp`/`Ollama` runner, `SHA-256` model manifest verifier, embedded `SQLite` RAG + encrypted PII store + offline sync queue, `FastAPI` service, reproducible benchmark scripts, `pytest` offline test suite).
  2. **Reproducible Edge AI Benchmark Report (Mandatory — CD-01, CD-05)** + **AISVS 1.0 Security Verification Section (Chapters C2, C3, C4, C5, C6, C7, C12 — CD-02)**:
     - Complete hardware/OS specification table.
     - Side-by-side comparison of $\ge 2$ model/quantisation configurations under identical conditions covering Task Quality Score (25-item dataset), Schema Validity %, Cold-Start Load Time (s), `TTFT` ($p_{50}/p_{95}$ ms), Prompt Processing (`t/s`), Token Generation (`t/s`), Disk Footprint (MB), Idle & Peak `RSS` Memory (MB), and Offline/Crash Reliability results.
     - Engineering recommendation justifying which configuration is selected for production deployment on 8 GB vs 16 GB target hardware.
- **Assessment Rubric (Gate 3 — 25% of Programme Grade):**
  - *Local Inference Tuning, Memory Budgeting & Offline-First Sync Architecture:* 25%
  - *Reproducible Edge AI Benchmark Methodology & Comparative Report (CD-01, CD-05):* 35%
  - *Zero-Network Execution Verification & Crash/Power-Loss Resilience:* 20%
  - *Edge Supply-Chain & Device Security (AISVS C3, C4, C6 — CD-02) & Code Quality:* 20%

---

## 6. Curated free learning resources (Track 4)

1. **`llama.cpp` Official Repository, GGUF Specification & `llama-bench` Guide** — https://github.com/ggml-org/llama.cpp `[SRC-014]`
2. **Ollama Documentation & Modelfile Reference** — https://github.com/ollama/ollama/tree/main/docs `[SRC-015]`
3. **Hugging Face Guide to Quantisation (GGUF, K-Quants)** — https://huggingface.co/docs/hub/gguf `[SRC-016]`
4. **SQLite Write-Ahead Logging (WAL) & FTS5 Full-Text Search Docs** — https://www.sqlite.org/wal.html ; https://www.sqlite.org/fts5.html `[SRC-022]`
5. **OWASP AISVS 1.0 (Chapter C3: Model Lifecycle; Chapter C6: Supply Chain Security for Models)** `[SRC-001]`

---

## Change log

| Version | Date | Change |
|---|---|---|
| 0.1 | 2026-11-16 | Track 4 curriculum drafted incorporating CD-05 (Stage 4). |
| 0.2 | 2026-11-16 | Integrated full Stage 5 weekly lesson plans, GGUF/llama-bench labs, and Gate 3 rubric (GD-02b). |
