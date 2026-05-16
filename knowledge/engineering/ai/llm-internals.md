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
- Decoding acceleration: speculative decoding drafts multiple tokens with a smaller model and verifies them with the target model.
- Normalization/activation: RMSNorm removes mean-centering overhead; SwiGLU/GeLU improve smooth nonlinear capacity versus ReLU.
- Fine-tuning: LoRA freezes the base and learns low-rank deltas; QLoRA adds 4-bit base quantization for memory-efficient adapter training.
- Retrieval: RAG primarily mitigates missing/fresh knowledge and hallucination risk; it does not solve context design or ranking alone.
- Sparse capacity: MoE increases parameter capacity while activating only a subset of experts per token.
- Sampling: temperature, top-k, and top-p are inference-time entropy controls; they do not create knowledge.
- Evaluation: exact match, edit distance, n-gram overlap, semantic similarity, and LLM judges measure different failure surfaces. LLM judges carry verbosity and position bias.
- Contamination: an eval is invalid if training and eval distributions overlap materially.

## Open Threads
- Map which internals matter most for Clous HR workflows: long-context retrieval, tool-use reliability, structured extraction, or latency.
- Separate model-side gains from system-side gains when evaluating product improvements.

## Evidence
- 2025-08-20 | Raw learning note: hard LLM quiz on RoPE, scaling laws, checkpointing, SwiGLU/GeLU, context extension, FlashAttention, RMSNorm, KV cache, speculative decoding, Adafactor, LoRA, QLoRA, RAG, MoE, CoT.
- 2025-11-05 | Raw learning note: encode-decode vs prefill/decode, Q/K/V, multi-head attention, transformer blocks, parameter interpretation, SFT, preference tuning, sampling, entropy, perplexity, eval metrics, judge biases, contamination.

## Sources
- raw/_history/Private & Shared 10/AI Engineering/@Alvaro Villalba Perez learns 2a2a1ee8bd0680b7ab33d8c5c6650c64.md (processed stub)
- raw/PROCESSED.md
