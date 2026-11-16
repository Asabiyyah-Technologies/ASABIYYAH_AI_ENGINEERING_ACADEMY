# FACILITATOR AND MENTOR HANDBOOK
## Asabiyyah Technologies Global Applied AI Engineering Masterclass

| Field | Value |
|---|---|
| Document ID | ASB-FAC-002 |
| Version | 0.1 Draft |
| Status | Draft – pending management review |
| Owner (role) | Programme Director & Lead Instructional Designer (TBC) |
| Last updated | 2026-11-16 |
| Parent document | [MASTER_PROGRAMME_BLUEPRINT.md](../MASTER_PROGRAMME_BLUEPRINT.md) |
| Related decisions | AD-01–03, CD-01–05, PD-03–05, PR-04–09 |
| Stage of origin | Stage 9 |

> **Companion document:** Detailed weekly teaching plans for Weeks 11–14 and the 14-week workload audit reside in [Stage_5_Master_Teaching_Plan_Weeks_11_to_14_and_Workload_Validation.md](Stage_5_Master_Teaching_Plan_Weeks_11_to_14_and_Workload_Validation.md) (`ASB-FAC-001`).

---

## 1. Programme Overview for Instructional Staff

The Asabiyyah Technologies Global Applied AI Engineering Masterclass is a 14-week (`12–15 h/week`) engineering programme training up to 50 learners per cohort across a shared Common Core (Weeks 1–4), four specialist tracks (Weeks 5–10), and cross-functional capstone product delivery (Weeks 11–14).

## 2. Lead Facilitator (Instructor) Responsibilities

1. **Live Technical Instruction (`4.0 h/week`):** Deliver two 2-hour interactive code-along sessions per week following the **Explain → Demonstrate → Guided Practice** methodology.
2. **Guided Lab Supervision (`3.0 h/week`):** Lead the weekly practical lab session, demonstrating clean debugging, trace inspection, and test verification on CPU-compatible hardware.
3. **Pre-Week Asset & 8 GB Baseline Verification:** Publish the weekly offline download manifest 48 hours ahead and verify that all demo/starter code runs within a `<6 GB` RAM CPU budget.
4. **Assessment Calibration & Moderation:** Lead weekly 30-minute Mentor Pod calibration meetings, second-mark borderline/distinction Gate submissions, and co-chair Week 14 Oral Technical Defence panels.

## 3. Mentor Responsibilities (1 Mentor per 6–7 Learners — `PD-05`, `PR-04`)

1. **Pod Management:**
   - *Weeks 1–4:* Guide a 6–7 learner Common Core Mentor Pod through foundational Python, `FastAPI`, `ModelProviderAdapter`, evaluation datasets, and Gate 1 readiness.
   - *Weeks 5–10:* Guide a **Single-Track Mentor Pod** (6–7 learners in your specialist domain: Track 1, 2, 3, or 4).
   - *Weeks 11–14:* Co-supervise one of the **5 Cross-Functional Capstone Product Teams (~10 learners)**.
2. **GitHub Pull Request Code Reviews (72-Hour SLA):** Review weekly learner PRs using the **Standard Code Review Template (Appendix C)**, verifying automated `pytest` results, typing, evaluation metrics, and security hygiene.
3. **Weekly Pod Check-In (`45–60 min/week`) & Outage Tracking:** Run weekly code clinics, log attendance/async outage check-ins, and escalate any learner who falls 2 labs behind within 24 hours.

## 4. Teaching Philosophy: Engineering Systems Over Framework Magic

- **Rule 1 — Never teach a framework before teaching the underlying mechanism:**
  - Show raw `httpx` JSON calls and `Pydantic` validation before introducing provider gateways.
  - Code `BM25` and Reciprocal Rank Fusion (`RRF`) math in 25 lines of Python before calling vector store helpers (`CD-04`).
  - Code a pure-Python `while step < max_steps` ReAct loop before introducing `LangGraph` (`CD-03`).
- **Rule 2 — Live-debug failures openly:** When a 1.5B local model outputs malformed JSON or misses a retrieval chunk during a live demo, do not hide it—open the OpenTelemetry trace (`Arize Phoenix` / JSONL), show learners *why* it failed, and write the validator/reranker fix live (`CD-01`).

## 5. Adult and Project-Based Learning Principles

- Adult engineers learn by **building, breaking, measuring, and fixing real artefacts**.
- Limit continuous slide lecturing to **$\le 15$ minutes** before switching to live code, terminal execution, trace inspection, or a short learner poll/checkpoint.

## 6. Common Core Delivery Guidance (Weeks 1–4)

- **Week 1 Priority:** Enforce virtual environment hygiene (`uv`/`venv`), strict `Pydantic v2` typing, and Git branch/PR discipline immediately. Do not allow learners to submit Jupyter `.ipynb` notebooks where a packaged Python module (`src/` + `tests/`) is required.
- **Week 2 Priority:** Ensure every learner successfully runs local `Ollama` (`qwen2.5:1.5b`) *and* configures their `ModelProviderAdapter` fallback so hardware/API issues never block Weeks 3–14.
- **Week 3–4 Priority:** Establish the habit that **every feature requires a golden test case (`CD-01`) and an input/output security check (`CD-02`)**.

## 7. Specialist Track Delivery Guidance (Weeks 5–10)

### 7.1 Track 1 Guidance: AI Application Engineering (`ASB-AAE-001`)
- Focus on **resilience under failure**: use `pytest` chaos fixtures to simulate HTTP `429`/`503` and 5-second network stalls during every gateway and `SSE` streaming review.
- Verify that semantic/exact SQLite caches include `tenant_id` in the lookup key and that token-bucket rate limiters (`LLM10`) reject oversized requests *before* calling the LLM.

### 7.2 Track 2 Guidance: RAG & Knowledge Engineering (`ASB-RAG-001` — `CD-04`)
- **Enforcing CD-04:** Do not accept projects that only implement basic vector similarity search. Every learner must implement and compare all four modes: (1) `BM25`, (2) `Dense Vector`, (3) `Hybrid (BM25 + Dense + RRF k=60)`, and (4) `Hybrid + Cross-Encoder Reranking` (`ms-marco-MiniLM-L-6-v2`).
- **Preventing Evaluation Leakage:** Verify that learners anchor ground-truth retrieval labels to canonical document/section spans so `Recall@k` and `MRR@k` remain valid when chunking parameters change.
- **Enforcing AISVS C8:** Verify that metadata ACL filtering happens *inside* the retriever query (pre-retrieval pushdown), never as an easily bypassed post-generation prompt instruction.

### 7.3 Track 3 Guidance: Agentic AI Engineering (`ASB-AGT-001` — `CD-03`)
- **Enforcing CD-03 (MCP):** Every learner must build both an **MCP Server** (exposing typed `Tools`, `Resources`, and `Prompts`) and an **MCP Client** connected to their agent. Teach both current SDK patterns (`stdio`, `Streamable HTTP`, OAuth 2.1 Resource Server scopes) and the `2026-07-28` stateless request headers and `server/discover` specification `[SRC-005]`.
- **Debugging `stdio` MCP Servers:** Remind learners that any stray `print()` to `stdout` inside a `stdio` MCP server corrupts JSON-RPC frames; enforce logging to `stderr` or file.
- **Enforcing AISVS C9 & C10:** Require explicit `max_steps` caps, parameterised SQL/path allowlists, and a mandatory Human-in-the-Loop (`interrupt_before`) gate whenever a tool has `destructiveHint=True`.

### 7.4 Track 4 Guidance: Edge & Offline AI Engineering (`ASB-EDG-001` — `CD-05`)
- **Enforcing CD-05 (Standard Edge Benchmark):** Grade learners on **methodology and within-host comparability**, never on how expensive their laptop is. A learner on an 8 GB Core i5 who rigorously benchmarks `Qwen2.5-1.5B Q4_K_M` vs `Q8_0` with controlled thread counts, `-c 2048`, airplane-mode verification, and `psutil` peak `RSS` scores 100%, whereas a learner with a 32 GB GPU machine who submits unrepeatable numbers without controlled flags fails the rubric.
- **Offline Verification:** Run the learner's test suite with network sockets disabled (`pytest --disable-socket` / firewall block) and `HF_HUB_OFFLINE=1` to prove true offline operation.

## 8. Laboratory Management and Live Session Pacing

- Structure every 3-hour Guided Lab into three milestones:
  - **Milestone 1 (`0:00–0:45`):** Environment & starter test verification (everyone gets green baseline tests).
  - **Milestone 2 (`0:45–2:15`):** Core implementation in breakout Mentor Pods (facilitators rotate across pods).
  - **Milestone 3 (`2:15–3:00`):** Telemetry/security check, draft PR push, and common bug debrief.

## 9. Technical Troubleshooting Guide (Resource-Constrained & Nigerian Context)

| Symptom | Root Cause | Immediate Facilitator / Mentor Fix |
|---|---|---|
| Learner's 8 GB laptop freezes when loading local LLM | Default context window (`32k+`) allocating 4+ GB KV cache or model $>3\text{B}$ parameters | Set `-c 2048` (`num_ctx: 2048`) and switch to `qwen2.5:1.5b-instruct-q4_K_M` (`~1.0 GB` RAM) `[SRC-014]`. |
| `RAG` or `Edge` script hangs at startup when offline | `sentence-transformers` / `huggingface_hub` attempting online version check | Export `HF_HUB_OFFLINE=1` and `TRANSFORMERS_OFFLINE=1`; load from local cached directory path. |
| Power cut disconnects learner mid-session | Grid/inverter switchover or ISP drop | Log outage in Pod Attendance sheet; direct learner to `<60 MB` audio/Markdown pack and 24-hour PR grace window. |
| Windows PowerShell blocks `.venv\Scripts\Activate.ps1` | Default Windows `ExecutionPolicy` restriction | Run `Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass` or call `.venv\Scripts\python.exe -m pytest` directly. |

## 10. Learner Engagement and Early Intervention

- Track weekly PR submissions every Monday morning.
- **Yellow Flag (1 missed PR or 1 missed Pod check-in):** Mentor sends a supportive direct message within 24 hours offering a 15-minute debugging slot.
- **Red Flag (2 consecutive missed PRs or `<65%` on Gate 1):** Escalate to Programme Operations Lead for a formal **Technical Remediation & Catch-Up Plan**.

## 11. Assessment, Grading and Rubric Application (`04_ASSESSMENT/`)

- Grade exclusively using the **7-Dimension Assessment Framework (`D1`–`D7`)** in `04_ASSESSMENT/Assessment_Framework_and_Rubrics.md`.
- Never award partial "effort marks" for broken code that does not run or reports that omit empirical evaluation datasets. Instead, return an actionable **Resubmit within 7 days** checklist.

## 12. Code Review Standards

Every mentor PR review must check four non-negotiables before clicking *Approve*:
1. Automated `pytest` suite passes and tests actual behaviour (not trivial `assert True`).
2. `Pydantic v2` schemas validate inputs/outputs and no secrets/PII are committed.
3. OpenTelemetry `gen_ai.*` traces or evaluation metrics (`CD-01`) are generated and committed.
4. Track-specific security controls (`CD-02` AISVS chapters) are implemented and tested.

## 13. Mentorship Model (Weekly Pod Rhythm)

Each 60-minute weekly Mentor Pod session follows a fixed agenda:
- `10 min`: Stand-up round (what worked, what blocked you, power/bandwidth status).
- `30 min`: Live peer code review of 2 selected learner PRs (rotating weekly).
- `20 min`: Targeted unblocking on the current week's lab and upcoming gate deliverable.

## 14. Capstone Supervision (Weeks 11–14)

- **Week 11 Mandatory Check:** Confirm the 10-person team has locked its `Pydantic`/API/`MCP` interface contracts and assigned a named individual module owner and AISVS chapter owner to all 10 members by Day 3 of Week 11.
- **Week 12 Mandatory Check:** Verify that all four specialist subsystems run together end-to-end and emit a shared OpenTelemetry `trace_id`.
- **Week 13 Mandatory Check:** Supervise the cross-team red-team sprint and verify that all high/critical findings are patched in code and documented in `OWASP_AISVS_Security_Verification_Report.md`.

## 15. Conducting the Week 14 Individual Oral Technical Defence

Follow the **15-Minute Individual Oral Defence Protocol** (`04_ASSESSMENT/Assessment_Framework_and_Rubrics.md` §7):
- `0–3 min`: Git commit walkthrough of the learner's owned module.
- `3–7 min`: Live trace diagnosis or code modification question (`CD-01`).
- `7–11 min`: Specialist track deep-dive (`CD-03` MCP / `CD-04` Hybrid RAG & RRF / `CD-05` Edge Benchmark / Track 1 Gateway).
- `11–15 min`: OWASP AISVS 1.0 threat/mitigation verification and system limitation question (`CD-02`).

## 16. Constructive Feedback and Remediation

Write feedback that is **Specific, Evidence-Based, and Actionable** (e.g., *"In `src/rag/retriever.py:L58`, metadata filtering is applied after top-5 dense retrieval, causing `Recall@5` to drop to 0 when tenant B chunks dominate top-5. Move the `Filter(must=[FieldCondition(...)])` inside `qdrant.query_points()` and re-run `test_cross_tenant_acl.py`"*).

## 17. Upholding Academic Integrity

- Check `AI-Assistance-Disclosure` notes on every PR.
- Spot-check evaluation JSONL files and benchmark logs (`CD-05`) to ensure timestamps, latencies, and `SHA-256` hashes come from genuine runs rather than copy-pasted text.

## 18. Teaching Responsible AI and Security (`CD-02`, `NDPA 2023`)

- Consistently remind learners that **OWASP AISVS 1.0** is an engineering verification standard and never a certification badge (`CD-02`).
- Enforce **NDPA 2023** compliance in every lab: reject any PR containing real personal data or lacking human-intervention safeguards for high-impact automated decisions (`NDPA s.37`).

## 19. Learner Safeguarding and Inclusion

Maintain a psychologically safe, inclusive learning environment. Report any harassment, safeguarding concern, or severe learner distress immediately to the Programme Director under Policy 9 (`09_ADMINISTRATION/Policy_Manual_and_Legal_Review_Register.md`).

## 20. Quality Assurance and Calibration

Participate in pre-cohort dry runs, weekly 30-minute mentor syncs, and Gate 1/3/4 double-marking moderation (`20%` sample + all borderline fails `<70%`).

## 21. Reporting and Documentation

Submit weekly Pod Attendance & PR Completion logs every Monday by 12:00 WAT and complete Gate moderation sheets within 72 hours of gate deadlines.

---

## Appendices: Operational Checklists and Templates for Facilitators & Mentors

### Appendix A: Live Lesson Delivery Checklist
- [ ] Offline asset manifest published 48h prior; starter branch pushed and tagged.
- [ ] Demo verified on 8 GB RAM CPU budget with local `Ollama` + remote adapter fallback + offline `pytest` fixtures ready.
- [ ] Screen font size $\ge 16\text{pt}$; dual recording active (`720p` + `<60 MB` low-bandwidth audio/Markdown pack).
- [ ] Zero `.env` secrets or personal data visible on screen.
- [ ] Session notes and recording uploaded within 6 hours.

### Appendix B: Laboratory Preparation Checklist
- [ ] Starter repository clones and passes baseline `pytest` in `<60 seconds` offline.
- [ ] Windows PowerShell (`run.ps1`) and Linux/macOS (`Makefile`) commands tested.
- [ ] Expected telemetry output (`traces.jsonl`) and evaluation scorecard format verified.
- [ ] Mentor breakout pods staffed and briefed on the top 3 expected learner bugs.

### Appendix C: Standard GitHub PR Code Review Template
```markdown
### Asabiyyah Mentor PR Review — Week [NN] | Learner: @[github_handle]
- **Automated `pytest` Suite:** [PASS / FAIL (X/Y tests passing)]
- **D1 Functional Correctness (20%):** [Score / Comments]
- **D2 Architecture, Typing & Provider Adapter (15%):** [Score / Comments]
- **D3 AI Evaluation & OpenTelemetry Traces — CD-01 (20%):** [Score / Comments]
- **D4 Security (AISVS) & NDPA Privacy — CD-02 (15%):** [Score / Comments]
- **D5–D6 Performance, Docs & Reproducibility (20%):** [Score / Comments]
- **AI Assistance Disclosure Verified:** [Yes / No]
- **Verdict:** [APPROVED / CHANGES REQUESTED — Action items listed below]
```

### Appendix D: Weekly Mentorship Pod Log Template
```markdown
**Pod ID:** [Pod 1–8] | **Track:** [Core / AAE / RAG / AGT / EDG] | **Week:** [W1–W14] | **Mentor:** [Name]
| Learner Name | Live Pod Attended? | Outage Logged (Async Pack Completed)? | Weekly PR Submitted? | Rubric Score (%) | Risk Flag (Green/Yellow/Red) | Action Note |
|---|---|---|---|--:|---|---|
```

### Appendix E: Assessment Moderation Record Template
```markdown
**Assessment Gate:** [Gate 1 / Gate 3 / Gate 4] | **Learner / Team ID:** [ID]
**First Marker Score (D1–D7 Breakdown):** [XX%] | **Second Marker Score (D1–D7 Breakdown):** [YY%]
**Variance > 5%?** [Yes/No] | **Agreed Moderated Score:** [ZZ%]
**Mandatory Reports Verified (`CD-01`, `CD-02` + `CD-03/04/05`)?** [Yes/No] | **Moderator Sign-Off:** [Role & Date]
```

### Appendix F: Capstone Team Supervision Weekly Tracker (Weeks 11–14)
```markdown
**Capstone Team:** [Team 1–5] | **Co-Mentors:** [Names]
- **W11 Check:** Architecture diagram, `Pydantic`/MCP contracts locked, 10 individual module + AISVS owners assigned, 30-case golden dataset committed? [PASS/FAIL]
- **W12 Check:** End-to-end Alpha integrated (UI + Hybrid RAG + MCP Agent + Edge mode) with unified OpenTelemetry `trace_id`? [PASS/FAIL]
- **W13 Check:** Cross-team red-team completed, high/critical bugs patched in code, Draft Eval (`CD-01`) & AISVS (`CD-02`) reports submitted? [PASS/FAIL]
- **W14 Check:** Clean-room build verified, all 10 individual commits audited, 15-min Individual Oral Defences completed? [PASS/FAIL]
```

### Appendix G: Post-Week Facilitator Technical Feedback Form
```markdown
**Week:** [W1–W14] | **Track:** [Core / Track 1–4] | **Facilitator:** [Role/Name]
1. **Did the week's content and lab fit within the 12–15h learner budget?** [Yes / Tight / Exceeded — explain]
2. **Any 8GB RAM, CPU, Windows/Linux, or offline package bottlenecks observed?** [Details]
3. **Top 2 technical misconceptions observed across learners:** [Details]
4. **Recommended curriculum or starter-repo patch for next cohort:** [Details]
```

---

## Change log

| Version | Date | Change |
|---|---|---|
| 0.1 | 2026-11-16 | Created in Stage 9 covering all 21 handbook sections and 7 operational checklists/templates. |
