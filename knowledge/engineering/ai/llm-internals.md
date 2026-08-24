# LLM Internals

[Source: Alvaro’s Brain]

LLM performance is the interaction of representation, scale, memory movement, decoding, adaptation, retrieval, and evaluation. Capability claims are weak unless tied to which bottleneck they change.

## Compiled Truth
- Positional generalization: RoPE encodes relative phase, so attention can extrapolate beyond fixed absolute positions when scaling/interpolation is handled correctly.
- Scaling law discipline: compute-optimal training co-scales parameters and tokens; underfed models waste parameters and compress post-training headroom.
- Training memory: gradient checkpointing trades extra backward compute for lower activation residency; it is a memory enabler, not an accuracy trick.
- Attention efficiency: FlashAttention is exact attention with lower IO and memory traffic; it improves wall-clock and memory pressure without changing the quadratic attention definition.
- Transformer primitives: decoder LLMs use embeddings, repeated attention + MLP blocks, and unembedding to token logits; Q indexes the current query, K indexes prior token positions, V carries retrievable content.
- Inference state: KV caching avoids recomputing previous tokens during autoregressive decoding; it accelerates long decoding but consumes memory.
- KV-cache as virtual memory: PagedAttention stores KV in fixed-size blocks (default 16 tokens) with a block table per request; prefix hashing reuses complete blocks across requests; incomplete blocks cannot be cached. Memory formula is `2 * layers * kv_heads * head_dim * seq * batch * bytes_per_elem`.
- Prefill vs decode: prefill is compute-bound over the prompt; decode is memory-bandwidth-bound (reload weights + KV for one/few tokens). Mixing them in one step (vLLM V1) plus chunked prefill prevents a long prompt from monopolizing the engine.
- Decoding acceleration: speculative decoding drafts multiple tokens with a smaller model and verifies them with the target model. Accept/reject preserves the target distribution; vLLM V1 uses n-gram / EAGLE / Medusa rather than a full draft LM. Muse Glimmer ships a quantized DFlash drafter for local speculative decode.
- Serving loop: schedule (decode first, then prefill) → allocate KV slots → flattened continuous batch forward → sample → free blocks on stop. Prefix cache hits skip recomputation of shared prompt prefixes.
- Disaggregated P/D: separate prefill and decode instances because their rooflines differ; KV is transferred via a connector (LMCache/NIXL in production). Improves TTFT vs ITL isolation.
- TP decode collectives: long-context small-batch tensor-parallel inference puts small AllReduce on the token critical path. Barrier-free push protocols (LL packed flag+data, sentinel, LL128 atomic) approach ~1.4µs SoL on GB200; ~1µs barriers can be ~40% of a 5µs AllReduce.
- Normalization/activation: RMSNorm removes mean-centering overhead; SwiGLU/GeLU improve smooth nonlinear capacity versus ReLU.
- Fine-tuning: LoRA freezes the base and learns low-rank deltas; QLoRA adds 4-bit base quantization for memory-efficient adapter training.
- Retrieval: RAG primarily mitigates missing/fresh knowledge, traceability, and hallucination risk by grounding generation in retrieved evidence; it does not solve context design, ranking, latency, or source-quality problems alone. First-pass lexical ranking is still BM25 in most hybrid stacks.
- RAG and fine-tuning are orthogonal adaptation levers: use RAG when the application needs dynamic external knowledge or auditable sources; use fine-tuning when the goal is model behavior, style, domain terminology, or stable task specialization. Hybrid designs fit systems that need both fresh evidence and domain behavior.
- Model selection should start from task shape and data availability. LLMs are stronger for zero/few-shot, out-of-distribution, open-ended generation, real-world noisy requests, and knowledge-intensive tasks; smaller fine-tuned models remain attractive for rich-label traditional NLU, strict latency/cost targets, regression-like outputs, and task distributions far from language-model objectives.
- Sparse capacity: MoE increases parameter capacity while activating only a subset of experts per token.
- Sampling: temperature, top-k, and top-p are inference-time entropy controls; they do not create knowledge. Guided decoding masks logits with a grammar FSM (xgrammar) so only legal tokens remain.
- Evaluation: exact match, edit distance, n-gram overlap, semantic similarity, and LLM judges measure different failure surfaces. LLM judges carry verbosity and position bias.
- Contamination: an eval is invalid if training and eval distributions overlap materially.
- Hidden CoT as IP: frontier APIs encrypt reasoning blobs for client-side stateless replay. Cross-model/user compatibility of those blobs enabled extraction via weaker decoder models (patched after 2026-07 disclosure). Encrypted traces are not confidential storage.

## Open Threads
- Map which internals matter most for Clous HR workflows: long-context retrieval, tool-use reliability, structured extraction, or latency.
- Separate model-side gains from system-side gains when evaluating product improvements.
- Decide whether Clous serving should treat prefill/decode as one engine or disaggregated workers.

## Evidence
- 2025-08-20 | Raw learning note: hard LLM quiz on RoPE, scaling laws, checkpointing, SwiGLU/GeLU, context extension, FlashAttention, RMSNorm, KV cache, speculative decoding, Adafactor, LoRA, QLoRA, RAG, MoE, CoT.
- 2025-11-05 | Raw learning note: encode-decode vs prefill/decode, Q/K/V, multi-head attention, transformer blocks, parameter interpretation, SFT, preference tuning, sampling, entropy, perplexity, eval metrics, judge biases, contamination.
- 2026-08-13 | Aleksa Gordić vLLM anatomy (engine V1, paged KV, continuous batching, prefix cache, guided/speculative decode, disagg P/D, MultiProcExecutor, DP serving).
- 2026-08-13 | Shen et al. arXiv 2607.16100: barrier-free NCCL AllReduce approaching interconnect SoL; ITL/cost impact on TP decode.
- 2026-08-13 | Panfilov et al. arXiv 2608.09867: encrypted reasoning-trace extraction via cross-model replay.

## Sources
- raw/_history/Private & Shared 10/AI Engineering/@Alvaro Villalba Perez learns 2a2a1ee8bd0680b7ab33d8c5c6650c64.md (processed stub)
- raw/PROCESSED.md
- https://www.aleksagordic.com/blog/vllm
- https://arxiv.org/html/2607.16100v1
- https://arxiv.org/abs/2608.09867
- https://chimchim89.github.io/BM25/
- https://research.meta.ai/blog/introducing-muse-glimmer-open-agentic-model
- https://towardsdatascience.com/rag-vs-finetuning-which-is-the-best-tool-to-boost-your-llm-application-94654b1eaba7/
- https://arxiv.org/abs/2304.13712
