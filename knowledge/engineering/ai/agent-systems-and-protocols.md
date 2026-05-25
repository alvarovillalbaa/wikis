# Agent Systems And Protocols

Agent architecture separates tool access, agent orchestration, cross-agent protocol, memory, research loops, and product-specific domain control.

## Compiled Truth
- Practical agent systems have a layered build stack: model/provider choice, prompts, structured output, tools, memory, dynamic routing, middleware, workflow graphs, RAG, multi-agent control, evals, and deployment.
- MCP is the tool/resource integration layer: agents reach external systems through structured tool/context interfaces.
- OpenAI Agents SDK-style orchestration is the runtime/triage layer: choose, run, and coordinate agents inside the product.
- A2A is the cross-agent interoperability layer: expose agent cards, endpoints, tasks, messages, streaming, push notifications, auth, and lifecycle state across vendors/frameworks.
- A2A is most valuable when agents need external interoperability or direct collaboration beyond simple triage; it is less urgent if all collaboration is internal and already handled by orchestration.
- A2A complements MCP: MCP connects agents to tools/resources; A2A connects agents to agents.
- Structured output turns LLM calls into application boundaries: schemas should carry extraction, routing, classification, and action payloads instead of free text.
- Tool design is the highest-leverage agent design surface: narrow tool affordances, stable names, explicit auth, precise inputs/outputs, and observable side effects beat broad magical tools.
- Memory should be separated by horizon: working context for the current run, hierarchical or retrieved memory for durable state, and processors that prune or filter tool traces before they pollute context.
- Middleware owns cross-cutting controls: guardrails, authentication, authorization, logging, retries, and policy gates.
- Graph workflows give agents deterministic structure: branching, chaining, merging, conditions, suspend/resume, and streaming updates make long-running execution inspectable.
- Production-grade agents need tool-use reliability, memory, traces, sandboxing, evals, and recovery from partial failures.
- Advanced agent patterns include CoT, ToT, ReAct, reflection, function calling, planning, long-term memory, multi-agent collaboration, process-supervised reward models, and programmatic decomposition.
- Autonomous research agents should implement query understanding, plan generation, source gathering, source evaluation, synthesis, citations, visuals, iterative refinement, self-evaluation, and final report assembly.
- For HR research agents, source policy should privilege internal RAG, HR systems, authoritative public sources, compliance context, and privacy constraints.
- Structural agent failure framework: most "dumb" agent behavior is a systems failure, not a model failure. Four stabilizing pillars: (1) Durable Memory — structured, queryable, not ephemeral context; (2) Explicit Tools — clear signatures and return types eliminate guesswork; (3) Specific Goal Definition — vague instructions cause wandering; precise goals anchor reasoning; (4) Recovery Logic — retries and diagnostics prevent collapse.
- **Manus context management trilogy** (rlancemartin, 2025): General-purpose agent running ~50 tool calls/task in a cloud VM. Three orthogonal strategies: (1) *Context reduction* — two-tier tool result storage: full representation for recent results driving current decisions; compact file-path references for stale results; schema-based trajectory summarization when compaction yields diminishing returns. (2) *Context offloading* — bind a small function set (<20 atomic tools: Bash, filesystem) to the LLM; push execution diversity to the sandbox layer; store tool results on filesystem and retrieve via `glob`/`grep` — mirrors skills/progressive disclosure patterns. (3) *Context isolation* — multi-agent with pragmatic (not role-based) task assignment; planner assigns tasks to executors; simple tasks receive only instructions, complex tasks receive full planner context + shared filesystem; constrained decoding enforces output schema conformance. Abandoned `todo.md` approach: ⅓ of all actions were unproductive task-list updates. Model routing by cost: Claude → code, Gemini → multimodal, OpenAI → math/reasoning. Lesson: if performance plateaus with stronger models, the harness (not the model) is the bottleneck.
- **Foundation Agents survey** (Bang Liu et al., 47 collaborators, arxiv 2504.01990): Modular brain-inspired architecture maps agent components to human brain functions — memory (hippocampus), world modeling (prefrontal cortex), reward processing (basal ganglia), goals, emotion analog. Four research pillars: Modular Architecture, Self-Enhancement (continuous learning), Multi-Agent Systems (collective intelligence), Safety & Ethics (alignment, robustness). Framing: agent components should be separable modules each matching a cognitive function, not monolithic prompt-response chains.
- **Paperclip** (paperclipai): Multi-agent company orchestration layer: org charts, budgets, governance, goal alignment across heterogeneous agents (OpenClaw, Claude Code, Codex, Cursor, Bash, HTTP endpoints). "If OpenClaw is an employee, Paperclip is the company." Manages goal decomposition, work auditing, cost monitoring, and agent coordination from a single dashboard. Clipmart: marketplace for pre-built company templates (full org structures + agent configs + skills). Key design: any process that can receive a heartbeat is hirable.
- **724-office** (wangziqi06): Production 24/7 self-evolving agent — 10K lines pure Python, 36 tools, 20 files, zero framework (no LangChain/LlamaIndex/CrewAI). Architecture: messaging platform → router (multi-tenant Docker auto-provisioning) → LLM tool-use loop → modular tool domains (messaging, admin, search, video, page/ECharts, mirror/soul-report). Three-layer memory: session history + LLM-compressed long-term + LanceDB vector retrieval. Critical reliability patterns: (1) *Nudge system* — 5 rules for structural behavior correction; auto-detects when LLM has tools but doesn't use them and injects hint. (2) *Circuit breaker* — disables a tool after 3 consecutive failures per session. (3) *Budget-aware system prompt* — token budget tracked during assembly. (4) *Dynamic tool filtering* — 5 context profiles (voice/scheduler/group/diagnostic/default) suppress unused tools to reduce token waste. (5) *Runtime tool creation* — agent writes, saves, and loads new Python tools at runtime via `create_tool`. (6) *Inactivity guard* — auto-skips cron tasks for dormant users (3-day threshold). Case study: all production-hardening features arose from operating 24/7 across multiple users — not design speculation.
- **agent-designer** (alirezarezvani/claude-skills): Multi-agent architecture checklist: choose between single-agent, supervisor, swarm, hierarchical, and pipeline patterns; specify roles by identity/responsibilities/capabilities/interfaces/constraints; design tools with validation, stable outputs, error classes, idempotent writes, and atomicity; choose message-passing/shared-state/event-driven communication; add guardrails, HITL checkpoints, task/quality/cost/latency metrics, scaling model, and failure handling. Interpretation: useful as a design-review checklist, but not a replacement for domain-specific evals or production traces.

## Open Threads
- Decide whether A2A is strategic now or a future interoperability affordance.
- Specify which Clous agents need direct peer collaboration versus central orchestration.
- Define research-agent citation/evidence gates before autonomous report generation.

## Sources
- raw/_history/Private & Shared 10/AI Engineering 14ea1ee8bd0680abbf4cca7f900fbd02.md
- sources/ai/principles-of-building-ai-agents.pdf
- https://developers.googleblog.com/en/a2a-a-new-era-of-agent-interoperability/
- https://github.com/google/A2A
- https://google.github.io/A2A/
- https://www.koyeb.com/blog/a2a-and-mcp-start-of-the-ai-agent-protocol-wars
- https://learnopencv.com/googles-a2a-protocol-heres-what-you-need-to-know/
- https://www.devshorts.in/p/agent2agent-a2a-protocol-explained
- https://hackernoon.com/getting-to-know-googles-agent2agent-protocol
- https://help.openai.com/en/articles/10500283-deep-research-faq
- https://www.langchain.com/
- https://www.microsoft.com/en-us/research/project/autogen/
- https://www.databricks.com/
- raw/_history/Private & Shared 10/AI Engineering/image.png — "How to Build an AI Agent That Doesn't Feel Dumb" (4-pillar framework)
- https://rlancemartin.github.io/2025/10/15/manus/ — Manus agent architecture deep-dive
- https://arxiv.org/abs/2504.01990 — Foundation Agents survey: brain-inspired modular architecture (Bang Liu et al.)
- https://github.com/paperclipai/paperclip — Paperclip multi-agent company orchestration
- https://github.com/wangziqi06/724-office — 724-office: production 24/7 pure-Python agent with nudge, circuit breaker, runtime tool creation
- https://github.com/alirezarezvani/claude-skills/tree/main/engineering/agent-designer — agent-designer multi-agent architecture skill
