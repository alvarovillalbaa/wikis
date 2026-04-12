---
tags:
  - knowledge
field: ai-architecture
---
AI systems are broader than agents. An agent = LLMs with varying autonomy levels. An AI system = agents + instant processing + async processing + data flows across all of them.

**Three processing modes:**
- *Autonomy* — complex tasks handled without human intervention
- *Instant processing* — real-time responses where latency is critical
- *Async processing* — data arrives in pieces over time; system processes at a defined moment

**Cognitive Workload**: the intelligence effort required to produce optimal output. Scales with task complexity and degree of data transformation (e.g. summarizing 46 pages = high workload).

**One-Constraint Thesis**: a foundational model specialized on a single limitation outperforms a generalist one for that task. NL Gap Closing = tuning a model toward one human need.

**Agentic workflow layers:** Initial (task breakdown / knowledge injection) → Main (core output) → Secondary (refinement, context addition)

**Key propagation concepts:**
- *Instruction Forwarding* — instructions passed across agents to keep alignment
- *Context Forward-Propagation* — reasoning/assumptions carried from one model call to the next

**Governance:**
- *Model Governance* — compute resource allocation across models
- *Weight Governance* — distributing decision authority between models to avoid overstepping
- *Weight Cleanse* — continuous weight adjustment via RLHF during ongoing training

**Agentic Chaining (AAP):** agents run in parallel or series depending on dependency structure. Long contexts split via *Continuous Context Partitioning* and reassembled as needed.
