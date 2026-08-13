# Objects vs Memory vs Data vs Context

[Source: Alvaro’s Brain]

- Memory
    - Conversations and Traces
    - Items (+ Episodes + Triples)
    - Network (specific for HR, cross-user actions)
    - Lessons
    - Knowledge
    - History
    - Experience
    - Patterns
- Learnings
    - Instructions
    - Fine-tuning
    - Few-shot
    - System Blocks (SPL)
- Modeling
    - Skills
    - MD System
    - Decisions
- Recitation
    - Canvas
    - Files
    - Input
    - BDI
- Data = objects (may have KG)
    - Insights, Analysis, etc.

# Infrastructure
- Generation (as AI agent tool calls, or regular functions)
- CO (Continuous Optimization) Pipelines (Cleaning/Updating)

# Post-building flywheel (production agents)

Compiled from Judgment Labs (2025-10-07): model post-training makes skills; *post-building* makes assembled agents reliable.

- Production trajectories (reasoning, actions, env responses, outcomes) are the measurement substrate.
- User corrections, retries, approvals, and pairwise preference are votes; generic judges and stale hand-written rubrics point at the wrong hill.
- Convert mined criteria into online scores, then optionally into rewards for SFT/RL. Custom evals turn a usage-distribution advantage into a product moat.
- Cursor tab-completion is the cited case: preference capture → +28% acceptance.

## Sources
- https://www.judgmentlabs.ai/blogs/climbing-the-hills-that-matter
