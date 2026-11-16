# Asabiyyah Technologies Global Applied AI Engineering Masterclass
## Programme Documentation System

**One Foundation. Multiple Specialisations. Real-World AI Products.**

This repository holds the programme documentation for the Asabiyyah Technologies Ltd Global Applied AI Engineering Masterclass: a 14-week, part-time, online-first applied AI engineering programme with a shared Common Core and four specialisations.

> Status: documentation under development. No content is approved until recorded as such in [PROGRAMME_STATUS.md](PROGRAMME_STATUS.md) and [DECISION_REGISTER.md](DECISION_REGISTER.md).

## 1. Control documents

| File | Role | Authority |
|---|---|---|
| [MASTER_PROGRAMME_BLUEPRINT.md](MASTER_PROGRAMME_BLUEPRINT.md) | Programme-level **single source of truth** | All curricula, syllabi, handbooks and policies must agree with it |
| [DECISION_REGISTER.md](DECISION_REGISTER.md) | Record of approved, proposed, assumed and superseded decisions | Determines what is approved |
| [OPEN_QUESTIONS.md](OPEN_QUESTIONS.md) | Unresolved questions and the stages they block | No authority — never cite as fact |
| [PROGRAMME_STATUS.md](PROGRAMME_STATUS.md) | Stage tracker and approval record | Records status; only management records approval |

## 2. Folder map

| Folder | Contents |
|---|---|
| `01_PROGRAMME_STRATEGY/` | Strategy and positioning |
| `02_COMMON_CORE/` | Weeks 1–4 and preparatory pathway |
| `03_SPECIALISATION_TRACKS/` | Four active tracks (Weeks 5–10) + `FUTURE_ML_ENGINEERING/` (**future only**) |
| `04_ASSESSMENT/` | Assessment framework, rubrics, capstone and report templates |
| `05_LEARNER_DOCUMENTATION/` | Learner handbook and guides |
| `06_FACILITATOR_AND_MENTOR/` | Facilitator and mentor handbooks |
| `07_PROGRAMME_OPERATIONS/` | Operations and delivery procedures |
| `08_PROJECTS_AND_RESOURCES/` | Project bank and resources |
| `09_ADMINISTRATION/` | Policies (some require legal review) |
| `10_RESEARCH_AND_BENCHMARKING/` | Evidence and source register |
| `11_FINAL_PUBLICATION/` | Derived publication outputs only |

## 3. Document hierarchy

```
DECISION_REGISTER  ──informs──▶  MASTER_PROGRAMME_BLUEPRINT
                                        │ governs
             ┌──────────────────────────┼──────────────────────────┐
     Curricula (02, 03)        Assessment (04)            Policies & operations (07, 09)
             │                          │                          │
     Syllabi & lesson plans ────────────┴──────▶ Handbooks (05, 06) ◀┘
                                        │
                           Final publication (11) — derived only
```

Conflict rule: the higher document prevails unless the decision register records a newer approved decision, in which case the higher document is flagged for update.

## 4. Conventions

### 4.1 Naming
| Type | Convention | Example |
|---|---|---|
| Root control documents | `UPPER_SNAKE_CASE.md` | `DECISION_REGISTER.md` |
| Folders | `NN_UPPER_SNAKE_CASE/` (track folders unnumbered) | `02_COMMON_CORE/` |
| Content documents | `Title_Snake_Case.md` | `Common_Core_Syllabus.md` |
| Weekly documents | `Week_NN_Short_Title.md` | `Week_05_Hybrid_Retrieval.md` |
| Versions | **Never** in filenames (`_v2`, `_final` prohibited) | — |

### 4.2 Document header
Every content document begins with:

```
Document ID | Version | Status | Owner (role) | Last updated (YYYY-MM-DD)
Parent document | Related decisions | Stage of origin
```

Document ID pattern: `ASB-<AREA>-<NNN>` — areas: `GOV` governance, `STR` strategy, `CC` Common Core, `AAE` AI Application, `RAG` RAG & Knowledge, `AGT` Agentic, `EDG` Edge & Offline, `MLF` future ML, `ASM` assessment, `LRN` learner, `FAC` facilitator, `OPS` operations, `PRJ` projects, `ADM` administration, `RES` research, `PUB` publication.

### 4.3 Versioning
- `0.x` draft → `1.0` approved by management → `1.x` minor approved correction → `2.0` structural change (requires a decision register entry).
- Each document ends with a change log. Status values: Draft · Under Review · Approved · Superseded.

### 4.4 Identifiers and cross-references
- Decisions: `AD`, `CD`, `PD`, `GD`, `PR`, `AS`; questions `OQ`; sources `SRC-nnn` (see `10_RESEARCH_AND_BENCHMARKING/`).
- Cite decisions by ID, not paraphrase. State each fact in one place and link to it.
- Use relative Markdown links, e.g. `[Blueprint §16](../MASTER_PROGRAMME_BLUEPRINT.md#16-learning-hours-and-workload)`.

### 4.5 Integrity
No invented partnerships, accreditation, employer commitments, outcomes, statistics, endorsements or learner numbers. Verified facts, assumptions and recommendations are labelled distinctly. Unknowns are labelled **Unknown**.

## Change log

| Version | Date | Change |
|---|---|---|
| 0.1 | 2026-11-16 | Created in Stage 0. |
