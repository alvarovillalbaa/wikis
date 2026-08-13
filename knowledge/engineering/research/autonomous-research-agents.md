# Autonomous Research Agents

Autonomous research agents are report compilers with planning, collection, synthesis, citation, visualization, refinement, and self-evaluation loops. Production systems extend this with persistent memory, hybrid retrieval, and closed self-improvement loops.

## Compiled Truth

### Research Agent Architecture
- Ideal loop: understand query → plan subquestions → gather internal/external data → evaluate sources → synthesize → cite → generate visuals → refine → self-check → deliver.
- Architecture roles: planner, researcher, synthesizer, visualizer, reporter, reviewer/evaluator.
- Autonomy requires guardrails: scope control, time/iteration budget, source recency/authority rules, contradiction handling, and report completeness checks.
- HR-specific research should privilege HR taxonomies, internal HR data, compliance regimes, privacy constraints, and authoritative industry sources.

### Memory and Retrieval Layer
- GBrain (Garry Tan): Hybrid BM25 + vector + typed KG. Auto-wiring of entity relations with zero LLM calls. BrainBench P@5 49.1%, R@5 97.9%; graph-disabled loses 31.4pp P@5.
- QMD (Tobi Lutke): On-device BM25 + vector + LLM rerank. Context metadata per collection. MCP query/get/multi_get/status. RRF hybrid.
- PRAXIS (ICLR 2026): Post-deployment procedural learning via state-action-result triples without fine-tuning.
- BM25 (Robertson / Sparck Jones): TF saturation (k1) + length vs avgdl (b). Default Elasticsearch/Solr ranker; RAG first-pass. Hybrid with dense is the production default.

### Self-Improving Agent Loops
- AutoResearch (Karpathy 2025): edit, timed run, keep if metric improves else revert.
- Pi Autoresearch (Shopify/Pi): keep/revert loop on a minimal harness. Reported unit tests 300x faster, React mount 20% faster.
- Autocontext, Hermes, autoresearch-agent, self-improving-agent: see prior compile and Sources.

## Open Threads
- Build a research-agent eval set around HR questions, citation correctness, source diversity, and report usefulness.
- Evaluate GBrain/QMD hybrid retrieval vs current RAG for Clous agent memory layer.
- Test AutoResearch / Pi Autoresearch on Clous prompt/system-block optimization.

## Sources
- raw/_history/Private & Shared 10/AI Engineering 14ea1ee8bd0680abbf4cca7f900fbd02.md
- raw/_history/autoresearch.md
- https://github.com/greyhaven-ai/autocontext
- https://github.com/garrytan/gbrain
- https://github.com/tobi/qmd
- https://github.com/NousResearch/hermes-agent
- https://github.com/WecoAI/awesome-autoresearch
- https://arxiv.org/abs/2511.22074
- https://earendil.com/posts/pi-autoresearch-and-databricks/
- https://chimchim89.github.io/BM25/
