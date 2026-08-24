# Frontier Model Training

[Source: Alvaro's Brain]

Frontier-model building is a staged optimization program: mission, scaling budget, data rights/quality, tokenizer, architecture, training stack, pretraining, base evals, post-training, safety, inference, continuous improvement, and cost control.

## Compiled Truth
- Mission first: target capabilities, guardrails, latency, GPU class, budget, and go/no-go metrics constrain every later choice.
- Size/tokens: for compute-optimal training, model parameters and training tokens must scale equally (Chinchilla law) — large undertrained models waste compute and hurt inference cost; predict loss-at-scale using 1/1000th of full compute before committing.
- Data strategy: mix curated web, books, Wikipedia, code, math/science, dialogs, multilingual corpora, and safety data under a rights/provenance policy; Llama 3 (405B, 128K context) demonstrates this at open-weights scale with compositional multimodal extensions (image/video/speech via Llama Guard 3).
- Data hygiene: exact dedup, near-dedup (a single 61-word sentence appeared 60K+ times in standard corpora), PII filtering, toxicity filtering, and contamination scans; deduplicated models produce verbatim memorized text ~10× less and train more efficiently.
- Tokenization: settle BPE/SentencePiece and normalization before recalculating corpus stats; tokenizer changes alter loss floors and throughput; SentencePiece trains directly on raw sentences, eliminating language-specific pre-tokenization.
- Architecture default: decoder-only Transformer, RMSNorm, SwiGLU, RoPE, long-context scaling, and post-training-aware API/tool traces.
- Training stack: bf16, AdamW (decoupled weight decay — L₂ reg and weight decay are inequivalent in adaptive optimizers), cosine decay/warmup, FSDP/ZeRO-style sharding, tensor/sequence/data parallelism, activation checkpointing, fused kernels.
- Pretraining: stage broad clean data, then specialized domains, then hard slices; monitor train/validation loss, overflows, gradient norms, throughput, zero-shot evals.
- Base evals: standardized reasoning, knowledge, code, multilingual, and model-card draft before alignment.
- Post-training: SFT creates usable instruction behavior; RLHF/DPO/constitutional/RLAIF transforms capability into preference-aligned behavior.
- InstructGPT established the canonical RLHF sequence: collect demonstrations, train an SFT model, collect human preference rankings, then optimize the policy against a learned reward model. Scale alone did not solve instruction following: OpenAI reported a 1.3B InstructGPT model preferred over 175B GPT-3 on their prompt distribution, with better truthfulness/toxicity behavior and limited public NLP regressions.
- Local pedagogical pipeline (Language Model Builder / MLX): choose tokenizer+data → watch pretrain loss → sample base → SFT → DPO → chat. Default Mac settings yield coherent multi-paragraph text in about a day; GPT-2-small class (~100–150M on a few billion tokens) ~1 week on M5 Max. Checkpoints resume locally; safetensors export. This is understanding-scale, not frontier-scale.
- Compact agent distillation (Muse Glimmer 30B, Apache 2.0): (1) pretrain via logit distillation on Muse Spark outputs with a similar mix; (2) mid-train on longer-context agent-heavy data with richer traces plus organic data; (3) post-train SFT mixed with on-policy distillation and RL across general/reasoning/coding/agentic domains. Target: always-on local agents (tool calling, coding, LLM-as-judge) on one consumer GPU.
- Liquid cookbook shape: continued pretraining (text/translation + Unsloth), SFT (text and vision-language, TRL or Unsloth), DPO (TRL), GRPO for verifiable tasks (Unsloth and plain). Recipe family, not a single paper.
- Hidden-reasoning distillation risk: providers return CoT as client-side encrypted blobs. Cross-session/user/model compatibility let weaker family models transcribe frontier traces. Attack vectors: IP distillation, PII/credential recovery from published logs (315,320 blocks → 367 PII + 182 credentials), hidden harmful content in traces, encrypted prompt injection. Mitigations: server-side IDs, AEAD bind to user/session/predecessor, key rotation for leaked blobs, decoder refusal training. Patched after responsible disclosure; do not treat encrypted thinking as a secret store.
- Governance: EU GPAI Code of Practice (July 2025, voluntary, AI Board-endorsed as "adequate", 23 signatories including OpenAI/Google/Microsoft/Anthropic) imposes three obligations — transparency (Model Documentation Form, Article 53), copyright compliance policy (Article 53), systemic-risk safety for most-advanced models only (Article 55); model/system cards, adversarial testing, incident logs, and training-data summaries cannot be bolted on late.
- Inference: KV caching, batching, speculative decoding, paged attention, quantization, distillation, and observability define cost/token and latency SLOs.
- Compute economics: transformer inference cost scales mainly with model parameters and generated/input tokens, while training cost also depends on memory residency, interconnect bandwidth, and repeated experiment runs. For application startups, hosted model APIs are usually the Day-1 default; direct GPU infrastructure becomes justified when model training is the product, vertical control is required, or scale economics outweigh the operational distraction.
- Continuous training: consented prompts, failures, red-team cases, SFT/preference refreshes, and human preference A/B loops form the data flywheel.
- Pre-seed shortcut: adopt a frontier-grade base, run domain SFT/DPO on HR workflows, capture tool traces, write governance artifacts early, and gate weekly model cuts with lightweight static + preference evals.

## Open Threads
- Decide Clous differentiation axis first: proprietary HR data, post-training on HR workflows, or inference UX/tool reliability.
- Define the 30-day proof metric: win-rate, latency, structured-output validity, or task completion.
- Do not compile claims about open-weight distillation from proprietary CoT; the 2608.09867 appendix is correlational and post-patch.

## Sources
- raw/_history/Private & Shared 10/AI Engineering 14ea1ee8bd0680abbf4cca7f900fbd02.md
- https://arxiv.org/abs/2001.08361
- https://arxiv.org/abs/2203.15556
- https://ar5iv.org/pdf/2407.21783
- https://arxiv.org/abs/2211.15533
- https://ar5iv.labs.arxiv.org/html/2107.06499
- https://www.nist.gov/itl/ai-risk-management-framework
- https://aclanthology.org/P16-1162/
- https://arxiv.org/abs/1808.06226
- https://pytorch.org/docs/stable/amp.html
- https://arxiv.org/abs/1711.05101
- https://proceedings.neurips.cc/paper_files/paper/2022/file/b1efde53be364a73914f58805a001731-Paper-Conference.pdf
- https://arxiv.org/pdf/2305.18290
- https://arxiv.org/pdf/2212.08073
- https://arxiv.org/abs/2303.08774 — GPT-4 Technical Report: multimodal Transformer, predictable scaling (1/1000th compute preview), RLHF alignment
- https://arxiv.org/abs/2407.21783 — Llama 3: 405B dense Transformer, 128K context, Llama Guard 3, compositional multimodal (image/video/speech)
- https://arxiv.org/abs/2001.08361 — Scaling Laws (Kaplan et al.): power-law loss vs. params/data/compute; architecture choices secondary
- https://arxiv.org/abs/2203.15556 — Chinchilla (Hoffmann et al.): params and tokens must scale equally for compute-optimal training; Chinchilla 70B beats Gopher 280B
- https://arxiv.org/abs/2107.06499 — Deduplication (Lee et al.): 61-word sentence 60K+ times; deduplicated models memorize ~10× less; train-test contamination >4%
- https://aclanthology.org/P16-1162/ — BPE tokenization (Sennrich et al.): subword units for rare-word handling in NMT
- https://arxiv.org/abs/1808.06226 — SentencePiece (Kudo & Richardson): language-independent subword tokenizer, raw-sentence training
- https://arxiv.org/abs/1711.05101 — AdamW (Loshchilov & Hutter): decoupled weight decay; L₂ reg ≠ weight decay in adaptive optimizers
- https://artificialintelligenceact.eu/high-level-summary/
- https://digital-strategy.ec.europa.eu/en/policies/contents-code-gpai — EU GPAI Code of Practice: July 2025, 23 signatories, Model Documentation Form, 3 obligations
- https://lmsys.org/blog/2023-05-03-arena/
- https://research.meta.ai/blog/introducing-muse-glimmer-open-agentic-model
- https://arxiv.org/abs/2608.09867
- https://languagemodelbuilder.com/
- https://github.com/Liquid4All/cookbook/tree/main/finetuning
- https://30papers.com/
- https://a16z.com/navigating-the-high-cost-of-ai-compute/
- https://arxiv.org/abs/2304.13712
