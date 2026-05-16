# AI Governance And Safety

Agent governance is the control layer for autonomous software that can pursue goals, use tools, remember, collaborate, and affect external systems.

## Compiled Truth
- AI agents differ from chatbots because they can pursue high-level goals in open environments with tools, memory, and other agents.
- Agent capability should be modeled across reasoning/planning, memory, action/tool use, and multi-agent interaction; each capability expands both usefulness and control surface.
- Short, scoped tasks are improving faster than long-horizon reliability; deployment should distinguish capability spikes from robust autonomy.
- Adoption starts where tasks are structured, data-rich, feedback-heavy, and economically valuable: support, AI/ML R&D, cyber triage, narrow research reproduction.
- Core bottlenecks: hallucination, brittle plans, tool-use fragility, recovery failures, expensive inference, limited long-horizon reasoning.
- Long-horizon benchmarks are the key deployment warning: current agents can approach human parity on short tasks but degrade sharply on multi-step or hour-plus work.
- Risk categories:
  - Malicious use: lower cost/skill barrier for disinformation, cyber offense, and dual-use workflows.
  - Accidents/loss of control: persistent tool users compound errors and create opaque action chains.
  - Security: memory, APIs, tools, and inter-agent protocols expand prompt-injection and compromise surfaces.
  - Systemic: labor displacement, power concentration, surveillance, and market instability.
- Agent-filled futures bifurcate around governance: universal access plus visible/accountable agents can accelerate care, R&D, and public services; opaque mass deployment can create botnets, synthetic markets, surveillance, and institutional loss of control.
- Governance levers:
  - Alignment: multi-agent RL, agent risk-attitude tuning, encoded-reasoning defenses, alignment evals.
  - Control: rollback, shutdown/interruption, action whitelists, tool-use restrictions, control protocols.
  - Visibility: agent IDs, activity logs, cooperation-relevant capability evals, reward reports, audit trails.
  - Security/robustness: access controls, adversarial robustness tests, sandboxing, adaptive defense.
  - Societal integration: liability regimes, commitment devices, equitable access, law-following agents.
- Open problems: continuous multi-hour evals, robust oversight, institutional licensing/compute gates, benefit-sharing design.
- Constitutional/principle-based safety works by comparing responses against explicit principles: human rights, non-discrimination, privacy, harmlessness, no impersonated embodiment, non-expert humility, anti-conspiracy, obedience to human control, and reduced self-interest/power-seeking.
- **Anthropic Responsible Scaling Policy — ASL framework** (modeled on biosafety levels): ASL-1 = no meaningful catastrophic risk (pre-2019 models); ASL-2 = early dangerous capability but insufficient reliability for real harm (current Claude models — triggers White House commitment baselines); ASL-3 = substantially increased catastrophic misuse risk OR low-level autonomous capability → unusually strong security, no deployment if red-team adversarial testing shows meaningful catastrophic misuse risk; ASL-4/5+ = not yet defined, may require unsolved interpretability research before reaching. Board approval required for RSP changes. Key mechanism: commitments are made *before* reaching each tier, eliminating deployment-moment rationalization.

## Open Threads
- Convert governance levers into concrete Clous runtime checks: action permissions, memory boundaries, logs, eval gates, and incident response.

## Sources
- raw/_history/Private & Shared 10/AI Engineering 14ea1ee8bd0680abbf4cca7f900fbd02.md
- sources/ai/agent-governance.pdf
- https://www.anthropic.com/news/anthropics-responsible-scaling-policy
- https://assets.anthropic.com/m/24a47b00f10301cd/original/Anthropic-Responsible-Scaling-Policy-2024-10-15.pdf
- https://www.anthropic.com/news/claudes-constitution
- https://www.anthropic.com/research/specific-versus-general-principles-for-constitutional-ai
- https://www.anthropic.com/news/core-views-on-ai-safety
- https://www.un.org/en/about-us/universal-declaration-of-human-rights
- https://storage.googleapis.com/deepmind-media/DeepMind.com/Authors-Notes/sparrow/sparrow-final.pdf
