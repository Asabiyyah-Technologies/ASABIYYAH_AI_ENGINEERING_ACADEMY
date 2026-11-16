# FUTURE SPECIALISATION CONCEPT NOTE: MACHINE LEARNING ENGINEERING
## Asabiyyah Technologies Global Applied AI Engineering Masterclass

| Field | Value |
|---|---|
| Document ID | ASB-MLF-001 |
| Version | 0.1 Draft |
| Status | **FUTURE EXPANSION ONLY — NOT AN ACTIVE INITIAL TRACK (AD-03)** |
| Owner (role) | Programme Director (TBC) |
| Last updated | 2026-11-16 |
| Parent document | [MASTER_PROGRAMME_BLUEPRINT.md](../../MASTER_PROGRAMME_BLUEPRINT.md) §22.2 |
| Related decisions | AD-01, AD-02, **AD-03** |
| Stage of origin | Stage 4 |

> **Governance Warning (AD-03):** Machine Learning Engineering is **not** an active specialisation in the initial four-track delivery model of the Asabiyyah Technologies Global Applied AI Engineering Masterclass. It must **not** be advertised as an active Cohort 1 track, scheduled in Weeks 5–10, or assigned learners until management formally approves its activation and compute provisioning in [DECISION_REGISTER.md](../../DECISION_REGISTER.md).

---

## 1. Strategic rationale for deferral to a future phase

The initial four tracks (AI Application Engineering, RAG & Knowledge Engineering, Agentic AI Engineering, and Edge & Offline AI Engineering) focus on **building, grounding, orchestrating, evaluating, securing, and deploying systems around pre-trained and quantised open-weight models**—capabilities that make up the vast majority of immediate industry demand and can be executed 100% on modest 8 GB–16 GB CPU laptops without paid GPUs (PD-04).

By contrast, a rigorous **Machine Learning Engineering (MLE)** specialisation requires training classical models on large tabular/domain datasets and executing Parameter-Efficient Fine-Tuning (`PEFT` / `LoRA` / `QLoRA`) and preference alignment (`DPO`) on neural weights. While small demos can run on free cloud T4 GPUs, reliable cohort-wide instruction under Nigerian power and bandwidth constraints requires pre-negotiated cloud GPU credits or dedicated local compute nodes. Deferring MLE to Phase 2 preserves hardware accessibility and technical honesty in Cohort 1.

---

## 2. Proposed scope for future activation (Weeks 5–10 equivalent)

When authorised for a future cohort, the 6-week **Machine Learning Engineering** track is envisioned to cover:
1. **Week 5 — Data Curation, Feature Engineering & Labelling Pipelines:** Dataset versioning, data leakage prevention, synthetic data validation, and OWASP AISVS 1.0 **Chapter C1 (Training Data Integrity & Traceability)** `[SRC-001]`.
2. **Week 6 — Classical ML Systems & Tabular Production Baselines:** Gradient-boosted decision trees (`LightGBM` / `XGBoost` / `scikit-learn`), calibration, class imbalance, and when classical ML outperforms LLMs on cost and latency.
3. **Week 7 — Parameter-Efficient Fine-Tuning (`LoRA` & `QLoRA`):** Instruction-tuning compact open-weight models (1.5B–7B) for domain formatting, Nigerian language adaptation, or specialised tool calling.
4. **Week 8 — Experiment Tracking, Model Registry & Supply-Chain Security:** Reproducible training runs (`MLflow` / open-source registries), safe weight serialisation (`safetensors` / `GGUF` conversion), and AISVS **Chapter C3 (Model Lifecycle)** & **Chapter C11 (Adversarial Robustness)** `[SRC-001]`.
5. **Week 9 — Post-Training Evaluation, Bias Auditing & Regression Testing (CD-01):** Comparing base vs fine-tuned checkpoints on held-out golden benchmarks, calibration drift, and catastrophic forgetting analysis.
6. **Week 10 — Model Export, Quantisation Hand-Off & Serving:** Exporting fine-tuned adapters to `GGUF` / `ONNX` for deployment via Track 1 (Application API) or Track 4 (Edge Runtime).

---

## 3. Prerequisites required before management activation

Before this track can be moved from *Future Expansion* to *Active*, three operational gates must be met:
1. **Verified Compute Provisioning:** Guaranteed zero-cost learner access to reproducible GPU compute (e.g., sponsored cloud GPU workspaces or scheduled burst instances) with offline checkpoint resumption.
2. **Elevated Mathematics & Data Baseline:** An updated entry diagnostic verifying linear algebra, probability distributions, loss functions, and gradient descent fundamentals.
3. **Formal Management Approval:** A new `AD-` entry in `DECISION_REGISTER.md` authorising full Stage 4/5 curriculum and lab development.

---

## Change log

| Version | Date | Change |
|---|---|---|
| 0.1 | 2026-11-16 | Strategic concept note created in Stage 4 per AD-03. |
