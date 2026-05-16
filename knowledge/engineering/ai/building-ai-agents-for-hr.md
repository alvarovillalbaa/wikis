**Process characteristics:**
- HR: non-deterministic, non-testable, non-reproducible → higher-stakes AI judgment than Finance/Engineering
- Information/data ratio is low: 30+ page employment contract → ~1 paragraph of actionable content (law refs, payroll, role)
- Continuous data collection is manual and distributed (candidate applications, cross-employee feedback, satisfaction surveys)
- Multi-stakeholder hierarchy → multi-player AI required; HITL complexity exceeds most enterprise domains

**Data ownership thesis:**
- Capture 10x vs competitors; own end-to-end workflows to control data provenance
- Max 1 custom integration/customer, only if reusable across 2+ customers
- LinkedIn API shutdown → ATS market collapse; same pattern → Sales Tech 2024. Integration dependency = existential risk

**Anti-patterns (low-value AI targets):**
- Payroll execution (already automated)
- Resume parsing (15yr-old commodity)
- Pre-onboarding data entry (no net automation; adds UX friction)

**High-value AI targets:**
- Candidate selection across known + unknown applicant pool → first-interview scheduling + personalized outreach + post-interview transcript synthesis
- Reporting: forms → XLSX → slides (fully manual today); high automation ceiling
- Employee support: repeated policy/process questions (internal customer support equivalent)
- Payroll budgeting, analysis, forecasting, calibration

**AI system architecture:**
- Orchestration layer is the moat; scaffolding is the compounding asset
- Continuous learning; memory compounds over time
- Compliance processes (payroll deadlines, mandatory training): deterministic automation
- Adaptive processes (interview synthesis, onboarding personalization, performance signals): probabilistic AI

**People systems as codebases:**
- Processes currently live in oral tradition + half-maintained wikis; scattered across Docs/Confluence/Notion/HRIS
- Three enabling convergences: LLMs handle unstructured HR inputs (feedback, Slack, evidence); internal users provide tight feedback loops; real bottleneck was connective tissue (handoffs, undocumented knowledge transfers)
- Version control + rollback + audit trail on process changes: makes bias visible and reviewable, doesn’t resolve it
- Essential friction (managerial judgment conversations) vs accidental friction (3hrs compiling docs) — only eliminate accidental
- People partners → direct process builders; engineering ticket dependency eliminated

## Sources
- [Source: Alvaro’s Brain]
- https://jonathannen.com/people-systems-are-the-next-codebase/
- https://arxiv.org/abs/2311.06383 — RJDB: 50k+ (JD, matched/unmatched resume) triples; tasks: JD matching, explanation, skill extraction, resume editing; skill-occupation graph distillation → student models match/beat GPT-4