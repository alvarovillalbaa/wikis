# Context And Prompt Engineering

Context quality is an input-control problem: relevant state, distractor suppression, constraint tracking, and routing shape model behavior more than longer reasoning alone.

## Compiled Truth
- Extended reasoning can degrade on red herrings, spurious correlations, multi-constraint tasks, and AI-risk evaluations when the chain amplifies irrelevant assumptions.
- Context engineering is not just longer windows; it is selecting, ordering, compressing, partitioning, and verifying the right state.
- Prompting families form a toolbox:
  - Zero-shot: emotion, role, style, S2A, SimToM, RaR, RE2, Self-Ask.
  - Few-shot: example generation, ordering, exemplar selection, KNN, Vote-K, prompt mining.
  - Thought generation: CoT, zero-shot CoT, analogical, step-back, thread-of-thought, table CoT, active prompt, Auto-CoT, memory-of-thought, uncertainty-routed CoT.
  - Ensembling: self-consistency, universal self-consistency, meta-CoT, prompt paraphrasing, MMI variants.
  - Self-criticism: verification, calibration, refinement, reverse CoT, cumulative reasoning.
  - Decomposition: least-to-most, plan-and-solve, program-of-thought, tree/skeleton/recursive thought.
- For Clous, tagger prompts are routing infrastructure: map user utterances into context domains before generation.
- Existing tag classes include Clous context, assistant context, job context, company context, feedback, default, and null.
- Fine-tuning routes can be manual prompt repetition, dataset input-output pairs, or instruction-literal examples.
- System Prompt Learning and "knowledge/cognition/skills" should be treated as durable model-behavior surfaces, not one-off prompt copy.
- Six canonical context types for AI agents (productcompass.pm): Instructions (role, objective, requirements/steps, format), Examples (behavior + response examples), Knowledge (external domain/market context, task context, structured data), Memory (short-term chat state; long-term semantic/episodic/procedural — auto-attached by orchestration or accessed as a tool), Tool Results (injected by orchestration layer), Tools (description: what/how/return; parameters: type/description/required/examples).
- Information retrieval strategies: Query Rewriting, Hybrid Retrieval, Cache Retrieval, HyDE (Hypothetical Document Embeddings), Agentic Retrieval.
- Context assembly operations: Filtering, Deduplicating, Re-ranking, Scoring relevance, Compressing, Combining, Splitting, Chunk stitching, Templating, Managing tools, Prompting.
- **Context rot** (Chroma, 2025): LLM performance degrades non-linearly with input length even on trivial tasks across all SOTA models (GPT-4.1, Claude 4, Gemini 2.5, 18 total). Key patterns: (1) low semantic similarity between needle and query amplifies degradation; (2) topically-related distractors cause non-uniform failure intensifying with length — Claude abstains more, GPT hallucinates more; (3) focused prompts (~300 tokens) dramatically outperform full-context prompts (~113k tokens); (4) shuffled haystacks counterintuitively improve performance vs. structured documents (attention responds to organization patterns). Implication: distractor suppression and context compression are not optional — they determine reliability at scale.

## Open Threads
- Define the minimum routing taxonomy needed for current Clous product surfaces.
- Test whether taggers should be models, rules, or hybrid gates.

## Sources
- raw/_history/Private & Shared 10/AI Engineering 14ea1ee8bd0680abbf4cca7f900fbd02.md
- https://www.dbreunig.com/2025/05/07/claude-s-system-prompt-chatbots-are-more-than-just-models.html
- raw/_history/Private & Shared 10/AI Engineering/image 1.png, image 2.png, image 3.png, image 4.png — productcompass.pm context taxonomy
- https://www.trychroma.com/research/context-rot — context rot benchmarks across 18 LLMs
