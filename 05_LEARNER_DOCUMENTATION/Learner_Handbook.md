# LEARNER HANDBOOK
## Asabiyyah Technologies Global Applied AI Engineering Masterclass

| Field | Value |
|---|---|
| Document ID | ASB-LRN-001 |
| Version | 0.1 Draft |
| Status | Draft – pending management review |
| Owner (role) | Head of Learner Experience & Programme Director (TBC) |
| Last updated | 2026-11-16 |
| Parent document | [MASTER_PROGRAMME_BLUEPRINT.md](../MASTER_PROGRAMME_BLUEPRINT.md) |
| Related decisions | AD-01–03, CD-01–05, PD-03–05, PR-01–09 |
| Stage of origin | Stage 7 |

---

## 1. Welcome and Programme Introduction

Welcome to the **Asabiyyah Technologies Global Applied AI Engineering Masterclass**.

Over the next 14 weeks, you will train as an **Applied AI Systems Engineer**. You will not merely write chat prompts or watch slides—you will design, code, test, evaluate, secure, document, and defend working AI software systems that solve real problems.

## 2. About Asabiyyah Technologies Ltd

**Asabiyyah Technologies Ltd** is a technology and engineering organisation committed to building high-impact software capabilities and training globally competitive engineers across Nigeria, Africa, and international markets. Our educational mission is grounded in technical rigor, engineering honesty, and practical accessibility.

## 3. Programme Philosophy

**One Foundation. Multiple Specialisations. Real-World AI Products.**

We treat AI models as powerful but fallible software components. Every system you build in this programme must be:
- **Engineered cleanly** in typed Python (`FastAPI`, `Pydantic v2`, `pytest`, Git).
- **Provider-independent and constraint-resilient**, running locally on CPU via quantised open-weight models (`Ollama` / `llama.cpp` `GGUF`) or switching cleanly to free-tier APIs.
- **Quantitatively evaluated and observable** (`CD-01`).
- **Security-verified and privacy-compliant** referencing **OWASP AISVS 1.0** (`CD-02`) and the **Nigeria Data Protection Act (NDPA) 2023**.

## 4. Programme Objectives

By completing this programme, you will learn how to:
1. Build production-structured Python APIs and provider-independent LLM integrations.
2. Specialise deeply in one of four engineering tracks (`AI Application Engineering`, `RAG & Knowledge Engineering`, `Agentic AI Engineering`, or `Edge & Offline AI Engineering`).
3. Measure system quality using golden evaluation datasets and OpenTelemetry traces (`CD-01`).
4. Verify security controls against OWASP AISVS 1.0 (`CD-02`) and protect personal data under NDPA 2023.
5. Collaborate inside a cross-functional engineering team to ship and orally defend a complete capstone product.

## 5. Programme Architecture (14-Week Baseline)

| Phase | Weeks | Structure & Grouping | Weekly Hours |
|---|---|---|---|
| *Optional Preparatory Pathway* | *Weeks -2 to 0* | *Self-paced Python, Git, CLI, HTTP JSON & SQLite readiness* | *10–15 h total* |
| **Phase 1: Common Core** | **Weeks 1–4** | Shared foundation for all 50 learners + 8 Mentor Pods (6–7 learners/pod) | 12–15 h/week (`48–60 h`) |
| **Phase 2: Specialisation Track** | **Weeks 5–10** | You study **ONE** selected track in single-track mentor pods | 12–15 h/week (`72–90 h`) |
| **Phase 3: Integration & Product Eng.** | **Weeks 11–12** | 5 Cross-Functional Product Teams (~10 learners combining all 4 tracks) | 12–15 h/week (`24–30 h`) |
| **Phase 4: Production & Capstone** | **Weeks 13–14** | Hardening, Evaluation Report, AISVS Security Verification & Oral Defence | 12–15 h/week (`24–30 h`) |

## 6. The Common Core (Weeks 1–4)

Every learner completes Weeks 1–4 together (`02_COMMON_CORE/`):
- **Week 1:** Production Python 3.11+, `Pydantic v2`, asynchronous `FastAPI`, `pytest`, and Git PR workflows.
- **Week 2:** LLM mechanics, local CPU inference (`Ollama`), building a `ModelProviderAdapter`, and structured JSON outputs.
- **Week 3:** 3-layer application architecture, building a 15-item Golden Evaluation Dataset, and OpenTelemetry GenAI tracing (`CD-01`).
- **Week 4:** Threat modelling with OWASP LLM Top 10 (2025) & OWASP AISVS 1.0 (`C2`, `C7`), NDPA 2023 PII redaction (`CD-02`), Common Core Mini-App delivery, and the **Gate 1 Specialisation Readiness Assessment**.

## 7. The Four Active Specialisation Tracks (Weeks 5–10)

During Weeks 5–10, you specialise in **one** track:
1. **Track 1 — AI Application Engineering:** Multi-provider failover gateways, SQLite exact/semantic caching, stateful tool calling, real-time `SSE` streaming UIs, RBAC, token-bucket rate limiting (`LLM10`), and CI evaluation pipelines.
2. **Track 2 — RAG & Knowledge Engineering (`CD-04`):** Document parsing, structure-aware chunking, `BM25` lexical search, dense embeddings (`sentence-transformers`), `Qdrant`/`Chroma`, **Hybrid Retrieval with Reciprocal Rank Fusion (`RRF`)**, cross-encoder reranking, query transformation, metadata ACL filtering (`AISVS C8`), and a mandatory **4-Way Comparative Retrieval Evaluation Report**.
3. **Track 3 — Agentic AI Engineering (`CD-03`):** Pure Python ReAct loops, `LangGraph` stateful orchestration with SQLite checkpointing and Human-in-the-Loop approval gates, practical **Model Context Protocol (`MCP`)** server and client implementation (`Tools`, `Resources`, `Prompts`, OAuth 2.1 permissions, `2026-07-28` stateless discovery), and `AISVS C9 & C10` sandboxing.
4. **Track 4 — Edge & Offline AI Engineering (`CD-05`):** Open-weight SLMs, `GGUF` quantisation (`Q4_K_M`, `Q8_0`), KV-cache and CPU thread tuning in `llama.cpp`/`Ollama`, embedded offline SQLite RAG, delta sync under intermittent connectivity, `SHA-256` supply-chain checks (`AISVS C3 & C6`), and a mandatory **Reproducible Edge AI Benchmark Report** comparing $\ge 2$ configurations on your hardware.

*(Note: **Machine Learning Engineering** is a future expansion concept only (`AD-03`) and is not part of initial cohort delivery.)*

## 8. Track Selection and Prerequisites

- **Entry Baseline (`PD-04`):** Elementary Python proficiency (variables, loops, functions, dicts/lists), basic command-line and Git familiarity, basic algebra/statistics reasoning, and a development laptop. Prior AI/ML experience is **not** required.
- **How Track Placement Works:** In Week 4, you submit your Track Preference Form and complete Gate 1. Track placement balances your first/second preference, your Week 4 readiness strengths, and cohort balance (~10–15 learners per track) so Week 11 product teams have all four specialisations represented.

## 9. Programme Learning Outcomes (`PLO-1` to `PLO-5`)

Upon graduating, you will be able to:
- **PLO-1:** Build modular, typed, provider-independent AI backend components with automated tests.
- **PLO-2:** Deliver a working specialist system in your chosen track.
- **PLO-3 (`CD-01`):** Design golden evaluation datasets, inspect OpenTelemetry traces, and author an **AI System Evaluation Report**.
- **PLO-4 (`CD-02`):** Threat-model AI systems, verify controls against **OWASP AISVS 1.0** and **NDPA 2023**, and document residual risks honestly.
- **PLO-5:** Integrate specialist modules inside a cross-functional team and pass an individual 15-minute oral technical defence.

## 10. Learning Methodology

Every week follows a structured six-step engineering cycle:
**Explain → Demonstrate → Guided Lab Practice → Independent Exercises → GitHub PR Assessment → Reflection.**

## 11. Learning Schedule and Weekly Workload (`PD-03`)

Expect a consistent part-time commitment of **12 to 15 hours per week** (`~192 hours` across 14 weeks):
- **Live Instructor-Led Sessions:** `4.0 hours/week` (two 2-hour interactive code-along sessions).
- **Guided Practical Labs:** `3.0 hours/week` (hands-on lab with live mentor troubleshooting).
- **Independent Study & Exercises:** `1.5–2.5 hours/week` (readings, trace diagnosis, edge-case exercises).
- **Project Development & Assessment:** `3.5–5.0 hours/week` (weekly GitHub PR deliverables and report writing).

## 12. Technical Requirements and Low-Bandwidth Accessibility (`PD-04`, `PR-06`)

You do **not** need a dedicated GPU or any paid commercial API subscription.

| Requirement | Minimum Baseline Specification | Recommended Specification |
|---|---|---|
| **Processor (CPU)** | 64-bit x86_64 or ARM64, **4 physical cores** | 6–8+ physical cores (Intel i5/i7 11th Gen+, Ryzen 5000+, Apple M-series) |
| **Memory (RAM)** | **8 GB RAM** (runs 0.5B–3B `Q4_K_M` GGUF models locally) | **16 GB+ RAM** (runs 3B–8B `Q4_K_M` GGUF models locally) |
| **Storage** | **25 GB free SSD space** | **50 GB+ free NVMe SSD space** |
| **GPU / Paid APIs** | **None required** (100% CPU-compatible + free-tier adapter fallback) | Optional integrated/discrete GPU |
| **Connectivity** | Intermittent broadband/3G/4G sufficient to download weekly manifests | Stable broadband |

**Power & Bandwidth Resilience:**
- **Pre-Week Download Manifests:** Model weights (`1–2 GB` once) and libraries are announced 48 hours early so you can download them during off-peak data bundles and complete labs **100% offline**.
- **Low-Bandwidth Session Packs:** Every live session is published as compressed video, an `<60 MB` audio-only recording, and downloadable Markdown notes/code.

## 13. Recommended Open-Source Software Stack

All required software is free and open-source:
- **OS:** Windows 10/11 (with PowerShell / WSL2), Linux (Ubuntu 22.04+), or macOS.
- **Core Tools:** Python 3.11+, `uv` or `venv` + `pip`, Git & GitHub account, VS Code (or equivalent editor), `Docker Desktop` / `Docker Engine` (where supported by RAM).
- **Libraries & Engines:** `FastAPI`, `Pydantic v2`, `httpx`, `pytest`, `SQLite`, `Ollama`, `llama.cpp`, `sentence-transformers`, `rank-bm25`, `Qdrant` (local disk mode), `LangGraph`, `mcp` Python SDK, `Arize Phoenix` / `Promptfoo`.

## 14. Learning Resources

All compulsory readings, documentation links, and datasets are free and listed in each syllabus and in the **Technical Resource Library** (`08_PROJECTS_AND_RESOURCES/`).

## 15. Practical Laboratory Expectations

- Every weekly lab is submitted via a **GitHub Pull Request** containing working code, passing `pytest` tests, and required metrics.
- Your code must run from a clean virtual environment without hardcoded file paths (`C:\Users\YourName\...`) or committed `.env` API keys.

## 16. Project and Capstone Requirements

During Weeks 11–14, your 10-person cross-functional product team builds an integrated AI product. To pass Gate 4, your team and you individually must deliver:
1. Working GitHub repository with your traceable individual module commits.
2. **AI System Evaluation Report (`CD-01`)** on a $\ge 30$-case dataset with OpenTelemetry trace analysis.
3. **OWASP AISVS 1.0 Security Verification Report (`CD-02`)** with adversarial test results and mandatory non-certification disclaimer.
4. Architecture diagram, setup guide, and offline/container runbook.
5. **15-minute Individual Oral Technical Defence** where you explain your code, evaluation metrics, and security controls.

## 17. Assessment and Grading (`04_ASSESSMENT/`)

Your overall programme score is weighted across four gates:
- **Gate 1 — Common Core & Readiness Assessment (Week 4):** `20%` (min pass `65%`)
- **Gate 2 — Weekly Specialisation Labs (Weeks 5–9):** `20%` (min `5 of 6` labs passed at $\ge 65\%$)
- **Gate 3 — Track Specialist Project & Empirical Report (Week 10):** `25%` (min pass `70%`)
- **Gate 4 — Capstone Package & Individual Oral Defence (Week 14):** `35%` (min pass `70%` on both team package and individual defence)

Every project is graded across the 7 standard engineering dimensions: Functional Correctness (`20%`), Architecture & Code Quality (`15%`), AI Output Quality & Evaluation (`20%`), Security & Reliability (`15%`), Performance & Cost (`10%`), Documentation & Reproducibility (`10%`), and Demonstration & Technical Defence (`10%`).

## 18. Attendance, Participation and Outage Grace Policy

- You are expected to maintain **$\ge 75\%$ engagement** across live sessions and mentor pod check-ins.
- **Electricity & Connectivity Protection:** If a power cut or ISP outage prevents live attendance, log an outage notice via the low-bandwidth check-in form/SMS, review the downloadable session pack, and push your lab PR within the automatic **24-hour grace window**—this counts fully toward your participation requirement without penalty.

## 19. Academic Integrity

- You are 100% accountable for every line of code and every metric you submit.
- Using AI coding assistants is permitted **only** if disclosed in your PR description (`AI-Assistance-Disclosure`), and you must be able to explain and modify every line of your code live during mentor reviews and your Week 14 Oral Defence.
- Fabricating evaluation scores, falsifying benchmark logs, or copying another learner's repository without attribution is a serious academic integrity violation (`09_ADMINISTRATION/Policy_Manual.md`).

## 20. Responsible AI Use

Never use programme tools to build deceptive systems, bypass safety controls outside authorised red-team labs, process unconsented personal data, or present probabilistic LLM outputs as infallible professional medical/legal/financial advice without human oversight (`NDPA 2023 s.37`).

## 21. Data Protection and Privacy (`NDPA 2023`)

- **Your Personal Data:** Asabiyyah Technologies Ltd processes learner registration and assessment records in accordance with the **Nigeria Data Protection Act (NDPA) 2023** (`09_ADMINISTRATION/Policy_Manual.md` — *flagged for legal review*).
- **Data in Your Projects:** Never upload real third-party personal data (real customer NINs, BVNs, patient records, or private company files) into repositories or remote APIs. Always use synthetic datasets and PII redaction filters.

## 22. Learner Code of Conduct

Treat fellow learners, mentors, and facilitators with professional respect across all live sessions, GitHub code reviews, and community channels. Harassment, discrimination, or disruptive conduct is governed by the Code of Conduct (`09_ADMINISTRATION/Policy_Manual.md`).

## 23. Mentorship and Support

- **Weeks 1–10:** You belong to a **6–7 learner Mentor Pod** that meets weekly for code review, lab debugging, and career/technical guidance.
- **Weeks 11–14:** Your 10-person Capstone Team is co-supervised by specialist mentors.

## 24. Complaints, Mitigating Circumstances and Appeals

- If you experience illness, bereavement, or prolonged infrastructure disruption, submit a **Mitigating Circumstances Request** to your Mentor and Programme Operations Lead.
- You may request a formal grade review or appeal within **7 calendar days** of receiving a Gate result under the Assessment & Academic Appeals Policy (`09_ADMINISTRATION/Policy_Manual.md`).

## 25. Certification Requirements (`PR-01`)

- **Award:** Graduates who pass all four assessment gates (overall weighted average $\ge 70\%$), submit all mandatory evaluation/security/benchmark reports (`CD-01` to `CD-05`), pass the Individual Oral Technical Defence, and meet the $\ge 75\%$ engagement threshold receive the **Certificate of Completion in Applied AI Engineering (with named Specialisation Track)** issued by **Asabiyyah Technologies Ltd**.
- **Important Notice:** This certificate is an industry training credential issued by Asabiyyah Technologies Ltd. It is **not** a university degree, statutory professional licence, or externally accredited qualification, and does not guarantee employment.

---

## 26. Frequently Asked Questions (FAQ)

1. **My laptop only has 8 GB of RAM and no NVIDIA GPU. Can I complete the programme?**
   *Yes.* Every core lab and even Track 4 (Edge AI) is tested on an 8 GB CPU-only baseline using compact quantised models (`Qwen2.5-1.5B-Instruct Q4_K_M` ~1.0 GB RAM) and our `ModelProviderAdapter` fallback.
2. **What happens if NEPA/power or my internet drops during a live session or deadline?**
   *You will not be penalised.* Download the `<60 MB` audio/Markdown session pack when power returns and use the automatic 24-hour outage grace window for GitHub PR submissions.
3. **Can I study more than one specialisation track in Weeks 5–10?**
   *You enroll in and are assessed on ONE primary track during Weeks 5–10 so you achieve real engineering depth.* However, you retain read access to all four track repositories and work alongside specialists from the other three tracks in your Week 11–14 Capstone Team.
4. **Who owns the Intellectual Property (IP) of my Capstone Project?**
   *Under our proposed IP Policy (`PR-02`, subject to legal review), learners retain default ownership of their original code, granting Asabiyyah Technologies Ltd a non-exclusive licence to showcase the project with attribution.*
5. **Does completing the OWASP AISVS 1.0 checklist mean my capstone is "OWASP Certified"?**
   *No (`CD-02`).* OWASP does not certify student projects. You use AISVS 1.0 as an engineering verification standard and must include the mandatory non-certification disclaimer in your report.

---

## 27. Appendices: Learner Checklists and Progress Guide

### Appendix A: Learner Onboarding Checklist (Complete Before Week 1 Day 1)
- [ ] Complete registration form and review the Learner Code of Conduct & Privacy Notice.
- [ ] Complete the 45-minute **Pre-Cohort Diagnostic** (`ASB-CC-002`). *(If `<70%`, complete Modules Prep 1–4 of the Preparatory Pathway.)*
- [ ] Configure GitHub account with SSH/PAT authentication and join the cohort GitHub organisation.
- [ ] Join your assigned 6–7 learner **Mentor Pod** channel and introduce yourself.
- [ ] Download the **Week 1–2 Offline Asset Manifest** (`Python 3.11+`, `Ollama`, `qwen2.5:1.5b` GGUF model).

### Appendix B: Learner Technical Readiness Verification Checklist
Run the following self-check commands in your terminal (`PowerShell` or `bash`) and confirm all pass:
- [ ] `python --version` $\rightarrow$ Returns `Python 3.11.x` or `3.12.x`.
- [ ] `git --version` $\rightarrow$ Returns `git version 2.x+`.
- [ ] `ollama --version` & `ollama run qwen2.5:1.5b "Reply with READY"` $\rightarrow$ Responds locally with network disconnected.
- [ ] Free SSD disk space $\ge 25\text{ GB}$ and available system RAM $\ge 8\text{ GB}$.
- [ ] `pytest` runs and passes inside a clean virtual environment (`python -m venv .venv`).

### Appendix C: 14-Week Learner Progress and Completion Tracker
| Milestone | Target Week | Required Artefact | Status (`[ ]`) |
|---|---|---|---|
| **Gate 1: Common Core & Readiness** | End of Week 4 | W4 Mini-App Repo + 20-Case Eval & AISVS C2/C7 Report + Readiness Test ($\ge 65\%$) | `[ ]` |
| **Track Selection Confirmed** | End of Week 4 | Assigned to Track 1 (`AAE`), Track 2 (`RAG`), Track 3 (`AGT`), or Track 4 (`EDG`) | `[ ]` |
| **Gate 2: Weekly Track Labs** | Weeks 5–9 | At least 5 of 6 weekly specialist GitHub PRs approved by Track Mentor | `[ ]` |
| **Gate 3: Specialist Project & Report** | End of Week 10 | Working Specialist Repo + Mandatory Track Report (`CD-03`/`04`/`05`) ($\ge 70\%$) | `[ ]` |
| **Capstone Alpha Integration** | End of Week 12 | Cross-functional 10-person team Alpha + 30-case dataset + unified traces | `[ ]` |
| **Gate 4: Capstone & Oral Defence** | End of Week 14 | Final Repo + Eval Report (`CD-01`) + AISVS Report (`CD-02`) + 15-min Individual Defence ($\ge 70\%$) | `[ ]` |

---

## Change log

| Version | Date | Change |
|---|---|---|
| 0.1 | 2026-11-16 | Created in Stage 7 covering all 27 required Learner Handbook sections and checklists. |
