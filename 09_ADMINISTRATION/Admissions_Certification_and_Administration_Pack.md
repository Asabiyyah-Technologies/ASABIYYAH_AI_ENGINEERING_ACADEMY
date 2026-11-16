# ADMISSIONS, CERTIFICATION AND ADMINISTRATION TEMPLATES PACK
## Asabiyyah Technologies Global Applied AI Engineering Masterclass

| Field | Value |
|---|---|
| Document ID | ASB-ADM-002 |
| Version | 0.1 Draft |
| Status | **Draft – Pending Management Approval & Legal Review (`LR-01`, `LR-05`)** |
| Owner (role) | Admissions Lead & Academic Registrar (TBC) |
| Last updated | 2026-11-16 |
| Parent document | [MASTER_PROGRAMME_BLUEPRINT.md](../MASTER_PROGRAMME_BLUEPRINT.md) §§6, 15, 18 |
| Related decisions | AD-01–03, CD-01–05, PD-03–05, PR-01–06 |
| Stage of origin | Stage 12 |

---

## PART A: ADMISSIONS AND SELECTION SYSTEM

### 1. Transparent Prospectus Information Summary (For Applicant Recruitment)
- **Programme Title:** Asabiyyah Technologies Global Applied AI Engineering Masterclass
- **Provider:** Asabiyyah Technologies Ltd
- **Format & Duration:** 14 weeks, part-time (`12–15 hours/week`), online-first live instructor-led international cohort (maximum 50 learners in Cohort 1) with low-bandwidth and offline execution support (`PD-03`, `PD-05`).
- **Structure:** Shared Common Core (`Weeks 1–4`) $\rightarrow$ **One** selected Specialisation (`Weeks 5–10`: *AI Application Engineering*, *RAG & Knowledge Engineering*, *Agentic AI Engineering*, or *Edge & Offline AI Engineering*) $\rightarrow$ Cross-Functional Integration & Capstone (`Weeks 11–14`).
- **Award (`PR-01`):** *Certificate of Completion in Applied AI Engineering (with named Specialisation Track)* issued by **Asabiyyah Technologies Ltd**, subject to passing all four assessment gates. *(Note: This is an industry training credential issued by Asabiyyah Technologies Ltd, not a university degree, professional licence, or externally accredited qualification.)*

---

### 2. Applicant Eligibility and Selection Criteria (`PD-04`)

Selection is merit-based, transparent, and free of arbitrary barriers:

| Criterion | Weight / Rule | Verification Method |
|---|---|---|
| **1. Elementary Programming Readiness** | **40%** | 45-minute automated **Pre-Cohort Coding & API Diagnostic** (`ASB-CC-002`): Python data structures, file/JSON error handling, basic HTTP request, and Git CLI. *Note: Applicants scoring `50–69%` are admitted conditionally via the free 2-week Preparatory Pathway (`13 h`); applicants scoring `>=70%` enter Week 1 directly.* |
| **2. Problem-Solving & Engineering Motivation** | **30%** | Short technical application statement describing a real problem the applicant wants to solve and commitment to `12–15 hours/week` of hands-on coding. |
| **3. Technical & Hardware Readiness (`PR-06`)** | **20%** | Access to a 64-bit laptop with $\ge 4$ cores, $\ge 8\text{ GB}$ RAM, and $\ge 25\text{ GB}$ free SSD storage (no GPU or paid API subscription required). |
| **4. Cohort Balance & Track Diversity** | **10%** | Ensuring balanced preliminary interest across the four active tracks (~10–15 learners per track across the 50-learner cap). |

---

### 3. Application Form & NDPA 2023 Privacy Notice Template (`LR-01`)

```markdown
# APPLICATION FORM — GLOBAL APPLIED AI ENGINEERING MASTERCLASS
**Section 1: Applicant Identity & Contact (Data Minimisation — NDPA 2023 s.24)**
- Full Name: ___________________________ | Preferred Name: ___________________
- Email Address: _______________________ | Phone / WhatsApp (for outage alerts): _______________
- Country & City of Residence: _________ | Time Zone (e.g., WAT / UTC+1): ______
- GitHub Username / Profile URL: https://github.com/__________________________

**Section 2: Programming & Technical Baseline (PD-04)**
- Primary Programming Language(s) & Years of Practice: ________________________
- Rate your current comfort (1 = Beginner to 5 = Fluent):
  [ ] Python functions, dicts/lists & virtual environments
  [ ] Git (`clone`, `branch`, `commit`, `push`, Pull Requests)
  [ ] Command Line (PowerShell / Bash) & JSON / REST APIs
- Link to 1 sample code repository or script you have written (if available): _____

**Section 3: Hardware & Connectivity Readiness Check (PR-06 — No GPU Required)**
- Laptop CPU & OS: _____________________ | System RAM: [ ] 8 GB  [ ] 16 GB+  [ ] <8 GB
- Free SSD Disk Space >= 25 GB? [ ] Yes [ ] No | Typical Internet: [ ] Broadband [ ] 3G/4G Mobile
- Can you commit 12–15 hours/week across 14 weeks? [ ] Yes [ ] No

**Section 4: Preliminary Specialisation Track Interest (Weeks 5–10 — Rank 1st & 2nd Choice)**
*(Final placement is confirmed at the end of Week 4 Common Core.)*
[ ] Track 1: AI Application Engineering
[ ] Track 2: RAG & Knowledge Engineering
[ ] Track 3: Agentic AI Engineering
[ ] Track 4: Edge & Offline AI Engineering

**Section 5: NDPA 2023 Privacy Notice & Explicit Consent [FLAGGED FOR LEGAL REVIEW — LR-01]**
Asabiyyah Technologies Ltd collects the information on this form solely to evaluate your application, administer the training cohort, and communicate programme updates in accordance with the Nigeria Data Protection Act (NDPA) 2023. Your data will never be sold to third parties.
- [ ] **Mandatory:** I confirm that the information provided is my own accurate work and I consent to Asabiyyah Technologies Ltd processing my application data.
- Signature / Full Name: _______________________ | Date: YYYY-MM-DD
```

---

### 4. Admission Decision Letter Templates

```markdown
### TEMPLATE A: Direct Admission Offer (Diagnostic Score >= 70%)
Dear [Name],
Congratulations! You have been selected for Cohort [N] of the **Asabiyyah Technologies Global Applied AI Engineering Masterclass** (14 weeks, 12–15 hours/week). Your Pre-Cohort Diagnostic score ([XX]/100) clears you for direct entry into Week 1 (Common Core). To secure your seat among the 50 cohort participants, please complete the Learner Registration & Consent Pack by [Date].

### TEMPLATE B: Conditional Admission via 2-Week Preparatory Pathway (Diagnostic Score 50–69%)
Dear [Name],
We are pleased to offer you a conditional seat in Cohort [N] of the **Asabiyyah Technologies Global Applied AI Engineering Masterclass**. To ensure you thrive in Week 1, your offer includes automatic enrolment in our free, self-paced **2-Week Preparatory Pathway (13 hours)** covering Python 3.11+, Git, CLI, and HTTP JSON APIs (`ASB-CC-002`). Completing the Preparatory Pathway and passing the readiness re-check by [Date] confirms your full seat in Week 1.
```

---

### 5. Week 4 Track Preference & Placement Procedure

At the end of Week 4 (Common Core), learners submit this form alongside Gate 1:
```markdown
# WEEK 4 SPECIALISATION TRACK PLACEMENT FORM
**Learner Name & ID:** [Name / ID] | **Gate 1 Score:** [XX%]
1. **First-Choice Specialisation Track (Weeks 5–10):** [Track 1 / 2 / 3 / 4]
2. **Second-Choice Specialisation Track:** [Track 1 / 2 / 3 / 4]
3. **1-Paragraph Technical Goal for Weeks 5–10:** [Explain how you plan to apply this track in the Week 11–14 Cross-Functional Capstone]
*Placement Rule:* All learners passing Gate 1 (>=65%) are placed into their 1st choice unless a single track exceeds 15 learners, in which case placement uses Gate 1 domain sub-scores and 2nd preferences so each track holds 10–15 learners for balanced Week 11 capstone teams.
```

---

### 6. Learner Registration & Consent Form (`LR-01`, `LR-04`)

```markdown
# LEARNER REGISTRATION & CONSENT AGREEMENT
**Learner Name:** _______________________ | **Cohort ID:** ASB-C01-___
1. **Programme & Policy Commitment:** I have read and agree to abide by the **Learner Handbook (`ASB-LRN-001`)** and the **Policy Manual (`ASB-ADM-001`)**, including the Code of Conduct, Academic Integrity Policy, and Responsible AI Use Policy.
2. **Certificate Acknowledgement (`PR-01`):** I understand that the **Certificate of Completion** is issued by Asabiyyah Technologies Ltd upon passing all 4 assessment gates (`>=70%` overall, mandatory `CD-01..05` reports, and Individual Oral Defence) and is not a university degree or external statutory licence.
3. **Session Recording & Showcase Consent (`NDPA 2023 s.25` — `LR-01`, `LR-04`):**
   - [ ] I consent to instructional recording of live sessions and my Week 14 Oral Technical Defence for grading, moderation, and low-bandwidth cohort playback.
   - [ ] *(Optional — May Opt Out)* I grant Asabiyyah Technologies Ltd a non-exclusive licence (`PR-02`) to showcase my public project links and name in academy graduate portfolios.
**Signed:** ___________________________ | **Date:** YYYY-MM-DD
```

---

## PART B: ACADEMIC ADMINISTRATION REGISTERS & OPERATIONAL TEMPLATES

All 13 administrative registers below are maintained in structured CSV/database tables with strict role-based access control:

```markdown
### 1. Master Learner Register (`Learner_Register.csv`)
| Learner_ID | Full_Name | Email | Country | Hardware_Tier (8GB/16GB) | Prep_Pathway_Status | W1_W4_Pod | Selected_Track (AAE/RAG/AGT/EDG) | W5_W10_Pod | W11_W14_Capstone_Team | Enrolment_Status |

### 2. Weekly Attendance & Outage Resilience Register (`Attendance_Register.csv`)
| Week | Learner_ID | Session_A (Live/Async_Outage/Absent) | Session_B (Live/Async_Outage/Absent) | Guided_Lab (Live/Async_Outage/Absent) | Pod_CheckIn | Outage_Ticket_Logged? | Weekly_Engagement_Valid? (Y/N) |

### 3. Weekly GitHub Assignment & PR Tracker (`Assignment_Tracker.csv`)
| Week | Learner_ID | Track | PR_URL | Commit_SHA | Pytest_Status (Pass/Fail) | AI_Disclosure_Present? | Submitted_Within_SLA_or_Grace? | Mentor_Reviewer | Review_Turnaround_Hours | Rubric_Score_Pct |

### 4. Master Gate Assessment Record (`Assessment_Record.csv`)
| Learner_ID | Track | Gate1_Core_20pct (Min 65) | Gate2_Labs_20pct (Min 5/6) | Gate3_Track_Proj_25pct (Min 70) | Gate4_Capstone_35pct (Min 70) | Individual_Defence_Pass? | Weighted_Total_Pct | Moderated_By | Reassessment_Used? |

### 5. Capstone & Specialist Project Progress Tracker (`Project_Progress_Tracker.csv`)
| Team_or_Learner_ID | Phase (Gate3 / Gate4) | Owned_Module_&_AISVS_Chapters | W11_Contracts_Locked | W12_Alpha_Traces | W13_RedTeam_&_Reports | W14_Clean_Build | CD01_Eval_Report_Verified | CD02_AISVS_Report_Verified | Track_CD03_04_05_Verified |

### 6. Mentor Assignment & Pod Roster Record (`Mentor_Assignment_Record.csv`)
| Mentor_ID | Mentor_Name | Specialist_Track | W1_W4_Pod_ID (6-7 Learners) | W5_W10_Track_Pod_ID (6-7 Learners) | W11_W14_CoSupervised_Capstone_Team (10 Learners) | Backup_Mentor_ID |

### 7. Individual Mentorship & Support Log (`Mentorship_Log.csv`)
| Date | Learner_ID | Mentor_ID | Support_Type (Code_Review / Outage_CatchUp / Remediation) | Technical_Blocker_Summary | Agreed_Action_Items | FollowUp_Date | Status |

### 8. End-of-Phase Learner Feedback Form (`Learner_Feedback_Form.md`)
- Phase Completed: [Common Core W4 / Specialisation W10 / Capstone W14]
- Average weekly hours spent: [ <12h | 12–15h | >15h ]
- Rate clarity of instruction, lab reproducibility on your hardware, and mentor PR feedback (1–5 scale).
- Did you use the low-bandwidth packs or offline manifests? How can we improve them?

### 9. Technical, Security or Data Incident Report (`Incident_Report_Form.md`)
- Incident ID: INC-____ | Date/Time (WAT): ________ | Severity: [Sev 1 Critical / Sev 2 Delivery / Sev 3 Academic]
- Category: [API Key Leak / Potential NDPA Data Breach / Sandbox Violation / Power-Platform Outage]
- Immediate Containment Action Taken (<1h): ____________________________________
- Root Cause & Preventive Fix: ___________________ | NDPC 72h Notification Required? [Yes/No]

### 10. Formal Learner Complaint Form (`Complaints_Form.md`)
- Learner Name & ID: ____________ | Date: ________ | Stage 1 Informal Resolution Attempted? [Yes/No]
- Summary of Complaint & Supporting Evidence: __________________________________
- Requested Resolution: _________________________ *(SLA: Acknowledged in 48h; outcome within 10 working days)*

### 11. Formal Academic Appeal Form (`Appeal_Form.md`)
- Learner Name & ID: ____________ | Assessment Gate Appealed: [Gate 1 / Gate 2 / Gate 3 / Gate 4]
- Ground for Appeal (check one): [ ] Procedural Irregularity  [ ] Score Calculation Error  [ ] Undisclosed Mitigating Circumstances with Evidence
- Detailed Statement & Evidence Attached: ______________________________________
```

---

## PART C: COMPLETION, CERTIFICATION PROCEDURE & CERTIFICATE DRAFT (`PR-01`)

### 1. Completion Verification Checklist & Certificate Eligibility Record

No certificate may be issued until the Academic Registrar and Programme Director sign off all seven items below for the learner:

```markdown
# CERTIFICATE ELIGIBILITY & COMPLETION CHECKLIST (`Certificate_Eligibility_Record.csv`)
**Learner Full Name:** _______________________ | **Learner ID:** ASB-C01-___
**Completed Specialisation Track:** [AI Application / RAG & Knowledge / Agentic AI / Edge & Offline AI]
- [ ] **1. Gate 1 (Common Core — 20%):** Score = [XX%] (Requirement: >= 65%)
- [ ] **2. Gate 2 (Weekly Specialisation Labs — 20%):** Passed = [X/6] labs (Requirement: >= 5 of 6 labs at >= 65%)
- [ ] **3. Gate 3 (Track Specialist Project & Report — 25%):** Score = [XX%] (Requirement: >= 70% + verified `CD-03` MCP / `CD-04` Hybrid RAG Comparison / `CD-05` Edge Benchmark Report)
- [ ] **4. Gate 4 (Capstone Package & Individual Defence — 35%):** Team Score = [XX%], Individual Oral Defence Score = [YY%] (Requirement: >= 70% on both)
- [ ] **5. Mandatory Capstone Reports Verified (`CD-01`, `CD-02`):** `AI_System_Evaluation_Report.md` and `OWASP_AISVS_Security_Verification_Report.md` (with non-certification disclaimer) verified in repository.
- [ ] **6. Participation Requirement:** Verified Live + Outage-Adjusted Async Engagement = [XX%] (Requirement: >= 75%)
- [ ] **7. Academic Integrity & Financial/Admin Clearance:** Zero unresolved misconduct holds.
- **OVERALL WEIGHTED PROGRAMME SCORE:** **[XX.X%]** (Requirement: **>= 70.0%**)
- **Registrar Sign-Off:** _______________ | **Programme Director Sign-Off:** _______________ | **Certificate Serial ID:** `ASB-AAEM-2026-[XXXX]`
```

---

### 2. Official Certificate of Completion Content Draft (`PR-01`, `LR-05`)

> **Representation Rule:** Must not contain any claim of external university accreditation, statutory licensing, or OWASP project certification.

```markdown
================================================================================
                          ASABIYYAH TECHNOLOGIES LTD
                        CERTIFICATE OF COMPLETION

                           This is to certify that
                             [LEARNER FULL NAME]

                      has successfully completed the
          GLOBAL APPLIED AI ENGINEERING MASTERCLASS (14 WEEKS)
             (192 Hours of Supervised Applied Engineering Training)

                        with Specialist Mastery in:
                  [NAME OF COMPLETED SPECIALISATION TRACK]

   Having demonstrated verified engineering competence across the Common Core,
   Specialist Track Project, Cross-Functional Capstone Product Delivery,
   Quantitative AI System Evaluation, Proportionate AI Security Verification,
                     and Individual Oral Technical Defence.

   Issued on: [DD Month YYYY]          Certificate Verification ID: ASB-AAEM-[YEAR]-[XXXX]
   ___________________________         ___________________________
   Programme Director                  Managing Director, Asabiyyah Technologies Ltd

   Notice: This Certificate of Completion is an industry-oriented professional
   training credential issued by Asabiyyah Technologies Ltd.
================================================================================
```

---

## PART D: NDPA 2023 PRIVACY AND RECORDKEEPING COMPLIANCE CHECKLIST (`LR-01`)

- [ ] **Data Minimisation (`NDPA s.24`):** Application and registration forms collect only fields strictly necessary for admissions, mentorship, and certification (zero unnecessary national ID numbers or financial account details collected).
- [ ] **Access Control:** Learner grades, disciplinary logs, and mitigating-circumstance records are stored in access-controlled directories restricted to the Programme Director, Registrar, and assigned Mentor.
- [ ] **Retention Schedule:** Unsuccessful applicant records are deleted **6 months** after cohort start; graduate assessment records and certificate verification hashes (`ASB-AAEM-YEAR-XXXX`) are retained for credential verification; session recordings are purged **12 months** after cohort completion unless covered by explicit showcase consent.
- [ ] **Legal Sign-Off (`LR-01`):** Privacy Notice and international participant transfer clauses reviewed by an NDPC-licensed Data Protection Compliance Organisation (DPCO) before opening public applications.

---

## Change log

| Version | Date | Change |
|---|---|---|
| 0.1 | 2026-11-16 | Created in Stage 12 covering all admissions, track placement, administration templates, certification procedures, and NDPA recordkeeping checks. |
