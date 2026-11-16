# TRACK 3: AGENTIC AI ENGINEERING — CURRICULUM, SYLLABUS AND WEEKLY LESSON PLANS (WEEKS 5–10)
## Asabiyyah Technologies Global Applied AI Engineering Masterclass

| Field | Value |
|---|---|
| Document ID | ASB-AGT-001 |
| Version | 0.2 Draft (Stage 4 Curriculum + Stage 5 Expanded Lesson Plans) |
| Status | Draft – pending management review |
| Owner (role) | Track 3 Lead Instructor — Agentic AI Engineering (TBC) |
| Last updated | 2026-11-16 |
| Parent document | [MASTER_PROGRAMME_BLUEPRINT.md](../../MASTER_PROGRAMME_BLUEPRINT.md) §12.3 |
| Related decisions | AD-01, AD-02, CD-01, CD-02, **CD-03**, PD-03, PD-04, PD-05, GD-02 |
| Stage of origin | Stage 4 (Specialisation Curriculum) and Stage 5 (Weekly Lesson Plans) |

> **Mandatory Curriculum Decision (CD-03):** This track teaches practical **Model Context Protocol (`MCP`)** implementation—covering MCP architecture (`Hosts`, `Clients`, `Servers`), `Tools`, `Resources`, `Prompts`, capability discovery (`server/discover` & handshakes), tool invocation, authentication/permissions (OAuth 2.1 Resource Server patterns and `2026-07-28` stateless request metadata), error handling, compatibility, and secure execution (OWASP AISVS 1.0 Chapters C9 & C10). Every learner must build, test, evaluate, and secure an **MCP-enabled agentic integration** `[SRC-001, SRC-005, SRC-012, SRC-019]`.

---

## 1. Track overview and target engineering role

- **Track Focus:** Engineering bounded, controllable, auditable AI agents and standardised `MCP` tool/resource integrations that execute complex multi-step workflows without runaway loops or excessive agency.
- **Target Engineering Role:** *Agentic AI Systems Engineer / AI Orchestration & MCP Integration Engineer.*
- **Prerequisites:** Common Core completion (Weeks 1–4) and passing Gate 1 ($\ge 65\%$).

---

## 2. Competency framework and learning outcomes (`SC-AGT`)

| Outcome ID | Measurable Learning Outcome | Bloom Level | Mapped Competencies | Assessment Verification |
|---|---|---|---|---|
| **AGT-LO-1** | Implement a deterministic `ReAct` (`Thought → Action → Observation`) execution loop from scratch in Python with explicit step budgets, timeout ceilings, schema validation, and loop-detection breakers `[SRC-012]`. | Apply / Analyse | `CC-01`, `CC-05`, `SC-AGT` | Week 5 Raw Python ReAct Engine PR |
| **AGT-LO-2** | Model stateful workflows using explicit state graphs (`LangGraph`), persistent checkpointing (`SQLite`), conditional routing, and human-in-the-loop (HITL) interrupt/resume gates `[SRC-019]`. | Apply / Create | `CC-03`, `SC-AGT` | Week 6 Stateful Graph & HITL Checkpoint PR |
| **AGT-LO-3** | Build and test a specification-compliant **Model Context Protocol (`MCP`) Server and Client** exposing typed `Tools`, `Resources`, and `Prompts` over `stdio` and HTTP transports, incorporating capability discovery and protocol version compatibility (`2025-11-25` and `2026-07-28`) (CD-03) `[SRC-005]`. | Apply / Create | `CC-03`, `CC-05`, `SC-AGT` | Week 7 Custom MCP Server & Client Integration PR |
| **AGT-LO-4** | Secure agentic workflows and MCP servers using **OWASP AISVS 1.0 Chapters C9 (Orchestration & Agentic Security) and C10 (MCP Security)** and **OWASP LLM06:2025 (Excessive Agency)**: least-privilege scoped permissions, read-only vs destructive tool annotations, indirect prompt-injection sandboxing, and human approval for state-mutating operations (CD-02, CD-03) `[SRC-001, SRC-002]`. | Analyse / Evaluate | `CC-07`, `SC-AGT` | Week 8 Secure MCP & Agent Red-Team Suite |
| **AGT-LO-5** | Instrument step-level OpenTelemetry agent and MCP spans (`gen_ai.agent.*`, tool call trajectories), evaluate trajectory efficiency and task completion across a 25+ scenario benchmark, and deliver a tested **MCP-Enabled Agentic System & Evaluation Report** (CD-01, CD-03) `[SRC-006, SRC-020]`. | Evaluate / Create | `CC-06`, `CC-08`, `CC-09`, `SC-AGT` | Weeks 9–10 Specialist Project & MCP Evaluation Report (Gate 3) |

---

## 3. Tools, technical requirements, and low-cost accessibility

- **Primary Open-Source Stack:**
  - *Foundational Control Loop:* Pure Python 3.11+ (`asyncio`, `Pydantic v2`, `httpx`) taught first (Principle 8).
  - *State Graph Orchestration:* `LangGraph` with `langgraph-checkpoint-sqlite` (100% local SQLite state persistence) `[SRC-019]` (lightweight alternative: Hugging Face `smolagents` `[SRC-016]`).
  - *Model Context Protocol (CD-03):* Official Python `mcp` SDK (`FastMCP` and low-level server/client primitives) + `MCP Inspector` local debugging tool `[SRC-005]`.
  - *Local Tool-Calling Models:* `Ollama` running `qwen2.5:1.5b-instruct` or `qwen2.5:3b-instruct` / `llama3.2:3b-instruct` (strong native tool-calling support on 8 GB CPU laptops) or `qwen2.5:7b` / `llama3.1:8b` on 16 GB laptops `[SRC-014, SRC-015]`.
  - *Observability & Evaluation:* OpenTelemetry GenAI agent/tool spans (`Arize Phoenix` / JSONL trajectory evaluator) `[SRC-006, SRC-020]`.
- **Anti-Bloat Principle (Principle 9):** Learners do **not** juggle 4 competing agent frameworks. They build a raw Python loop in Week 5, adopt `LangGraph` for stateful checkpointing in Week 6, and standardise all tool/resource integrations on **MCP** in Weeks 7–10. Multi-agent patterns are restricted to justified 2-role supervisor-worker handoffs.

---

## 4. Six-week workload allocation (Weeks 5–10)

Per **PD-03** (`12–15 hours/week`, `72–90 hours total`):

| Week | Title | Live Instructor-Led | Guided Labs | Independent Study | Project Dev & Assessment | Weekly Total |
|---|---|---|---|---|---|---|
| **Week 5** | Agent Architecture, Raw Python ReAct Loops & Bounded Tool Calling | 4.0 h | 3.0 h | 2.5 h | 4.0 h | **13.5 h** |
| **Week 6** | Stateful Workflow Orchestration (`LangGraph`), Memory & Human-in-the-Loop Gates | 4.0 h | 3.0 h | 2.5 h | 4.0 h | **13.5 h** |
| **Week 7** | Model Context Protocol (`MCP`) Architecture: Building Servers, Clients, Tools, Resources & Prompts (CD-03) | 4.0 h | 3.0 h | 2.5 h | 4.5 h | **14.0 h** |
| **Week 8** | MCP Auth, Permissions, Sandboxing & Agentic Security (AISVS C9 & C10 / CD-02, CD-03) | 4.0 h | 3.0 h | 2.5 h | 4.5 h | **14.0 h** |
| **Week 9** | Agent Trajectory Tracing, Failure Recovery, Bounded Multi-Role Patterns & Evaluation (CD-01) | 4.0 h | 3.0 h | 2.5 h | 4.0 h | **13.5 h** |
| **Week 10** | Production MCP-Enabled Agent Delivery, Compatibility Testing & Specialist Defence | 4.0 h | 3.0 h | 2.0 h | 5.0 h | **14.0 h** |
| **Total** | **Track 3 Specialisation (6 Weeks)** | **24.0 h** | **18.0 h** | **14.5 h** | **26.0 h** | **82.5 h** *(within 72–90 h)* |

---

## 5. Detailed Weekly Syllabus and Stage 5 Instructor Lesson Plans (Weeks 5–10)

### WEEK 5: Agent Architecture, Raw Python ReAct Loops & Bounded Tool Calling
- **Time:** 13.5 h (`4.0 h` Live | `3.0 h` Lab | `2.5 h` Independent | `4.0 h` Project)
- **Learning Objectives:** Distinguish deterministic workflows/chains from autonomous tool-calling loops; implement a raw Python `ReAct` execution cycle (`Thought → Action → Observation`) `[SRC-012]` with strict `Pydantic` tool argument validation, `max_steps` budgets, duplicate-call loop detection, and structured error feedback.
- **Instructor-Led Content & Demos (4.0 h):**
  - *Session 5A (2.0 h):* **Explain** when *not* to use an agent (simple classification/extraction) vs when a multi-step tool loop is justified. **Demonstrate** coding a 120-line pure-Python `AgentRunner` from scratch with zero agent frameworks, showing exact message history mutation on each tool call.
  - *Session 5B (2.0 h):* **Explain** failure modes of naive loops (infinite repetition, malformed tool JSON, tool runtime exceptions). **Demonstrate** adding `max_iterations=5`, token budgets, idempotent tool wrappers, and structured error-observation messages that allow the model to self-correct.
- **Guided Practical Lab (3.0 h):** *Lab AGT-05 — Pure Python Bounded ReAct Agent:* Build a local operations diagnostic agent that queries 3 local SQLite/filesystem diagnostic tools, handles simulated tool errors gracefully, and halts deterministically when `max_steps` is reached.
- **Independent Study & Project Work (6.5 h):** Read Yao et al. (*ReAct*, 2023) `[SRC-012]` and Hugging Face Agents Course Unit 1 `[SRC-016]`; design the domain workflow and tool contracts for the Track 3 Specialist Project.
- **Deliverable:** `GitHub PR #5` — Framework-free Python ReAct runner + loop-breaker unit tests.
- **Common Learner Difficulties & Prep Notes:** *Issue:* Returning raw Python stack traces to the LLM when a tool fails, wasting context tokens and leaking internal paths. *Fix:* Catch tool exceptions and return a concise, sanitised `ToolErrorResult(error_code, retryable, hint)` structure.

### WEEK 6: Stateful Workflow Orchestration (`LangGraph`), Checkpointing & Human-in-the-Loop (HITL)
- **Time:** 13.5 h (`4.0 h` Live | `3.0 h` Lab | `2.5 h` Independent | `4.0 h` Project)
- **Learning Objectives:** Transition from raw loops to explicit state machines using `LangGraph` (`StateGraph`, typed state reducers, conditional edges), persist execution checkpoints in local `SQLite`, and enforce **Human-in-the-Loop (`interrupt_before`) approval gates** prior to executing high-impact actions `[SRC-019]`.
- **Instructor-Led Content & Demos (4.0 h):**
  - *Session 6A (2.0 h):* **Explain** why production workflows need inspectable state graphs and durable checkpoints (resuming after a power cut or server restart). **Demonstrate** refactoring the Week 5 Python loop into a typed `LangGraph` `StateGraph` backed by `SqliteSaver`.
  - *Session 6B (2.0 h):* **Explain** Human-in-the-Loop governance (including **NDPA 2023 Section 37** safeguards against solely automated decisions with significant impact `[SRC-007]`). **Demonstrate** pausing graph execution before a state-mutating tool (`issue_refund`, `update_record`), exposing a `FastAPI` approval endpoint, and resuming or rejecting the action with an audit trail.
- **Guided Practical Lab (3.0 h):** *Lab AGT-06 — Checkpointed Graph with Human Approval Gate:* Build a stateful workflow that executes read-only lookups automatically, pauses at an approval checkpoint before any write operation, survives process restarts via SQLite, and resumes upon supervisor sign-off.
- **Independent Study & Project Work (6.5 h):** Implement the stateful graph and SQLite checkpointing architecture for the Track 3 Specialist Project.
- **Deliverable:** `GitHub PR #6` — `LangGraph` workflow with SQLite persistence and tested HITL interrupt/resume flow.
- **Common Learner Difficulties & Prep Notes:** *Issue:* Mutating graph state in-place instead of returning state updates via typed reducers. *Fix:* Enforce immutable `TypedDict`/`Pydantic` state updates and unit-test each graph node in isolation.

### WEEK 7: Model Context Protocol (`MCP`) Architecture: Servers, Clients, Tools, Resources & Prompts (CD-03)
- **Time:** 14.0 h (`4.0 h` Live | `3.0 h` Lab | `2.5 h` Independent | `4.5 h` Project)
- **Learning Objectives:** Master the **Model Context Protocol (`MCP`)** architecture (`Hosts`, `Clients`, `Servers`), implement custom MCP servers exposing `Tools` (with read-only/destructive annotations), `Resources` (static & URI-templated data), and `Prompts`, and build an MCP client that performs capability discovery (`server/discover` & initialization) and invokes tools across `stdio` and HTTP transports (CD-03) `[SRC-005, SRC-016]`.
- **Instructor-Led Content & Demos (4.0 h):**
  - *Session 7A (2.0 h):* **Explain** the $M \times N$ integration problem solved by MCP, JSON-RPC 2.0 message framing, and the three core server primitives (`Tools` = model-controlled actions; `Resources` = application/context data; `Prompts` = reusable templates) `[SRC-005]`. **Explain** protocol evolution from stateful `2025-03-26`/`2025-11-25` sessions to the **`2026-07-28` stateless architecture** (`MCP-Protocol-Version` / `_meta` per-request metadata, `Mcp-Method`/`Mcp-Name` routing headers, and `server/discover`) `[SRC-005]`. **Demonstrate** building an MCP Server in Python (`mcp` SDK) and inspecting it live with `MCP Inspector`.
  - *Session 7B (2.0 h):* **Demonstrate** building a Python MCP Client that connects to the MCP Server over both local `stdio` and HTTP, discovers available tools/resources dynamically, binds them into the Week 6 `LangGraph` agent, and handles structured tool outputs and resource links.
- **Guided Practical Lab (3.0 h):** *Lab AGT-07 — Custom End-to-End MCP Server & Agent Client (CD-03):* Build an MCP Server wrapping a local SQLite business database and document store (exposing 3 `Tools` with `readOnlyHint`/`destructiveHint` annotations, 2 URI-templated `Resources`, and 1 diagnostic `Prompt`); connect the Week 6 agent via an MCP Client and verify full capability discovery and invocation.
- **Independent Study & Project Work (7.0 h):** Complete the Hugging Face MCP Course core units `[SRC-016]`; build the custom MCP Server and Client integration for the Track 3 Specialist Project.
- **Deliverable:** `GitHub PR #7` — Working MCP Server + MCP Client + automated protocol integration test suite.
- **Common Learner Difficulties & Prep Notes:** *Issue:* Printing debug logs to `stdout` inside a `stdio`-transport MCP server, which corrupts JSON-RPC frames. *Fix:* Emphasise that `stdio` MCP servers must log exclusively to `stderr` or a file.

### WEEK 8: MCP Authentication, Permissions, Sandboxing & Agentic Security (AISVS C9 & C10 / CD-02, CD-03)
- **Time:** 14.0 h (`4.0 h` Live | `3.0 h` Lab | `2.5 h` Independent | `4.5 h` Project)
- **Learning Objectives:** Apply **OWASP AISVS 1.0 Chapter C9 (Orchestration & Agentic Security)** and **Chapter C10 (Model Context Protocol Security)** along with **OWASP LLM01:2025 (Indirect Prompt Injection)** and **LLM06:2025 (Excessive Agency)**: implement OAuth 2.1 / token-scoped permissions on MCP servers, prevent "confused deputy" and tool-poisoning attacks, enforce strict path/SQL/command sandboxing, and require human confirmation for destructive MCP tools `[SRC-001, SRC-002, SRC-005]`.
- **Instructor-Led Content & Demos (4.0 h):**
  - *Session 8A (2.0 h):* **Explain** MCP & Agentic threat vectors mapped to **AISVS C9 & C10**:
    1. *Indirect Prompt Injection via MCP Resources:* Untrusted external data instructing the agent to call a destructive tool.
    2. *MCP Tool Poisoning / Rug-Pulls:* Malicious instructions hidden inside tool descriptions or untrusted third-party MCP servers.
    3. *Confused Deputy & Excessive Agency (LLM06):* An MCP server executing actions with broad system credentials instead of the caller's scoped permissions.
    **Demonstrate** live exploitation of an unguarded MCP agent and step-by-step hardening.
  - *Session 8B (2.0 h):* **Explain** MCP authorization standards (OAuth 2.1 Resource Server classification, scope validation, `WWW-Authenticate` incremental consent, and header-based gateway policies in `2026-07-28`) `[SRC-005]`. **Demonstrate** implementing scoped bearer-token validation (`mcp:tools:read` vs `mcp:tools:write`), filesystem/SQL parameterisation sandboxes, and automatic HITL gating whenever an MCP tool carries `destructiveHint=True`.
- **Guided Practical Lab (3.0 h):** *Lab AGT-08 — Hardening MCP Servers & Red-Teaming Excessive Agency:* Add scoped token authorization, parameter allowlists, path-traversal prevention, and destructive-tool HITL gates to the Week 7 MCP Server/Client; run a 12-case adversarial attack suite (indirect injection via resource content, unauthorized scope escalation, SQLi/path traversal via tool args).
- **Independent Study & Project Work (7.0 h):** Implement full AISVS C2/C5/C7/C9/C10/C12 security controls and adversarial tests in the Track 3 Specialist Project.
- **Deliverable:** `GitHub PR #8` — Hardened MCP Server/Client + AISVS C9/C10 verification checklist + passing red-team test suite.
- **Common Learner Difficulties & Prep Notes:** *Issue:* Passing raw user strings into shell or dynamic SQL inside an MCP tool. *Fix:* Ban `shell=True` and raw string SQL interpolation across all course repos; enforce parameterised queries and strict `Pydantic` allowlists.

### WEEK 9: Agent Trajectory Tracing, Failure Recovery, Bounded Multi-Role Handoffs & Evaluation (CD-01)
- **Time:** 13.5 h (`4.0 h` Live | `3.0 h` Lab | `2.5 h` Independent | `4.0 h` Project)
- **Learning Objectives:** Instrument full agent and MCP execution trajectories using **OpenTelemetry GenAI** (`gen_ai.agent.name`, tool call spans, MCP request/response metadata) `[SRC-006]`, implement graceful fallback/recovery policies, evaluate when a 2-role Supervisor-Worker pattern is justified vs single-agent execution, and benchmark the agent on a 25+ scenario evaluation dataset (CD-01).
- **Instructor-Led Content & Demos (4.0 h):**
  - *Session 9A (2.0 h):* **Explain** agent evaluation metrics beyond final answer text: **Task Completion Rate**, **Tool Selection Accuracy**, **Trajectory Efficiency** ($\text{actual steps} / \text{optimal steps}$), **Invalid Tool Call Rate**, **Safety Gate Compliance**, total token cost, and end-to-end latency. **Demonstrate** tracing multi-step MCP calls in `Arize Phoenix` `[SRC-020]`.
  - *Session 9B (2.0 h):* **Explain** disciplined multi-agent design—why unconstrained 4-agent chat loops fail on CPU/token budgets, and how to implement a clean, bounded **2-role Router/Supervisor $\rightarrow$ Specialist Worker handoff** only when tool sets exceed 10–15 tools.
- **Guided Practical Lab (3.0 h):** *Lab AGT-09 — Trajectory Evaluation & Failure Analysis:* Run a 25-scenario evaluation harness (`evals/run_agent_eval.py`) against the MCP-enabled agent, recording step-by-step trajectories, computing tool-call precision/efficiency, and diagnosing the top 3 trajectory failures from OpenTelemetry traces.
- **Independent Study & Project Work (6.5 h):** Execute the 25+ scenario evaluation benchmark on the Specialist Project and compile the **Track 3 Agent & MCP Evaluation Report**.
- **Deliverable:** `GitHub PR #9` — 25-scenario trajectory evaluation suite, OpenTelemetry trace export, and failure taxonomy.
- **Common Learner Difficulties & Prep Notes:** *Issue:* Giving a single 3B local model 20+ complex tools at once, degrading tool selection accuracy. *Fix:* Demonstrate dynamic tool filtering or a 2-way domain router that exposes at most 4–6 relevant MCP tools per step.

### WEEK 10: Production MCP-Enabled Agent Delivery, Compatibility Testing & Specialist Defence
- **Time:** 14.0 h (`4.0 h` Live | `3.0 h` Lab | `2.0 h` Independent | `5.0 h` Project)
- **Learning Objectives:** Package the MCP Server and Agent Orchestrator as reproducible services (`FastAPI` + `Docker`), verify protocol compatibility and error recovery when an MCP server is slow or offline, and defend the **Track 3 Specialist Project** (Gate 3).
- **Instructor-Led Content & Demos (4.0 h):**
  - *Session 10A (2.0 h):* **Explain** production packaging of MCP servers and integration patterns for Week 11 cross-functional capstone teams (how Track 3's MCP server wraps Track 2's Hybrid RAG engine as an MCP `Tool`/`Resource` and exposes safe agentic workflows to Track 1's web backend).
  - *Session 10B (2.0 h):* **Demonstrate** live Track 3 Specialist Project defences, MCP Inspector verification, and Gate 3 rubric reviews.
- **Guided Practical Lab (3.0 h):** *Lab AGT-10 — Clean-Room MCP Interoperability & Fault Test:* Test the student's MCP Server against a standard reference MCP Client test harness (verifying discovery, valid/invalid tool calls, permission rejection, and timeout recovery).
- **Project Deliverable (Gate 3 — Track 3 Specialist Project Package):**
  1. **MCP-Enabled Agentic System Repository** (Custom MCP Server exposing `Tools`, `Resources`, `Prompts`; MCP Client + `LangGraph` stateful agent with SQLite checkpointing and HITL approval gate; `FastAPI` interface; `Dockerfile`; `pytest` suite).
  2. **Agentic & MCP Evaluation and Security Report (Mandatory — CD-01, CD-02, CD-03)**:
     - 25+ scenario benchmark results (Task Completion Rate, Tool Selection Accuracy, Trajectory Efficiency, Latency $p_{50}/p_{95}$, Token Cost).
     - MCP capability, compatibility, and fault-recovery test log.
     - **OWASP AISVS 1.0 Security Verification (Chapters C2, C5, C7, C9 Orchestration & Agentic Security, C10 MCP Security, C12 Logging)** + adversarial red-team results and mandatory non-certification disclaimer.
- **Assessment Rubric (Gate 3 — 25% of Programme Grade):**
  - *Agent Architecture, Stateful Checkpointing (`LangGraph`) & HITL Governance:* 25%
  - *MCP Server & Client Implementation (`Tools`, `Resources`, `Prompts`, Discovery — CD-03):* 30%
  - *Trajectory Evaluation Dataset, Metrics & OpenTelemetry Tracing (CD-01):* 25%
  - *Agentic & MCP Security Controls (AISVS C9 & C10 — CD-02, CD-03) & Code Quality:* 20%

---

## 6. Curated free learning resources (Track 3)

1. **Model Context Protocol (MCP) Official Specification & Python SDK** — https://modelcontextprotocol.io/specification `[SRC-005]`
2. **Hugging Face Free AI Agents Course & Official MCP Course** — https://huggingface.co/learn `[SRC-016]`
3. **LangGraph Official Documentation & Conceptual Guides** — https://langchain-ai.github.io/langgraph/ `[SRC-019]`
4. **Yao et al. (2023), *ReAct: Synergizing Reasoning and Acting in Language Models*** — https://arxiv.org/abs/2210.03629 `[SRC-012]`
5. **OWASP AISVS 1.0 (Chapter C9: Orchestration & Agentic Security; Chapter C10: MCP Security) & OWASP LLM06:2025** `[SRC-001, SRC-002]`

---

## Change log

| Version | Date | Change |
|---|---|---|
| 0.1 | 2026-11-16 | Track 3 curriculum drafted incorporating CD-03 and verified 2025–2026 MCP specs (Stage 4). |
| 0.2 | 2026-11-16 | Integrated full Stage 5 weekly lesson plans, MCP labs, AISVS C9/C10 security labs, and Gate 3 rubric (GD-02b). |
