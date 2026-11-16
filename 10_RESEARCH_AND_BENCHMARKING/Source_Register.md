# SOURCE REGISTER — GLOBAL RESEARCH AND BENCHMARKING

| Field | Value |
|---|---|
| Document ID | ASB-RES-002 |
| Version | 0.1 Draft |
| Status | Draft – pending management review |
| Owner (role) | Curriculum Research Lead (TBC) |
| Last updated | 2026-11-16 |
| Parent document | [Global_Research_and_Benchmarking_Report.md](Global_Research_and_Benchmarking_Report.md) |
| Related decisions | AD-01–03, CD-01–05, PD-03–05 |
| Stage of origin | Stage 1 |

## Purpose and verification rules

This register records all primary standards, specifications, peer-reviewed papers, technical documentation and benchmark educational resources cited in [Global_Research_and_Benchmarking_Report.md](Global_Research_and_Benchmarking_Report.md).

- **Verified (Primary):** Confirmed directly against the issuing organisation's specification, standard, repository or peer-reviewed publication.
- **Secondary:** Confirmed via reputable technical documentation or secondary summary where the primary document is syndicated.
- All sources were verified or accessed on **2026-11-16**.

---

## Source inventory

| ID | Title | Organisation / Authors | Publication / Release Date | Direct URL | Verification Level | Curriculum Relevance |
|---|---|---|---|---|---|---|
| SRC-001 | OWASP Artificial Intelligence Security Verification Standard (AISVS) v1.0 | OWASP Foundation | June 2026 | https://owasp.org/www-project-artificial-intelligence-security-verification-standard/ | Verified (Primary) | Core reference for CD-02; defines 12 chapters (C1–C12) and 3 appendices for proportionate capstone security verification. |
| SRC-002 | OWASP Top 10 for Large Language Model Applications (2025) | OWASP Foundation | November 2024 (v2025 release) | https://owasp.org/www-project-top-10-for-large-language-model-applications/ | Verified (Primary) | Foundational threat taxonomy (LLM01 Prompt Injection, LLM06 Excessive Agency, LLM07 System Prompt Leakage, LLM08 Vector & Embedding Weaknesses, LLM10 Unbounded Consumption). |
| SRC-003 | Artificial Intelligence Risk Management Framework (AI RMF 1.0, NIST AI 100-1) | National Institute of Standards and Technology (NIST) | January 2023 | https://www.nist.gov/itl/ai-risk-management-framework | Verified (Primary) | Governance, mapping, measuring and managing AI risks; underpins CD-01 and responsible AI in Common Core. |
| SRC-004 | Artificial Intelligence Risk Management Framework: Generative Artificial Intelligence Profile (NIST AI 600-1) | NIST | July 2024 | https://doi.org/10.6028/NIST.AI.600-1 | Verified (Primary) | GenAI-specific risk taxonomy (confabulation, data privacy, information integrity, value-chain/component integration). |
| SRC-005 | Model Context Protocol (MCP) Specification — Revisions 2025-03-26, 2025-06-18, 2025-11-25, and 2026-07-28 | Model Context Protocol Project / Linux Foundation | March 2025 – July 2026 | https://modelcontextprotocol.io/specification | Verified (Primary) | Core specification for CD-03 (Agentic AI track): clients, servers, tools, resources, prompts, OAuth 2.1 resource server auth, and 2026-07-28 stateless request/discovery evolution. |
| SRC-006 | OpenTelemetry Semantic Conventions for Generative AI (`open-telemetry/semantic-conventions-genai`) | OpenTelemetry / Cloud Native Computing Foundation (CNCF) | June 2026 (spun out at v1.42.0; status: Development) | https://opentelemetry.io/docs/specs/semconv/gen-ai/ | Verified (Primary) | Standardises telemetry attributes (`gen_ai.provider.name`, `gen_ai.operation.name`, `gen_ai.usage.*`, agent and MCP spans) for CD-01 observability. |
| SRC-007 | Nigeria Data Protection Act (NDPA) 2023 & NDPC Regulatory Guidance | Federal Republic of Nigeria / Nigeria Data Protection Commission (NDPC) | June 2023 (in force) | https://ndpc.gov.ng/ | Verified (Primary) | Legal baseline for Nigerian delivery: s.24 principles, s.25 lawful basis, s.28 DPIA for high-risk technologies (including AI), s.37 rights regarding automated decision-making. |
| SRC-008 | Okapi at TREC-3 & The Probabilistic Relevance Framework: BM25 and Beyond | Robertson, S. E., & Zaragoza, H. (*Foundations and Trends in Information Retrieval*, 3(4), 333–389) | 2009 (orig. 1994) | https://doi.org/10.1561/1500000019 | Verified (Primary) | Theoretical and algorithmic baseline for lexical retrieval (BM25) in CD-04 (RAG track). |
| SRC-009 | Reciprocal Rank Fusion Outperforms Condorcet and Individual Rank Learning Methods | Cormack, G. V., Clarke, C. L. A., & Büttcher, S. (*SIGIR '09*, pp. 758–759) | July 2009 | https://doi.org/10.1145/1571941.1572114 | Verified (Primary) | Defines Reciprocal Rank Fusion ($RRF\_score(d) = \sum \frac{1}{k + r(d)}$, typically $k=60$) required by CD-04. |
| SRC-010 | Retrieval-Augmented Generation for Knowledge-Intensive NLP Tasks | Lewis, P., et al. (*Advances in Neural Information Processing Systems*, 33) | 2020 | https://arxiv.org/abs/2005.11401 | Verified (Primary) | Foundational architecture for RAG systems (Track 2). |
| SRC-011 | RAGAS: Automated Evaluation of Retrieval Augmented Generation | Es, S., James, J., Espinosa-Anke, L., & Schockaert, S. (*EACL 2024 System Demonstrations*) | 2023 / 2024 | https://arxiv.org/abs/2309.15217 | Verified (Primary) | Reference metrics for retrieval and generation evaluation (context precision/recall, faithfulness, answer relevance) supporting CD-01 and CD-04. |
| SRC-012 | ReAct: Synergizing Reasoning and Acting in Language Models | Yao, S., et al. (*ICLR 2023*) | March 2023 | https://arxiv.org/abs/2210.03629 | Verified (Primary) | Foundational reasoning-and-acting execution loop taught before introducing agent orchestration frameworks (Track 3). |
| SRC-013 | Judging LLM-as-a-Judge with MT-Bench and Chatbot Arena | Zheng, L., et al. (*NeurIPS 2023 Datasets and Benchmarks*) | 2023 | https://arxiv.org/abs/2306.05685 | Verified (Primary) | Establishes methodology and biases (position, verbosity, self-enhancement) of LLM-as-a-judge evaluation (CD-01). |
| SRC-014 | `llama.cpp` and GGUF Specification (`ggml-org/llama.cpp`, `llama-bench`, `llama-perplexity`) | Gerganov, G., & ggml-org contributors | Continuous (2023–2026) | https://github.com/ggml-org/llama.cpp | Verified (Primary) | Primary engine and binary format (GGUF) for CPU/hybrid quantised inference and reproducible benchmarking (`llama-bench`) in Track 4 (CD-05). |
| SRC-015 | Ollama Documentation and Model Library | Ollama | Continuous (2023–2026) | https://ollama.com/ | Verified (Primary) | Accessible local model runner wrapping `llama.cpp` with an OpenAI-compatible HTTP API for local development across all tracks. |
| SRC-016 | Hugging Face Open-Source Courses (NLP/LLM Course, Agents Course, MCP Course) & `transformers` / `sentence-transformers` Docs | Hugging Face | 2024–2026 | https://huggingface.co/learn | Verified (Primary) | Open educational benchmark and primary hub for open-weight models, embeddings (`sentence-transformers`), rerankers and datasets. |
| SRC-017 | DeepLearning.AI Short Courses & AI Engineering Curriculum Benchmarks (ChatGPT Prompt Engineering, Building & Evaluating Advanced RAG, AI Agents in LangGraph, LLMOps) | DeepLearning.AI | 2023–2026 | https://www.deeplearning.ai/courses/ | Verified (Primary) | Industry benchmark for modular applied AI topics; highlights gap between 1–2 hour topic courses and integrated 14-week product engineering. |
| SRC-018 | FastAPI & Pydantic v2 Official Documentation | Sebastián Ramírez / Pydantic Services | Continuous (2023–2026) | https://fastapi.tiangolo.com/ ; https://docs.pydantic.dev/ | Verified (Primary) | Core Python backend and schema-validation stack for Track 1 and Common Core. |
| SRC-019 | LangGraph Documentation (Stateful Agent Orchestration) | LangChain Inc. | 2024–2026 | https://langchain-ai.github.io/langgraph/ | Verified (Primary) | Graph-based stateful orchestration option for Track 3 (introduced only after raw Python control loops are mastered). |
| SRC-020 | Arize Phoenix & OpenInference Open-Source AI Observability | Arize AI | 2024–2026 | https://docs.arize.com/phoenix | Verified (Primary) | Open-source, local-capable OpenTelemetry-based tracing and evaluation workbench suitable for zero-cost offline/local labs (CD-01). |
| SRC-021 | Promptfoo Open-Source LLM Evaluation & Red-Teaming CLI | Promptfoo | 2023–2026 | https://www.promptfoo.dev/docs/intro/ | Verified (Primary) | Local-first CLI for declarative evaluation datasets, regression testing, and OWASP LLM security testing (CD-01, CD-02). |
| SRC-022 | Qdrant & Chroma Open-Source Vector Databases + `rank-bm25` / SQLite FTS5 | Qdrant / Chroma / SQLite | Continuous (2023–2026) | https://qdrant.tech/documentation/ ; https://www.sqlite.org/fts5.html | Verified (Primary) | Local-capable vector and lexical storage engines for hybrid retrieval and metadata filtering (CD-04). |
| SRC-023 | Stanford CS224N / CS324 (Large Language Models) & Linux Foundation AI & Data Benchmarks | Stanford University / Linux Foundation | 2023–2026 | https://web.stanford.edu/class/cs224n/ ; https://lfaidata.foundation/ | Secondary | Academic and open-governance reference points contrasting theoretical ML depth with applied systems engineering. |
| SRC-024 | Microsoft Learn ("Generative AI for Beginners" / Azure AI Studio) & AWS / Google Cloud GenAI Architecture Guides | Microsoft / AWS / Google Cloud | 2024–2026 | https://learn.microsoft.com/en-us/training/ | Verified (Primary) | Cloud hyperscaler curriculum benchmarks; demonstrates heavy cloud lock-in that Asabiyyah intentionally avoids. |

## Change log

| Version | Date | Change |
|---|---|---|
| 0.1 | 2026-11-16 | Initial source register compiled and verified in Stage 1. |
