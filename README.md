<h1 align="center">Hi 🐯, I'm Priyanshu Deshmukh</h1>
<h3 align="center">AI Engineer | India 🇮🇳</h3>
<p align="center">
  <a href="https://github.com/ryo-ma/github-profile-trophy">
    <img src="https://github-profile-trophy-l1o7p9opu-ryo-ma-s-team.vercel.app/?username=priyansh4320" alt="GitHub Trophies" />
  </a>
</p>


# Priyanshu Deshmukh

**AI Engineer & Maintainer @ [AG2 (AutoGen)](https://github.com/ag2ai/ag2)**

Building production-scale multi-agent systems and enterprise AI architectures. Contributing to AG2, the leading open-source multi-agent conversation framework serving 20,000+ developers globally.

**Contact:** priyanshudeshmukh4@gmail.com | [Link](https://www.linkedin.com/in/priyanshudeshmukh/) | Hyderabad, India

---

## Current Work

**AG2 (AutoGen) — AI Engineer & Maintainer**

**Jul 2025 – Present**

Core maintainer and AI systems engineer for AG2’s multi-agent orchestration platform. Owned integration of frontier LLM capabilities (GPT-5 series), production-grade tooling for safe code edits, concurrency-safe agent runtimes, and document-scale RAG capabilities. Drove refactors that improved agent correctness, observability, and throughput while producing tutorials and docs that accelerated adoption.

---

**1) GPT-5 series, `apply_patch` & shell-tool support (Top-priority — hiring signal)**

* **GPT-5 & GPT-5.2 model enablement** — Added full GPT-5.2 model support and reasoning-effort configuration so AG2 agents can use higher-fidelity reasoning modes (including `xhigh`) and the Responses API when required. This work updated model enums, pricing/effort mappings, and the responses client to accept new parameters. 🔗 PR [#2250]. ([GitHub][1])
  *Why it matters:* Enables hiring teams to see you shipped forward-compatible LLM support and reasoning controls used in production agent decision-making.

* **GPT-5.1 `apply_patch` tool support (Responses API)** — Implemented support for GPT-5.1’s `apply_patch` tool (V4A diff/patch format) enabling agents to emit structured, actionable multi-file diffs that can be programmatically applied (safe autonomous refactoring, targeted bugfix patches, CI-friendly edits). Also delivered example tutorial/notebook to demonstrate the pattern. 🔗 PR [#2213]. ([GitHub][2])
  *Tech & skills:* tool-calling design, structured output parsing, patch application safety, tests for diff format handling.
  *Hiring signal:* shows you built automation that replaces brittle text-based code gen with auditable, deterministic edit operations.

* **Shell tool / tool concurrency support** — Implemented shell/tool execution improvements so agent tool calls (including shell) are concurrency-safe and return machine-parseable structured outputs for chaining. This reduced deadlocks/race conditions in pipeline runs and made tool outputs deterministic for planners. 🔗 PR reference: shell/tool work collection (see PR list). ([GitHub][3])
  *Tech & skills:* concurrency safety, tool contract design, deterministic output formats.

---

**2) Provider & infra resilience (Bedrock, Gemini, Ollama)**

* **AWS Bedrock resilience & structured outputs** — Added exponential backoff and retry strategies at the Bedrock provider layer and Bedrock structured-output handling so transient failures don’t cascade into agent crashes and downstream parsers consistently receive JSON/structured responses. 🔗 PR [#2292] (mentioned across PRs/listings).
  *Why it matters:* Production readiness for enterprise clouds.

* **Gemini: ThinkingConfig / reasoning controls** — Extended ThinkingConfig support to Gemini models so AG2 can control depth/latency of Gemini reasoning and capture "thought signatures" for better traceability in multi-step planning. 🔗 PR [#2254]. ([GitHub][4])
  *Tech & skills:* provider abstraction, reasoning controls, cross-provider parity.

* **Ollama validation fixes** — Fixed LLMConfig validation paths that previously caused runtime errors when `native_tool_calls` were enabled, preventing misconfiguration crashes. 🔗 PR [#1951].
  *Skills:* config validation, cross-provider stability.

---

**3) DocAgent — architecture, dynamic RAG, and high-throughput document workflows**

* **DocAgent architecture optimization (threading, concurrent ingest, supervisor)** — Simplified and optimized DocAgent internals: added a `ThreadPoolExecutor` for tool execution, a pseudo-supervisor for task orchestration, concurrent document ingestion, citation support, and flexible inner-agent prompting to greatly improve ingestion throughput and query latency. 🔗 PR [#2097]. ([GitHub][5])
  *Technical highlights:* concurrent ingestion pipelines, thread pools for I/O-bound tasks, scalable supervisor pattern, test scenarios for long-document ingestion.

* **Dynamic RAG (Vector + Graph / Neo4j integration + aggregator)** — Extended DocAgent beyond vector RAG by adding Graph RAG support (Neo4j) and a dynamic `rag_config` to select/aggregate results from vector and graph retrievals. This enables multi-hop, relationship-aware queries and a result aggregator for combined RAG outputs. 🔗 PR [#2105]. ([GitHub][6])
  *Why it matters:* Demonstrates system design for hybrid retrieval (vector + graph) and shows you enabled sub-second, multi-hop retrieval patterns valuable in enterprise search.

---

**4) Agent runtime refactors, networking & message model improvements**

* **ConversableAgent refactor (message flow & API consistency)** — Refactored ConversableAgent internals to enforce consistent message list APIs, clarify state transitions, and improve extensibility for multi-turn scenarios. 🔗 PR [#2086]. ([GitHub][7])
  *Skills:* API design, state-machine clarity, multi-turn correctness.

* **Agent networking / list[messages] API enforcement** — Standardized `list[messages]` semantics across agent messaging, improving inter-agent communication and easing integration with group chat / networking scenarios. 🔗 PR [#2081]. ([GitHub][8])

* **ParallelAgentRunner / concurrency orchestration** — Built `ParallelAgentRunner` to run agents in parallel safely (thread/process coordination, result aggregation, cancellation semantics), improving throughput for batched workflows. 🔗 PR [#2143]. ([GitHub][9])
  *Tech & skills:* concurrency patterns, cancellation semantics, thread-safe result aggregation.


**5) Reliability, fixes & dependency hygiene**

* **Memory / long-context stability** — Replaced brittle long-context paths and added safer concurrency patterns to avoid context overwrites in document agents (used in the DocAgent refactors above). (See DocAgent PRs #2097 / #2105.) ([GitHub][5])

* **Dependency & resolver hardening** — Switched pinned dependencies to ranges where appropriate and fixed async validation issues across providers to reduce release friction and unexpected breakages. (Referenced across PR list.)


**6) Docs, tutorials & community enablement**

* **Apply-patch tutorial & notebook** — Published a tutorial demonstrating GPT-5.1 `apply_patch` flows in AG2 to help integrators build safe code-editing agents (linked from release notes). 🔗 PR [#2213] (release notes & tutorial). ([GitHub][2])

* **DocAgent & Dynamic RAG notebooks** — Added sample notebooks showing concurrent ingestion, dynamic RAG configuration, and example runs — useful in interviews and technical screen walkthroughs. 🔗 PRs [#2097], [#2105]. ([GitHub][5])

* **Developer DX (devcontainer, logging, hooks)** — Added a Python 3.14 devcontainer to standardize contributor environments and documented lifecycle hooks (`process_message_before_send`) so downstream teams can plug custom logic into message pipelines.

---

## Previous Experience

**Alvyl Consulting** - Software Engineer (AI) (Aug 2024 - Jul 2025)

Architected FusionSecurity.ai, an enterprise-grade multi-agent security intelligence platform for Fortune 500 clients:

- Designed LangGraph-powered architecture with specialized role-based agents processing daily security events with high uptime
- Implemented hierarchical Supervisor Agent orchestration distributing tasks across 15+ specialized sub-agents in containerized AWS/Kubernetes environments
- Engineered multi-modal RAG system combining vector search, graph relationships, and structured data analysis
- Built self-evolving threat intelligence database with dynamic schema expansion
- Deployed containerized microservices supporting mission-critical security monitoring
- Integrated Semgrep SAST scanning in CI/CD pipelines
- Developed multi-cloud metadata analysis agents for AWS/Azure/GCP compliance monitoring

**Freelance AI/ML Solutions Architect** (2022 - 2024)

Delivered AI transformation solutions for BlackCoffer, Digipplus, PrecilyAI, and UniAcco. Built scalable ML pipelines with end-to-end MLOps integration.

---

## Technical Expertise

**Core Competencies**
- Multi-Agent Orchestration (AG2/AutoGen, LangGraph)
- Advanced RAG Systems (Vector, Graph, Structured)
- LLM Integration & Prompt Engineering
- Enterprise AI Security & Automation

**Infrastructure & Tools**
- Cloud Platforms: AWS, Azure, GCP, Kubernetes
- Databases: Neo4j, Vector Databases
- Security: Semgrep, SAST Integration
- CI/CD & MLOps Pipelines

**Architecture**
- Cloud-Native Microservices
- Production AI Systems
- Performance Engineering
- Security Intelligence Platforms

---

## Publications & Impact

- Published IEEE research on AI systems
- Contributing to framework serving 20,000+ developers
- Mentored 50+ community developers on multi-agent architecture
- Open-source contributions to AG2 core development

---

**Building intelligent systems that bridge cutting-edge AI research with production deployment.**
---

### 📫 Reach Me At:
- LinkedIn: [linkedin.com/in/priyanshudeshmukh](https://www.linkedin.com/in/priyanshudeshmukh/)
- priyanshudeshmukh4@gmail.com

---

### 🔗 Connect with Me:
<p align="left">
  <a href="https://www.linkedin.com/in/priyanshudeshmukh/" target="_blank">
    <img src="https://raw.githubusercontent.com/rahuldkjain/github-profile-readme-generator/master/src/images/icons/Social/linked-in-alt.svg" alt="LinkedIn" width="40" height="30" />
  </a>

</p>

