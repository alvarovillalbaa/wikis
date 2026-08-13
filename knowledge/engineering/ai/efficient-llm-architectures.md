# Efficient LLM Architectures

[Source: Alvaro's Brain]

Efficiency work attacks one of four surfaces: asymptotic attention cost, precision, active parameter count, or architecture search.

## Compiled Truth
- Quadratic attention grows with `n^2`; long-context workloads make this the dominant memory/compute bottleneck.
- Subquadratic attention reduces sequence cost below `n^2`; linear attention targets `O(n)`, sparse attention limits which token pairs interact.
- Linear-attention family: Linformer, Linear Transformer, Performer.
- Sparse-attention family: Longformer, BigBird, Sparse Transformers.
- Ring Attention (Liu, Zaharia, Abbeel, ICLR 2024): exact attention across a device ring. Each host keeps a query block; KV blocks circulate; softmax statistics accumulate in any order. Compute-transfer overlap needs `c ≥ F/B`. Per-host activation memory is independent of total sequence length `s`; blockwise attention already removed the full score matrix but left sequence-length cost in layer outputs.
- Quantization compresses weights/activations by reducing precision; uniform, dynamic-range, and quantization-aware training trade storage/latency for accuracy risk.
- Local 30B serving: Muse Glimmer FP16 would need >55GB; ~4-bit K-quant shrinks the LM to <20GB so KV cache + perception encoder + speculative drafter fit in 24–32GB with claimed negligible agentic-task loss.
- KV-head reduction: GQA/MQA/MLA shrink decode cache vs MHA. Muse Glimmer uses gated local+global GQA.
- MoE increases total parameters but routes each token to few experts; capacity rises without dense FLOP parity.
- LoRA adds trainable low-rank adapters to frozen base weights; it is a fine-tuning efficiency method, not only a deployment method.
- Speculative decode is a serving efficiency method: draft k tokens, verify in one target forward, accept prefix. Drafter memory is overhead; quantized drafters matter on-device.
- Progressive neural architecture search explores efficient architectures under performance constraints.
- Practical payoff: lower serving cost, edge feasibility, model accessibility, and energy efficiency.

## Open Threads
- Decide whether Clous needs long-context algorithmic savings or cheaper dense-model serving first.
- Benchmark any efficiency method against task quality, not generic perplexity only.

## Sources
- raw/_history/Private & Shared 10/AI Engineering 14ea1ee8bd0680abbf4cca7f900fbd02.md
- https://arxiv.org/abs/2310.01889v4 — Ring Attention
- https://fanout.sh/daily/2026-08-09-ring-attention
- https://research.meta.ai/blog/introducing-muse-glimmer-open-agentic-model
- https://sebastianraschka.com/blog/2026/muse-glimmer-30b-architecture-notes.html
- https://www.aleksagordic.com/blog/vllm
