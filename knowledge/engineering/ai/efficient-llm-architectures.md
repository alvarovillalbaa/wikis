# Efficient LLM Architectures

[Source: Alvaro's Brain]

Efficiency work attacks one of four surfaces: asymptotic attention cost, precision, active parameter count, or architecture search.

## Compiled Truth
- Quadratic attention grows with `n^2`; long-context workloads make this the dominant memory/compute bottleneck.
- Subquadratic attention reduces sequence cost below `n^2`; linear attention targets `O(n)`, sparse attention limits which token pairs interact.
- Linear-attention family: Linformer, Linear Transformer, Performer.
- Sparse-attention family: Longformer, BigBird, Sparse Transformers.
- Quantization compresses weights/activations by reducing precision; uniform, dynamic-range, and quantization-aware training trade storage/latency for accuracy risk.
- MoE increases total parameters but routes each token to few experts; capacity rises without dense FLOP parity.
- LoRA adds trainable low-rank adapters to frozen base weights; it is a fine-tuning efficiency method, not only a deployment method.
- Progressive neural architecture search explores efficient architectures under performance constraints.
- Practical payoff: lower serving cost, edge feasibility, model accessibility, and energy efficiency.

## Open Threads
- Decide whether Clous needs long-context algorithmic savings or cheaper dense-model serving first.
- Benchmark any efficiency method against task quality, not generic perplexity only.

## Sources
- raw/_history/Private & Shared 10/AI Engineering 14ea1ee8bd0680abbf4cca7f900fbd02.md
