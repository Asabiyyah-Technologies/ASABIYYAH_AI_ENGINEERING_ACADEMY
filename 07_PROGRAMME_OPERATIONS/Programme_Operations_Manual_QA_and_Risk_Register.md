# PROGRAMME OPERATIONS MANUAL, QUALITY ASSURANCE FRAMEWORK AND RISK REGISTER
## Asabiyyah Technologies Global Applied AI Engineering Masterclass

| Field | Value |
|---|---|
| Document ID | ASB-OPS-001 |
| Version | 0.1 Draft |
| Status | Draft – pending management review |
| Owner (role) | Programme Operations Lead & Quality Assurance Lead (TBC) |
| Last updated | 2026-11-16 |
| Parent document | [MASTER_PROGRAMME_BLUEPRINT.md](../MASTER_PROGRAMME_BLUEPRINT.md) §§15, 19, 20 |
| Related decisions | AD-01–03, CD-01–05, PD-03–05, PR-01–09 |
| Stage of origin | Stage 10 |

---

## 1. Programme Implementation Plan (Pre-Launch to Graduation Timeline)

| Phase | Timeline | Core Operational Milestones | Responsible Role |
|---|---|---|---|
| **Phase A: Setup & Technical Audit** | Weeks `-6` to `-3` | Audit all starter repos on 8 GB CPU baseline; publish Pre-Week Download Manifests; complete legal review of `LR-01..05`; onboard 4 Track Leads & 8 Mentors. | Programme Director & Ops Lead |
| **Phase B: Admissions & Prep Pathway** | Weeks `-4` to `0` | Run applicant eligibility screening & 45-min Pre-Cohort Diagnostic; route `<70%` scorers through the 2-week Preparatory Pathway (`ASB-CC-002`); form 8 Mentor Pods (6–7 learners/pod). | Admissions & Learner Support |
| **Phase C: Phase 1 — Common Core** | Weeks `1` to `4` | Deliver shared foundations (`48–60 h`); execute Gate 1 & Readiness Assessment; confirm Track 1–4 placements (~12–13 learners/track). | Common Core Lead & 8 Mentors |
| **Phase D: Phase 2 — Specialisation** | Weeks `5` to `10` | Deliver 4 parallel specialist tracks (`72–90 h`); monitor Gate 2 weekly labs; execute Gate 3 Specialist Project & empirical report moderation (`CD-03/04/05`). | 4 Track Leads & Track Mentors |
| **Phase E: Phase 3 & 4 — Integration & Capstone** | Weeks `11` to `14` | Form 5 Cross-Functional Product Teams (~10 learners); supervise W11 contracts, W12 Alpha, W13 cross-team AISVS red-team & Eval Report (`CD-01`, `CD-02`), and W14 4-panel Individual Oral Defences (Gate 4). | All Instructional Staff |
| **Phase F: Close-Out & QA Audit** | Week `+1` | Finalise completion board, issue Certificates of Completion (`PR-01`), archive repositories, and publish Cohort QA Retrospective. | Programme Director & QA Lead |

---

## 2. Cohort Capacity, Staffing and Grouping Topology (`PD-05`, `PR-04`)

- **Maximum First-Cohort Capacity:** 50 learners (Nigerian and international participants; English medium).
- **Mentor-to-Learner Ratio:** `1 : 6–7` (8 Mentor Pods across 50 learners).
- **Instructional Roles Required (To be resourced by Management — `OQ-08`):**
  - 1 Programme Director / Lead Architect
  - 4 Specialist Track Lead Instructors (`AAE`, `RAG`, `AGT`, `EDG` — one of whom also leads Common Core)
  - 8 Technical Mentors (2 per specialist track)
  - 1 Programme Operations & Learner Support Coordinator

---

## 3. Learner Onboarding and Technical Readiness Workflow

1. **T-14 Days:** Admitted learners receive the Welcome Pack (`Learner_Handbook.md`), GitHub Organisation invite, and Pre-Cohort Diagnostic link.
2. **T-10 Days:** Learners scoring `<70%` begin the self-paced 13-hour Preparatory Pathway (`ASB-CC-002`) with daily async mentor office hours.
3. **T-3 Days:** Every learner submits the output of `python verify_env.py` confirming Python 3.11+, Git, `pytest`, $\ge 8\text{ GB}$ RAM, $\ge 25\text{ GB}$ free SSD, and local `Ollama` (`qwen2.5:1.5b`) readiness.

---

## 4. Learning Environment and Low-Bandwidth / Power-Resilient Operations (Nigerian Context)

To ensure reliable delivery across Nigerian power/ISP conditions without assuming expensive hardware or high-speed fiber (`PD-04`, `PD-05`):
1. **Modular Platform Architecture (No Vendor Lock-In):**
   - *Source Control & Submissions (Approved — `PD-05`):* **GitHub** (repositories, Pull Requests, automated `pytest` CI).
   - *Live Video & Recording (Platform-Agnostic Requirement):* Any conferencing platform supporting low-bandwidth screen share, breakout rooms (8 pods), local/cloud recording, and separate audio track export.
   - *Community & Async Coordination:* Low-bandwidth text-first channels (e.g., Discord/Slack/Matrix + SMS/WhatsApp broadcast fallback for urgent power/schedule notices).
2. **Pre-Week Offline Asset Manifests:** Published every Friday at 12:00 WAT for the following week—listing exact wheel lockfiles and `GGUF`/embedding weights so learners download once during off-peak data bundles and work 100% offline.
3. **Triple-Format Session Packs:** Within 6 hours of every live session, Ops publishes: (a) 720p video, (b) `<60 MB` 360p/audio-only recording, and (c) full Markdown transcript + runnable code bundle.
4. **Automatic 24-Hour Power/ISP Outage Grace Protocol:** Learners who log an outage check-in receive an automatic 24-hour PR extension and async participation credit when they complete the downloadable pack.

---

## 5. Weekly Programme Management Rhythm

| Day | Operational Activity | Owner |
|---|---|---|
| **Friday (Prior Week)** | Publish next week's Offline Asset Manifest, starter repo branch, and lab brief. | Track Leads & Ops |
| **Monday** | Close prior week's PR window (plus 24h outage grace); generate Yellow/Red flag tracker; run 30-min Mentor Calibration sync. | Ops Lead & Mentors |
| **Tuesday & Thursday** | Deliver Live Instructor-Led Sessions A & B (`2 × 2.0 h`); upload low-bandwidth recording packs within 6 hours. | Track Leads & Ops |
| **Friday / Saturday** | Deliver 3.0-hour Guided Practical Lab + 60-min Mentor Pod code clinics. | Track Leads & Mentors |
| **Sunday** | Weekly GitHub PR submission deadline (`23:59 WAT`); automated `pytest` grader runs on PR creation. | Learners |

---

## 6. Attendance, Assignment, Project Supervision and Moderation Procedures

- **Attendance & Engagement Tracking:** Recorded weekly per pod (Live Attendance OR Verified Outage Log + Async Pack + Submitted PR = Present). Minimum completion requirement: **$\ge 75\%$**.
- **Assignment & PR Tracking:** Automated GitHub script exports PR status (`Submitted`, `Tests Passing`, `Mentor Reviewed`, `Rubric Score`) into the central Assessment Register (`09_ADMINISTRATION/`).
- **Double-Marking Moderation:** `20%` random sample + all `<70%` fail and `>=90%` distinction submissions across Gates 1, 3, and 4 are second-marked using `Appendix E` of the Facilitator Handbook (`ASB-FAC-002`).

---

## 7. Quality Assurance (QA) and Monitoring & Evaluation (M&E) Framework

> **Integrity Rule:** This QA framework measures verifiable internal educational and engineering metrics only. It never fabricates or assumes external graduate employment statistics.

| QA Dimension | Key Performance Indicator (KPI) | Target Threshold | Data Source & Frequency | Corrective Action Trigger |
|---|---|---|---|---|
| **1. Technical Accessibility (8 GB Baseline)** | % of weekly starter labs passing clean-room test on 8 GB CPU-only container offline | **100%** | Pre-week automated CI check | Block lab release until memory/offline bug is fixed |
| **2. Curriculum & Decision Fidelity** | % of required `CD-01..05` artefacts verified in Gate 3 & Gate 4 submissions | **100%** | Gate 3 & Gate 4 Moderation Logs | Mandatory resubmission before passing gate |
| **3. Learner Pacing & Workload (`PD-03`)** | Median self-reported weekly learner hours | **12.0–15.0 h/wk** | Weekly 2-question learner pulse form | Trim optional reading/lab scope if median $>15.0\text{ h}$ |
| **4. Mentorship SLA Compliance** | % of weekly GitHub PRs reviewed by mentors within 72 hours | **$\ge 95\%$** | GitHub PR timestamp audit (Mondays) | Reallocate PR queue to backup mentor |
| **5. Assessment Consistency** | Inter-marker score variance before moderation on double-marked sample | **$\le 5\%$** | Gate 1, 3, 4 Moderation Sheets | Mandatory rubric recalibration session |
| **6. Outage Resilience Effectiveness** | Completion rate of learners utilizing the low-bandwidth pack / 24h outage grace | **$\ge 85\%$ parity** with live attendees | Attendance & PR Register | Provide offline USB/peer sync pack or 1-on-1 mentor catch-up |

---

## 8. Comprehensive Programme Risk Register

| Risk ID | Category | Risk Description | Likelihood | Impact | Mitigation & Preventive Controls | Owner |
|---|---|---|---|---|---|---|
| **RSK-01** | **Infrastructure (Nigeria)** | Prolonged grid power outage or ISP disruption prevents learners or an instructor from joining a live session or pushing PRs. | **High** | **Medium** | Co-facilitator backup on every live session; `<60 MB` audio/Markdown session packs; pre-week offline download manifests; automatic 24h PR grace window (`PD-05`). | Ops Lead |
| **RSK-02** | **Hardware / Technical** | Learners with 8 GB RAM CPU laptops experience OOM crashes or slow inference during RAG, Agent, or Edge labs. | **High** | **High** | Standardise on compact `1.5B–3B Q4_K_M` GGUF models with `-c 2048` context cap (`~1.0–2.0 GB` RAM) `[SRC-014]` + `ModelProviderAdapter` zero-cost remote fallback (`PR-06`). | Track Leads |
| **RSK-03** | **Academic / Pacing** | Entry coding variance stalls Week 1 Common Core or overwhelms beginners. | **Medium** | **High** | Mandatory Pre-Cohort Diagnostic routing `<70%` scorers into the 2-week self-paced Preparatory Pathway (`ASB-CC-002`, `PR-03`). | Common Core Lead |
| **RSK-04** | **Capstone Delivery** | 10-person cross-functional teams suffer integration deadlock or uneven workload ("free-riding") in Weeks 11–14. | **Medium** | **High** | Start capstone in Week 11 (`PR-05`); enforce Day-2 `Pydantic`/MCP contract freeze with mocks; require individual Git commit audit + **15-min Individual Oral Technical Defence** (`PR-04`). | Programme Director |
| **RSK-05** | **Security & Privacy** | A learner accidentally commits a live API key or real personal data (violating **NDPA 2023**) to a GitHub repository. | **Medium** | **High** | Pre-commit secret/PII scanner hooks in all starter repos; synthetic-only data rule; mandatory Week 4 PII redaction middleware; immediate key revocation & 72h NDPC escalation protocol (`LR-01`). | Security / QA Lead |
| **RSK-06** | **Reputational / Compliance (`CD-02`)** | A learner or marketing post falsely claims a capstone is "OWASP AISVS Certified" or that the Certificate of Completion is an accredited degree. | **Low** | **Critical** | Mandatory non-certification disclaimer checked in every Gate 3/4 rubric (`CD-02`); strict publication control (`LR-05`, `PR-01`). | Programme Director |
| **RSK-07** | **Technical Currency** | Rapid changes in `MCP` specification (`2026-07-28`) or `OpenTelemetry GenAI` attributes break lab code mid-cohort. | **Medium** | **Medium** | Pin exact SDK versions in `pyproject.toml` lockfiles per cohort and review `Source_Register.md` bi-annually `[SRC-005, SRC-006]`. | Track Leads |

---

## 9. Incident Escalation Procedure

1. **Severity 1 — Critical Security, Data Breach (`NDPA 2023`), or Safeguarding Incident:**
   - *Examples:* Real third-party personal data leaked in a public repo; active abuse/harassment; unauthorized external red-teaming attack.
   - *Action (Within 1 Hour):* Immediately take repository private / revoke credentials / suspend offending account; notify **Programme Director** and **Data Protection / Legal Counsel**. If personal data breach meets **NDPA 2023 s.40** threshold, notify the **Nigeria Data Protection Commission (NDPC) within 72 hours** `[SRC-007]`.
2. **Severity 2 — Live Delivery or Platform Outage:**
   - *Examples:* Lead instructor loses power/internet mid-session; GitHub Actions runner outage on deadline day.
   - *Action (Within 15 Minutes):* Backup co-facilitator assumes screen share; if cohort-wide connectivity fails, post SMS/low-bandwidth notice and publish pre-recorded walkthrough + automatic 24-hour deadline extension.
3. **Severity 3 — Academic Progress or Team Conflict:**
   - *Examples:* Learner misses 2 consecutive PRs; capstone sub-team interface dispute.
   - *Action (Within 48 Hours):* Pod Mentor and Ops Lead convene a 20-minute mediation/remediation session and log a binding action plan.

---

## 10. Operational Checklists and Reporting Templates

### Appendix A: Pre-Cohort Launch Implementation Checklist
- [ ] Management sign-off recorded in `DECISION_REGISTER.md` for `PR-01..09`.
- [ ] Legal review completed and signed off for `LR-01..05` (`09_ADMINISTRATION/Policy_Manual_and_Legal_Review_Register.md`).
- [ ] All 14 weekly starter repositories, `pytest` suites, and offline manifests tested on an 8 GB RAM CPU environment.
- [ ] 50 learners onboarded, diagnostic completed, and assigned to 8 Mentor Pods (6–7 learners/pod).
- [ ] 4 Track Leads and 8 Mentors calibrated on rubrics (`04_ASSESSMENT/`).

### Appendix B: Weekly Programme Operations Status Report Template
```markdown
# WEEKLY OPERATIONS & QA REPORT — WEEK [W1–W14]
**Date:** [YYYY-MM-DD] | **Active Cohort Size:** [N/50]
1. **Participation & Resilience:** Live Attendance: [X%] | Verified Outage/Async Pack Completion: [Y%] | Combined Engagement: [X+Y % (Target >=75%)]
2. **Weekly PR & Automated Test Pass Rate:** PRs Submitted: [N/50] | Passing `pytest`: [N] | Mentor Reviews Completed <72h: [Z%]
3. **Workload Pulse:** Median Learner Hours Reported: [XX.X h (Target 12–15h)]
4. **Learners on Yellow/Red Support Flags:** [Count & anonymized IDs + remediation status]
5. **Technical / Infrastructure Incidents & Actions Taken:** [Summary]
```

---

## Change log

| Version | Date | Change |
|---|---|---|
| 0.1 | 2026-11-16 | Created in Stage 10 covering all 20 operational areas, QA/M&E framework, Risk Register, and escalation procedures. |
