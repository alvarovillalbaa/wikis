# Pretraining Run Operations

[Source: Alvaro's Brain]

Pretraining operations are a control system over data mixture, sequence construction, throughput, optimizer stability, eval gates, incidents, lineage, determinism, and budget.

## Compiled Truth
- Domain buckets need per-sample metadata: doc id, domain, language, timestamp, license, quality, toxicity, PII, length, hash.
- Mixture scheduling should move from broad clean data to specialized domains and hard slices; temperature upsampling prevents small high-value domains from disappearing.
- Replay limits matter: web-scale data streams without explicit epochs; curated math/code/problem slices need bounded repeat factors and skip lists.
- Quality curriculum: begin with high mean quality, relax later to broaden coverage while tracking contamination and memorization.
- Sequence construction: use length curriculum, document-boundary-aware packing, BOS/EOS discipline, minimum chunk size, and no accidental cross-document attention.
- Throughput: optimize effective tokens per step via microbatch, accumulation, data parallel world size, and sequence length; track MFU, tokens/sec, FLOPs/sec, IO wait.
- Stability defaults: bf16 AdamW, warmup, cosine decay, global norm clipping, RMSNorm/SwiGLU, zero dropout in pretrain unless evidence says otherwise.
- Step telemetry: loss, LR, grad norm, param norm, update ratio, overflows, NaNs, activation stats, GPU utilization, HBM, comm time, IO wait.
- Eval cadence: validation by domain and length, gradient noise, memorization probes, zero-shot slices, long-context needles, safety probes.
- Gates must halt automatically: flat early loss, repeated multi-domain eval regressions, code loss degradation after mixture shift, long-context failure, safety probe failures.
- Incident response maps symptom to action: NaNs lower LR/resume N-1; throughput collapse checks dataloader/storage/NCCL; flat loss checks masking/tokenizer; eval loss divergence reweights data.
- Artifacts: checkpoint manifest, RNG states, optimizer/scheduler state, env, git commit, dataset snapshot manifests, eval inputs, scores, and checksums.
- Determinism: fix seeds, container, CUDA/cuDNN/kernel/driver/NCCL versions, deterministic ops where feasible, and document performance-driven nondeterminism.
- Budgeting: use `~6 * params * tokens` FLOPs as rough decoder-only planning math, then reserve 10-20% for incidents/evals/restarts.

## Open Threads
- Convert this into a concrete runbook only if Clous trains or heavily post-trains owned models.

## Sources
- raw/_history/Private & Shared 10/AI Engineering 14ea1ee8bd0680abbf4cca7f900fbd02.md
