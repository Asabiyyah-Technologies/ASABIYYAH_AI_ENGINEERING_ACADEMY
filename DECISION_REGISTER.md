# DECISION REGISTER

| Field | Value |
|---|---|
| Document ID | ASB-GOV-003 |
| Version | 0.1 Draft |
| Status | Under Review |
| Owner (role) | Programme Director (TBC) / Management |
| Last updated | 2026-11-16 |
| Parent document | — (governance root) |
| Stage of origin | Stage 0 |

## Purpose and rules

This register is the authoritative record of **what has been decided**. The [Master Programme Blueprint](MASTER_PROGRAMME_BLUEPRINT.md) must reflect every approved entry.

1. Approved entries are never silently overwritten. A change requires a new entry, and the old entry moves to **Superseded** with a cross-reference.
2. Only management (the user) can approve a decision. Documentation authors record decisions; they do not make them.
3. Proposed recommendations (`PR-`) and assumptions (`AS-`) have **no authority** until approved.
4. ID prefixes: `AD` architecture baseline · `CD` curriculum decision · `PD` programme planning decision · `GD` governance decision · `PR` proposed recommendation · `AS` assumption · `OQ` open question (see [OPEN_QUESTIONS.md](OPEN_QUESTIONS.md)).

---

## A. Management-approved decisions

### A1. Architecture baseline

| ID | Decision | Date | Source | Affects |
|---|---|---|---|---|
| AD-01 | 14-week programme: Common Core Weeks 1–4; **one selected** specialisation Weeks 5–10; Integration & Product Engineering Weeks 11–12; Production Engineering & Capstone Weeks 13–14. Changes to duration, hours, sequencing or track architecture require a documented reason and management approval. | 2026-11-16 | Master Control Prompt §2; Stage 2 prompt | Blueprint; all curricula |
| AD-02 | Four active initial specialisations: (1) AI Application Engineering; (2) RAG & Knowledge Engineering; (3) Agentic AI Engineering; (4) Edge & Offline AI Engineering. | 2026-11-16 | Master Control Prompt §2 | 03_SPECIALISATION_TRACKS |
| AD-03 | Machine Learning Engineering is a **potential future specialisation only**. It may be documented as a concept note. It is not part of the four-track initial delivery. | 2026-11-16 | Master Control Prompt §2 | FUTURE_ML_ENGINEERING |

### A2. Curriculum decisions (approved — not optional)

| ID | Decision | Mandatory evidence | Affects |
|---|---|---|---|
| CD-01 | **Shared AI Evaluation & Observability competency.** All four specialisations develop competence in establishing baselines, constructing evaluation datasets, measuring quality, inspecting traces, analysing failures, monitoring latency and cost, and documenting limitations. | Every capstone includes an **AI System Evaluation Report**. | Common Core; all tracks; 04_ASSESSMENT |
| CD-02 | **OWASP AISVS 1.0 as capstone security reference.** Used for proportionate AI security assessment. Capstones address applicable requirements including threat identification, authentication, authorisation, data protection, prompt injection, tool security, testing and documented remediation. **Using AISVS does not make a project certified, accredited or independently audited, and no such claim may be made.** | AISVS-referenced security assessment in every capstone. | All tracks; 04_ASSESSMENT |
| CD-03 | **MCP implementation in Agentic AI Engineering.** Covers MCP architecture, clients, servers, tools, resources, prompts, tool discovery, invocation, authentication, permissions, error handling, compatibility and secure execution. | Learners build and test an **MCP-enabled integration**. | Agentic AI track |
| CD-04 | **Hybrid retrieval and reranking in RAG & Knowledge Engineering.** Covers BM25, semantic retrieval, hybrid retrieval, Reciprocal Rank Fusion, reranking, query transformation, metadata filtering, source attribution and retrieval evaluation. | Learners **compare retrieval approaches using a defined test dataset**. | RAG track |
| CD-05 | **Standard Edge AI benchmark report.** Consistent methodology measuring model quality, latency, throughput where applicable, memory usage, model footprint, quantisation, hardware configuration, offline behaviour and reliability. | Learners compare **at least two model configurations under comparable conditions** and submit a **reproducible Edge AI Benchmark Report**. | Edge & Offline track |

### A3. Programme planning decisions

| ID | Decision | Date | Affects |
|---|---|---|---|
| PD-01 | Project root `ASABIYYAH_AI_ENGINEERING_ACADEMY/` is created directly inside the current workspace folder; no unnecessary nesting. | 2026-11-16 | Structure |
| PD-02 | The Master Control Prompt and Stage 0–13 prompts are supplied by management, one stage at a time. The prompt architecture is not recreated or rewritten. | 2026-11-16 | Governance |
| PD-03 | Part-time commitment of **12–15 learner hours per week** for 14 weeks (≈168–210 hours). Indicative weekly split: live instructor-led 4 h; guided practical labs 3 h; independent study and exercises 2–3 h; project development and assessment 3–5 h. Every syllabus distinguishes instructor-led, guided, independent and project hours. | 2026-11-16 | All syllabi |
| PD-04 | **Intermediate, beginner-friendly entry baseline:** basic computer literacy; elementary programming (preferably Python) including variables, conditions, loops and functions; basic mathematical reasoning; access to a laptop suitable for software development. Prior AI/ML/RAG/agent experience not required. Optional self-paced **two-week preparatory pathway (≈10–15 h)** covering Python fundamentals, Git/GitHub, command line, APIs and introductory data handling. Dedicated GPUs and paid API subscriptions are **not** mandatory. | 2026-11-16 | Blueprint; admissions; Common Core |
| PD-05 | **Online-first, live instructor-led international cohort.** Maximum first-cohort capacity 50; Nigerian and international participants; 14 weeks; English; approximately five teams of ten; mentorship target one mentor per six to seven learners; live sessions, guided labs, self-paced learning, **GitHub-based practical submissions**, dedicated learner community; recordings where appropriate, downloadable materials and low-bandwidth alternatives. Platform selection deferred to the platform architecture stage. | 2026-11-16 | Delivery; operations |

### A4. Governance decisions

| ID | Decision | Date | Effect |
|---|---|---|---|
| GD-01 | User instruction (2026-11-16): "bypass all the approval gates until you reach the final instruction of the prompt." Stages 0–5 (the prompts supplied to date) are executed sequentially without intermediate stops. **This waives the pause, not the review.** Each stage is recorded as *Completed – pending management review*; no content is marked Approved on management's behalf. Execution stops at the Stage 5 approval gate. | 2026-11-16 | PROGRAMME_STATUS.md |
| GD-02 | Default documentation choices applied under GD-01: (a) each folder contains a short README; (b) Stage 5 expands the Stage 3/4 syllabus and lesson-plan files rather than creating parallel copies (resolves OQ-12 provisionally); (c) PR-01 and PR-02 remain *Proposed*. Management may reverse any of these. | 2026-11-16 | Structure; Stages 3–5 |

---

## B. Proposed recommendations (not approved)

| ID | Recommendation | Raised | Status |
|---|---|---|---|
| PR-01 | Certificate described as a **Certificate of Completion issued by Asabiyyah Technologies Ltd**, subject to approved completion requirements. Not a professional licence, university qualification or externally accredited certificate. | Master Control Prompt §11 ("current proposed certificate") | Proposed — awaiting management confirmation and completion criteria (OQ-10) |
| PR-02 | Learners retain ownership of their own project work by default; Asabiyyah receives a limited, non-exclusive licence to showcase work with attribution and consent. Team-work IP and third-party/client data terms to be defined. | Stage 0 | Proposed — **requires legal review** |

Further `PR-` entries arising from Stages 1–5 are listed in Section B2 as they are produced.

### B2. Recommendations from later stages

| ID | Recommendation | Raised | Status |
|---|---|---|---|
| PR-03 | Establish a 2-week self-paced Preparatory Pathway (`13 h`) and mandatory Pre-Cohort Diagnostic (`>=70%` direct entry; `<70%` routed to Prep Pathway) to protect Common Core pacing (`R-01`, `OQ-04`, `OQ-15`). | Stage 1 & Stage 3 | Proposed — implemented in `ASB-CC-002` pending management review |
| PR-04 | Adopt two-phase cohort grouping: Single-Track Mentor Pods (6–7 learners, 8 pods total) in Weeks 5–10; 5 Cross-Functional Product Teams (~10 learners combining Tracks 1–4) with individual module ownership and 15-min oral defence in Weeks 11–14 (`R-03`, `OQ-01`, `OQ-02`). | Stage 1 & Stage 2 | Proposed — reflected in Blueprint §15 and Stage 5 plan pending management review |
| PR-05 | Initiate Capstone architecture, evaluation dataset construction (CD-01), and AISVS threat modelling (CD-02) in Week 11 (`R-04`, `OQ-03`). | Stage 1, 2 & 5 | Proposed — reflected in Blueprint §§13–14 and Stage 5 plan pending management review |
| PR-06 | Adopt dual-tier learner hardware specification (Minimum: 8 GB RAM, 4-core CPU, 25 GB SSD running 1.5B–3B `Q4_K_M` GGUF models; Recommended: 16 GB+ RAM, 50 GB SSD running 7B–8B models) + `ModelProviderAdapter` fallback + Pre-Week Download Manifests (`R-05`, `OQ-06`). | Stage 1 & Stage 2 | Proposed — reflected across Blueprint §6.2 and all track syllabi pending management review |
| PR-07 | Apply a **Proportionate OWASP AISVS 1.0 Verification Profile** for capstones: Core Chapters C2, C4, C5, C6, C7, C12 for all projects + Track Chapters C8 (RAG), C9 & C10 (Agentic/MCP), and C3 (Edge), with mandatory non-certification disclaimer (`R-02`, `CD-02`, `[SRC-001]`). | Stage 1 & Stage 2 | Proposed — reflected across Blueprint §14 and Stages 3–5 pending management review |
| PR-08 | Teach MCP core primitives (`Tools`, `Resources`, `Prompts`) alongside both OAuth 2.1 Resource Server permissions and the `2026-07-28` stateless request/discovery architecture (`R-06`, `CD-03`, `[SRC-005]`). | Stage 1 & Stage 4 | Proposed — implemented in `ASB-AGT-001` pending management review |
| PR-09 | Embed Nigeria Data Protection Act (NDPA) 2023 requirements (s.24 principles, s.28 DPIA trigger, s.37 human-intervention safeguards for automated decisions) into Common Core Week 4 and Capstone readiness checks (`R-07`, `[SRC-007]`). | Stage 1, 2 & 3 | Proposed — implemented in `ASB-CC-001` and Blueprint §14 pending management review |

---

## C. Assumptions awaiting verification

| ID | Assumption | Verification route |
|---|---|---|
| AS-01 | GitHub (free tier) is accessible to all target learners in their jurisdictions. | Check during platform architecture stage. |
| AS-02 | Learners have at least intermittent internet access sufficient to attend or later download live sessions. | Admissions questionnaire. |

---

## D. Unresolved questions

See [OPEN_QUESTIONS.md](OPEN_QUESTIONS.md).

## E. Superseded decisions

None.

## Change log

| Version | Date | Change |
|---|---|---|
| 0.1 | 2026-11-16 | Initial register created in Stage 0. |
