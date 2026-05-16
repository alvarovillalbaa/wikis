# Autonomous Research Agents

Autonomous research agents are report compilers with planning, collection, synthesis, citation, visualization, refinement, and self-evaluation loops. Production systems extend this with persistent memory, hybrid retrieval, and closed self-improvement loops.

## Compiled Truth

### Research Agent Architecture
- Ideal loop: understand query → plan subquestions → gather internal/external data → evaluate sources → synthesize → cite → generate visuals → refine → self-check → deliver.
- Architecture roles: planner, researcher, synthesizer, visualizer, reporter, reviewer/evaluator.
- Autonomy requires guardrails: scope control, time/iteration budget, source recency/authority rules, contradiction handling, and report completeness checks.
- HR-specific research should privilege HR taxonomies, internal HR data, compliance regimes, privacy constraints, and authoritative industry sources.

### Memory and Retrieval Layer
- **GBrain** (Garry Tan, YC CEO, production): Hybrid search = BM25 full-text + vector semantic + typed knowledge graph entity links. Auto-wiring: every page write extracts entity references and creates typed relations (`attended`, `works_at`, `invested_in`, `founded`, `advises`) with zero LLM calls. Graph layer carries the performance gap: BrainBench P@5 49.1%, R@5 97.9% — graph-disabled variant loses 31.4pp P@5; BM25+vector-only RAG similar margin. Production scale: 17,888 pages, 4,383 people, 723 companies, 21 autonomous cron jobs. Named search modes: `conservative` (~4K tokens/query), `balanced` (~10K), `tokenmax` (~20K). Self-healing: fixes own citations and consolidates memory overnight without human intervention. LongMemEval benchmark built-in for continuous retrieval quality tracking.
- **QMD** (Tobi Lutke, Shopify): On-device BM25 + vector + LLM reranking via node-llama-cpp/GGUF. Contextual tree: context metadata added per collection (not per document) guides LLM toward better contextual selection — context and content are orthogonal signals. MCP server: `query`, `get`, `multi_get`, `status`. `--min-score` threshold for agentic filtering. Hybrid query exposes `lex`/`vec`/`hyde` subtypes combined via RRF + reranking.
- **PRAXIS** (ICLR 2026, MemAgents Workshop): Post-deployment procedural learning — stores state-action-result triples from episodes, retrieves by joint matching of environmental + internal state. Improves task accuracy, reliability, and cost efficiency across foundation model backends; generalizes to previously unseen tasks in comparable environments. Enables continuous learning without fine-tuning.

### Self-Improving Agent Loops
- **AutoResearch pattern** (Karpathy, 2025): `program.md` instructs coding agent to edit target file, run for fixed time, check eval metric, commit if improved else revert, loop. Domain-portable: GPT training (original), GPU kernel (18→187 TFLOPS, RightNow AI), Shopify Liquid template (53% faster, 61% fewer allocations, Tobi Lutke), voice agent prompts (0.728→0.969), baseball pitch prediction (R² 0.44→0.78). Mechanism: evaluation loop + keep/revert discipline = automated gradient descent over code.
- **auto-agent**: Given a golden dataset, autonomously improves a target agent via hypothesis-driven loop — analyze failures → spawn coding agent to fix → evaluate → accept or rollback. Golden dataset is the optimization objective.
- **Autocontext** (Greyhaven AI): Recursive self-improving harness. Iterates against real evaluation (not synthetic). Each run produces structured trace, artifacts, playbooks, datasets, and optionally a distilled local model — the next agent inherits the full improvement history. Backends: Pi runtime, Anthropic, OpenAI, Hermes. MCP server: `autocontext_solve_scenario`, `autocontext_evaluate_output`, `autocontext_run_improvement_loop`.
- **Hermes** (Nous Research): Closed learning loop: agent-curated memory with periodic nudges; autonomous skill creation after complex tasks; skills self-improve during use; FTS5 session search + LLM summarization for cross-session recall. Honcho dialectic user modeling for persistent cross-session user model. Compatible with agentskills.io open standard. Scheduled cron automations, subagent delegation, 7 terminal backends (local, Docker, SSH, Modal serverless, Daytona, Vercel Sandbox). Model-agnostic: OpenRouter 200+ models, NIM, OpenAI, or own endpoint.
- **autoresearch-agent** (alirezarezvani/claude-skills): Canonical Claude Code plugin implementation of the AutoResearch loop. Commands: `/ar:setup` (experiment dir + config + git branch), `/ar:run` (one iteration), `/ar:loop` (autonomous cron loop), `/ar:status` (dashboard), `/ar:resume` (after context limit). Iteration protocol: agent edits target file with ONE change → commits → calls `run_experiment.py --single` → receives KEEP/DISCARD/CRASH → repeats. Results persist in `results.tsv` and git log. Invariant: the evaluator is never modified — it is ground truth.
- **self-improving-agent** (alirezarezvani/claude-skills): Auto-memory orchestration plugin. `/si:review` spawns `memory-analyst` to surface promotion candidates from `~/.claude/projects/.../memory/`. `/si:promote <pattern>` graduates a pattern from MEMORY.md to CLAUDE.md (higher enforcement priority). `/si:extract <pattern>` spawns `skill-extractor` to build a portable skill package. `error-capture.sh` PostToolUse hook auto-appends structured failure entries from Bash tool calls into memory with zero overhead on success. Design split from autoresearch-agent: autoresearch-agent optimizes *code* against an external evaluator; self-improving-agent curates *memory/rules* through human judgment.

## Open Threads
- Build a research-agent eval set around HR questions, citation correctness, source diversity, and report usefulness.
- Evaluate GBrain/QMD hybrid retrieval vs current RAG for Clous agent memory layer.
- Apply PRAXIS state-action-result pattern to HR workflow agent episode storage.
- Test AutoResearch loop on Clous agent prompt/system-block optimization against HR eval sets.

## Sources
- raw/_history/Private & Shared 10/AI Engineering 14ea1ee8bd0680abbf4cca7f900fbd02.md
- raw/_history/autoresearch.md
- raw/_history/agents.md
- raw/_history/agentic-memory.md
- raw/_history/agent-harness.md
- raw/_history/long-horizon-agents.md
- https://help.openai.com/en/articles/10500283-deep-research-faq
- https://www.langchain.com/conceptual-guides/traces-start-agent-improvement-loop
- https://github.com/greyhaven-ai/autocontext — Autocontext recursive self-improving harness
- https://github.com/garrytan/gbrain — GBrain production hybrid KG+vector memory system
- https://github.com/tobi/qmd — QMD on-device hybrid search for agentic workflows
- https://github.com/NousResearch/hermes-agent — Hermes self-improving agent platform
- https://github.com/WecoAI/awesome-autoresearch — AutoResearch pattern use cases and implementations
- https://arxiv.org/abs/2511.22074 — PRAXIS: procedural recall for agents (ICLR 2026 MemAgents)
- https://github.com/alirezarezvani/claude-skills/tree/main/engineering/autoresearch-agent — autoresearch-agent Claude Code plugin
- https://github.com/alirezarezvani/claude-skills/tree/main/engineering-team/self-improving-agent — self-improving-agent memory curation plugin
