# PROGRAMME POLICY MANUAL, RESPONSIBLE AI FRAMEWORK AND LEGAL REVIEW REGISTER
## Asabiyyah Technologies Global Applied AI Engineering Masterclass

| Field | Value |
|---|---|
| Document ID | ASB-ADM-001 |
| Version | 0.1 Draft |
| Status | **Draft – Pending Management Approval & Qualified Legal Review** |
| Owner (role) | Programme Director & Legal/Compliance Counsel (TBC) |
| Last updated | 2026-11-16 |
| Parent document | [MASTER_PROGRAMME_BLUEPRINT.md](../MASTER_PROGRAMME_BLUEPRINT.md) §20 |
| Related decisions | CD-01, CD-02, PD-05, PR-01, PR-02, OQ-09, OQ-11 |
| Stage of origin | Stage 8 |

> **CRITICAL GOVERNANCE & LEGAL REVIEW NOTICE:**
> This Policy Manual contains draft institutional policies for the Asabiyyah Technologies Global Applied AI Engineering Masterclass. No policy herein becomes legally binding or publicly effective until formally approved by management and reviewed by qualified legal counsel in Nigeria (and applicable international jurisdictions for non-resident participants). All clauses requiring legal verification are indexed in **Section 13 (Legal Review Register)**.

---

## POLICY 1: Learner Code of Conduct

1. **Purpose & Scope:** Applies to all learners across live online sessions, mentor pod meetings, GitHub repositories, code reviews, and community forums.
2. **Expected Professional Standards:**
   - Communicate constructively and respectfully with peers, mentors, and facilitators across diverse nationalities, backgrounds, and skill levels.
   - Deliver honest, timely commitments to your 6–7 learner Mentor Pod (Weeks 1–10) and your 10-person Cross-Functional Capstone Team (Weeks 11–14).
   - Provide objective, blameless technical feedback during GitHub Pull Request reviews.
3. **Prohibited Conduct:** Harassment, bullying, discriminatory language, doxxing, disruption of live sessions, unauthorized sharing of session recordings containing peer likenesses, or misuse of computing labs for unauthorized security attacks.

---

## POLICY 2: Academic Integrity Policy

1. **Core Principle — Human Engineering Ownership:** Every learner is personally accountable for the correctness, safety, and originality of all code, evaluation datasets, benchmarks, and reports submitted under their name or GitHub account.
2. **Permitted & Disclosed Use of AI Coding Assistants:**
   - Learners may use AI coding assistants for syntax lookup, boilerplate scaffolding, or debugging **provided that**:
     1. Use is explicitly declared in the Pull Request template (`AI-Assistance-Disclosure: [Tool used & scope]`).
     2. The learner personally writes or thoroughly verifies all core architecture, tests, evaluation runners, and security checks.
     3. The learner can explain and live-edit any line of their committed code during Mentor Pod checks and the **Week 14 Individual Oral Technical Defence**.
3. **Academic Misconduct Offences:**
   - **Plagiarism:** Submitting another learner's or an external repository's code/reports without explicit attribution and licence compliance.
   - **Fabrication of Empirical Data:** Hardcoding mock responses to fake passing tests, manually editing `results.json` or OpenTelemetry trace logs (`CD-01`), or inventing hardware metrics in an Edge AI Benchmark Report (`CD-05`).
   - **Ghostwriting / Impersonation:** Having a third party write assessment deliverables or sit an assessment/oral defence.

---

## POLICY 3: Responsible AI Use Policy

1. **Verification Over Blind Trust:** Learners must treat all LLM and agent outputs as probabilistic and potentially confabulated (`NIST AI 600-1` `[SRC-004]`). No system built in the programme may present unverified model output as authoritative medical, legal, financial, or safety-critical instruction without prominent human-in-the-loop review gates (`NDPA 2023 s.37` `[SRC-007]`).
2. **Authorised Red-Teaming Boundary:** Prompt-injection, jailbreaking, and adversarial security payloads (`CD-02`) may **only** be executed against local sandbox containers or designated cohort red-team targets (e.g., Week 13 paired capstone testing). Attacking third-party production APIs or external services is strictly prohibited.
3. **Dataset & Bias Responsibility:** Learners must document known dataset biases, linguistic coverage gaps (including performance variance on Nigerian languages and Pidgin), and failure modes in every `AI_System_Evaluation_Report.md` (`CD-01`).
4. **Distinction Between Policy & Technical Reference (`CD-02`):** This policy governs learner and staff conduct; **OWASP AISVS 1.0** `[SRC-001]` is used as a technical security verification reference for capstone architecture and never implies external security certification.

---

## POLICY 4: Data Protection and Privacy Policy Draft (`NDPA 2023` Alignment)

> **[FLAGGED FOR LEGAL REVIEW — LR-01]:** Must be reviewed by a Nigeria Data Protection Commission (NDPC)-licensed Data Protection Compliance Organisation (DPCO) / legal counsel prior to cohort launch `[SRC-007]`.

1. **Regulatory Baseline:** Asabiyyah Technologies Ltd processes personal data in accordance with the **Nigeria Data Protection Act (NDPA) 2023** (Sections 24–37) and applicable international data protection principles for international participants `[SRC-007]`.
2. **Categories of Learner Data Collected (Data Minimisation — NDPA s.24):**
   - Full name, email/phone contact, country/state of residence, educational/programming background, hardware readiness self-report, GitHub username, session attendance/outage logs, assessment grades, and recorded oral defences.
3. **Lawful Basis & Consent (NDPA s.25):**
   - *Contractual Necessity:* Processing admissions, grading, mentorship, and issuing the Certificate of Completion.
   - *Explicit Consent:* Recording live teaching sessions and oral defences, or showcasing graduate projects/names publicly. Learners may opt out of public marketing showcase without affecting their academic standing.
4. **Strict Ban on Real Third-Party Personal Data in Labs:**
   - Learners and instructors must **never** ingest, commit, or transmit real unconsented third-party personal data (e.g., real Nigerian NINs, BVNs, bank statements, patient health records, or private employer files) into course repositories or external LLM APIs. All labs use synthetic or public-domain corpora plus automated PII redaction middleware.
5. **Data Subject Rights & Breach Notification:** Learners have the right to access, rectify, or request erasure of their personal data, and to contest solely automated decisions (`NDPA s.37`). Any personal data breach is escalated internally immediately and reported to the NDPC within **72 hours** where required by law (`NDPA s.40`) `[SRC-007]`.

---

## POLICY 5: Attendance, Participation and Infrastructure Resilience Policy

1. **Minimum Engagement Standard:** Learners must maintain **$\ge 75\%$ verified weekly engagement** across the 14 weeks.
2. **Equal Recognition of Asynchronous / Outage-Resilient Participation (`OQ-05`):**
   - Recognising electricity and internet variability in Nigeria and similar environments, a learner who cannot attend a live session due to power/ISP failure satisfies that week's participation requirement by:
     1. Logging an outage notification within 24 hours,
     2. Reviewing the low-bandwidth recording/Markdown pack, and
     3. Submitting the weekly GitHub Lab Pull Request within the automatic **24-hour outage grace window**.
3. **Early Support Trigger:** Any learner who misses two consecutive weekly PR submissions or Mentor Pod check-ins without communication is contacted by Learner Support to create a catch-up plan.

---

## POLICY 6: Assessment and Academic Appeals Policy

1. **Transparent Rubric Grading:** All assessments are graded against the published 7-dimension rubrics (`04_ASSESSMENT/Assessment_Framework_and_Rubrics.md`).
2. **Right to Reassessment:** Learners scoring below threshold on Gate 1 (`<65%`), Gate 3 (`<70%`), or Gate 4 (`<70%`) are entitled to one structured reassessment submission within 7 calendar days (capped at the pass threshold).
3. **Grounds for Formal Academic Appeal:** A learner may appeal a gate result within **7 calendar days** of grade notification on grounds of: (a) procedural irregularity in marking, (b) computational error in score aggregation, or (c) documented mitigating circumstances that could not reasonably be disclosed beforehand. Dissatisfaction with academic judgement alone is not grounds for appeal once double-marking moderation has been completed.
4. **Appeal Review Panel:** Appeals are reviewed within 10 working days by an independent reviewer (Programme Director or Senior Instructor not involved in the original marking).

---

## POLICY 7: Complaints and Grievance Policy

1. **Informal Resolution First (Stage 1):** Learners are encouraged to raise technical, scheduling, or mentorship concerns directly with their Mentor or Programme Operations Lead for resolution within **3 working days**.
2. **Formal Written Complaint (Stage 2):** If unresolved, or if the complaint concerns a mentor/facilitator, the learner submits a **Formal Complaint Form** (`09_ADMINISTRATION/Admissions_Certification_and_Administration_Pack.md`) to the Programme Director, who acknowledges receipt within **48 hours** and issues a written investigation outcome within **10 working days**.
3. **Non-Retaliation Guarantee:** No learner will suffer academic or administrative disadvantage for raising a complaint in good faith.

---

## POLICY 8: Disciplinary Procedure

> **[FLAGGED FOR LEGAL REVIEW — LR-02]:** Ensure alignment with fair-hearing principles and applicable Nigerian contract/education law.

1. **Principles of Natural Justice:** All disciplinary actions follow clear notice of the allegation, disclosure of evidence, a fair opportunity for the learner to respond in writing and/or in a hearing, proportionate sanctions, and a right of appeal.
2. **Tiered Sanctions:**
   - **Level 1 (Minor / First Infraction — e.g., undisclosed minor AI boilerplate use, late team communication):** Written warning + mandatory correction/resubmission within 72 hours.
   - **Level 2 (Serious Infraction — e.g., plagiarised lab PR, fabricated evaluation/benchmark metrics, repeated code-of-conduct breach):** Score of `0%` on the affected component, mandatory ethics/remediation task, and formal probation.
   - **Level 3 (Gross Misconduct — e.g., malicious cyberattack/red-teaming outside sandbox, severe harassment, uploading stolen real PII, paid ghostwriting):** Dismissal from the programme without Certificate of Completion following a formal panel review.
3. **Confidentiality & Recordkeeping:** Disciplinary records are restricted to the Programme Director and Compliance Lead and retained securely.

---

## POLICY 9: Safeguarding, Accessibility and Inclusion Policy

> **[FLAGGED FOR LEGAL REVIEW — LR-03]:** Review safeguarding escalation duties for online international cohorts.

1. **Inclusive Learning Environment:** Asabiyyah Technologies Ltd welcomes qualified learners regardless of gender, ethnicity, religion, physical disability, nationality, or socio-economic background.
2. **Adult Cohort Baseline & Vulnerable Participants:** The programme is designed for adults (`18+ years`). If management ever admits an exceptional participant aged `16–17`, written parental/guardian consent and two-facilitator presence rules apply to all 1-on-1 mentoring sessions.
3. **Accessibility Adjustments:** Low-bandwidth text transcripts, screen-reader-friendly Markdown materials, and extended practical test time (`+25%`) for documented disabilities are provided upon request during onboarding.

---

## POLICY 10: Intellectual Property (IP) and Project Ownership Policy Draft (`PR-02`)

> **[FLAGGED FOR MANAGEMENT DECISION & LEGAL REVIEW — LR-04 / OQ-11]:** Management must confirm selection of Option A (Recommended) before cohort contracts are issued.

1. **Asabiyyah Background IP:** All curriculum documents, syllabi, starter repositories, grading scripts, datasets created by Asabiyyah, and brand assets remain the exclusive intellectual property of **Asabiyyah Technologies Ltd**. Learners receive a personal, non-transferable licence to use them for learning.
2. **Learner Project & Capstone IP — Recommended Fair Default (`PR-02`):**
   - **Learner Ownership of Original Code:** Learners (and cross-functional Capstone Teams jointly for shared repositories) **retain copyright and intellectual property ownership** of the original software code, architectures, and reports they author during the programme.
   - **Open-Source Recommendation:** Capstone teams are encouraged to license their public portfolio repositories under a permissive open-source licence (`MIT` or `Apache-2.0`) so every team member can freely Fork, demonstrate, and extend the project for employment or startup use.
   - **Non-Exclusive Showcase Licence to Asabiyyah:** By enrolling, learners grant Asabiyyah Technologies Ltd a **royalty-free, non-exclusive, worldwide licence** to display, link to, and demonstrate their project repositories, screenshots, and evaluation summaries for educational, quality-assurance, and academy showcase purposes, always with explicit attribution to the learner authors.
   - **Sponsor / Client Data Exception:** If a future capstone team voluntarily chooses an external company-sponsored problem brief involving proprietary partner IP, a separate written project IP agreement must be signed by all team members *prior* to Week 11; no learner may be forced onto a proprietary-IP team against their wishes.

---

## POLICY 11: Information Security and Acceptable Use Policy

1. **Credential & API Key Hygiene:** Learners must never commit API keys, `.env` files, or bearer tokens to GitHub. Repositories must include a `.gitignore` blocking `.env*`, `*.db`, and `*.gguf`. Any leaked secret must be revoked immediately.
2. **Local Inference & Container Safety:** Local model servers (`Ollama`, `llama-server`) and vector databases (`Qdrant`) must bind to `127.0.0.1` (localhost) by default (`AISVS C4`), never `0.0.0.0` on public Wi-Fi/shared networks.
3. **Supply-Chain Verification:** Learners must download open-weight models and packages only from verified sources listed in the weekly manifest and verify `SHA-256` digests (`AISVS C6`).

---

## POLICY 12: Facilitator and Mentor Conduct Policy

1. **Professional & Objective Grading:** Facilitators and mentors must grade strictly against published rubrics (`04_ASSESSMENT/`), disclose any personal or financial conflict of interest with a learner, and complete grading turnaround within **72 hours** of submission.
2. **Technical Rigor & Honesty:** Facilitators must model engineering best practices—never teaching insecure shortcuts (`shell=True`, hardcoded keys, unverified claims) or misrepresenting AISVS checklists as security certifications (`CD-02`).
3. **Duty of Care & Confidentiality:** Mentors must keep learner performance struggles, disability accommodations, and power/connectivity hardships strictly confidential within the instructional team.

---

## 13. Legal Review Register (Mandatory Pre-Launch Sign-Off Table)

| Ref ID | Policy / Document Section | Specific Legal & Regulatory Issue | Primary Applicable Law / Standard | Required Reviewer | Status |
|---|---|---|---|---|---|
| **LR-01** | Policy 4 (`ASB-ADM-001`) & Registration Pack (`ASB-ADM-002`) | Learner privacy notice, lawful basis, cross-border data transfer for international students, recording consent, and 72-hour breach reporting. | **Nigeria Data Protection Act (NDPA) 2023** (ss. 24–40) & NDPC Guidance; UK/EU GDPR where applicable `[SRC-007]`. | NDPC-Licensed DPCO / Data Privacy Counsel | **Pending Legal Review** |
| **LR-02** | Policy 6, Policy 7 & Policy 8 (`ASB-ADM-001`) | Enforceability of disciplinary sanctions, dismissal terms, and appeals procedure in learner enrolment terms. | Nigerian Contract Law & Consumer Protection Framework | Corporate / Education Legal Counsel | **Pending Legal Review** |
| **LR-03** | Policy 9 (`ASB-ADM-001`) | Adult (`18+`) age verification or minor safeguarding protocols and international online harassment jurisdiction. | Nigerian Cybercrimes Act / Safeguarding Law | Legal Counsel | **Pending Legal Review** |
| **LR-04** | Policy 10 (`ASB-ADM-001` — `PR-02`) | Default learner IP retention, joint ownership among 10-person capstone teams (`MIT`/`Apache-2.0` licensing), and Asabiyyah non-exclusive showcase licence. | Nigerian Copyright Act & IP Law | IP Legal Counsel + Management Sign-Off | **Pending Management & Legal Review** |
| **LR-05** | Certificate wording (`ASB-ADM-002` — `PR-01`) & Prospectus (`11_FINAL_PUBLICATION/`) | Ensuring "Certificate of Completion — Asabiyyah Technologies Ltd" and AISVS 1.0 references comply with advertising/educational representation laws and carry zero implied NUC/NBTE accreditation or OWASP certification claims. | Nigerian Educational & Advertising Standards; OWASP Trademark/Usage Rules (`CD-02`) | Legal Counsel + Management Sign-Off | **Pending Management & Legal Review** |

---

## Change log

| Version | Date | Change |
|---|---|---|
| 0.1 | 2026-11-16 | Created in Stage 8 covering all 12 policies, NDPA 2023 alignment, IP options, and the Legal Review Register. |
