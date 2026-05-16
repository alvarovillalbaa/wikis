# Cybersecurity — Privacy, Consent, and HCI

[Source: WORK/KNOWLEDGE/Programming/Cybersecurity/Design.pdf]
[Source: WORK/KNOWLEDGE/Programming/Cybersecurity/HCI.pdf]

Privacy-by-design and informed consent frameworks for information systems, grounded in Value Sensitive Design methodology.

---

## Source notes

- `Design.pdf` — "Informed Consent by Design" (Friedman, Lin, Miller), Chapter 24 of *Security and Usability* (O'Reilly, 2005). Complete chapter, fully read.
- `HCI.pdf` — *Human–Computer Interaction*, 3rd ed. (Dix, Finlay, Abowd, Beale; Pearson, 2004). 817-page general HCI textbook; pages 1–10 read (TOC/framework only). Covers: foundations (human, computer, interaction), design process, models/theories, groupware, ubiquitous computing. Not security-specific; filed here as companion to Design.pdf.

---

## Value Sensitive Design (VSD)

- Emerged 1990s — design approach accounting for human values throughout the design process
- Values in scope: privacy, security, trust, human dignity, informed consent, intellectual property, usability
- Three investigation types (iterative, mutually informing):
  - **Conceptual** — philosophically grounded analysis of values and tradeoffs (e.g., access vs. privacy)
  - **Empirical** — human response to artifact in social context; surveys, interviews, interaction logs
  - **Technical** — performance analysis and design of technical mechanisms
- Stakeholder distinction: **direct** (interact with system) vs. **indirect** (affected by system output, e.g., people documented in court records)
- Interactional theory: values are neither inscribed in technology nor purely social — technology and social systems co-shape each other

---

## Informed Consent Model for Information Systems

Six components (Friedman, Felten, Millett 2000):

| Component | Definition |
|---|---|
| **Disclosure** | Accurate info on benefits/harms; what data collected, who has access, how long archived, what used for, how identity protected |
| **Comprehension** | User accurately interprets what is disclosed; test: can user restate in own words and apply to hypothetical scenarios? |
| **Voluntariness** | Action not coerced or manipulated; coercion includes monopoly conditions where no comparable alternative exists |
| **Competence** | Mental/emotional/physical capability to give consent; COPPA requires parental consent for under-13 |
| **Agreement** | Clear, visible, ongoing opportunity to accept or decline; implicit consent valid only if all other components also met |
| **Minimal distraction** | Meet all criteria without unduly diverting user from primary task — the hardest criterion to implement |

- "Informed" = disclosure + comprehension
- "Consent" = voluntariness + competence + agreement
- **Manipulation types** that undermine voluntariness:
  - Manipulation of options (forcing unnecessary data collection)
  - Manipulation of information (overwhelming with cookie requests to induce "accept all")
  - Psychological manipulation (flattery, guilt, subliminal cues; users respond to computer social cues as they would to humans)

---

## Case Studies

### 1. Cookie handling (Mozilla browser redesign)
- Problem (as of 1999): default = accept all cookies; no harm/benefit disclosure per cookie; no alert when cookies were *used* (only when set); burden on user to decline one-at-a-time
- Solution: "Cookie Watcher" peripheral-awareness sidebar
  - Color coding: third-party = red, same-domain = green; italics = session; bold = >1yr duration
  - Two just-in-time interventions: click cookie → Cookie Manager; "Learn About Cookies" button → info dialog
- Technical constraint: HTTP protocol lacks mechanism for server to declare why it needs a cookie → protocol-level change required to fully disclose harm/benefit

### 2. Secure connections — user mental models
- Study: 72 users, 3 communities (rural Maine, suburban NJ, high-tech California)
- Top evidence users relied on to judge security: icon/lock (45–53%), HTTPS protocol (16–20%), type of information requested (18–27%)
- Most common incorrect evaluation source: icon/lock (45% of incorrect "not secure" judgments) and type of information (27% of incorrect assessments both ways)
- Mental model split: correct model = security applies to information *in transit* (encryption); incorrect model = security is a property of a *place* (the server/site)
- High-tech users more likely to hold transit model (74%) vs. rural (33%) — but high-tech still sometimes wrong
- Design implication: lock/padlock icon reinforces incorrect "place" mental model; interaction design should reinforce transit model

### 3. Gmail — scope limits of informed consent
- Gmail scans email body for keyword-targeted ads (automated, no human reader)
- Disclosure analysis (2004): Gmail privacy policy adequately addressed what collected, who has access, what used for, identity protection — but vague on retention duration
- Voluntariness: reasonably neutral TOS language; alternative services existed (lower storage)
- Unresolved boundary question: Does machine reading of personal content constitute privacy violation?
  - Parent's definition: privacy = no undocumented personal info known by *others* → machine reading not a violation
  - Bloustein's definition: privacy = inviolate personality/dignity → any intrusion, machine or human, is violation
- Indirect stakeholder problem: email senders did not consent; Gmail only obtained receiver consent

---

## 10 Design Principles for Informed Consent

1. **Decide what's exempt** — Belmont Report criteria: no harm possible, purpose known, no coercion → may be exempt from consent requirement
2. **Invoke implicit consent cautiously** — as critical services move online, "no comparable alternative" makes implicit consent coercive
3. **Understand scope** — informed consent ≠ privacy; privacy, trust, security are related but distinct values with different design implications
4. **Include indirect stakeholders** — not just direct users; anyone affected by system output
5. **User control over nuisance factor** — range of control granularity: global overrides + micromanaged + intermediate subsets
6. **Defaults matter** — most users never change defaults; default must err toward preserving consent
7. **Avoid technical jargon** — plain language addressing user's values, needs, interests
8. **Inform through interaction model** — mental models users build through interaction must match technical reality (e.g., don't use lock icon to imply "secure place" when security is about transit)
9. **Field test for comprehension and agreement** — representative + atypical users; consent carries moral imperative so adequate performance is a requirement, not a best practice
10. **Design proactively** — retrofitting informed consent into deployed systems is nearly impossible; build it in from the start

---

## HCI Textbook Framework (Dix et al.)

- Part 1 — Foundations: human (perception, memory, reasoning, emotion), computer (I/O devices, displays, processing), interaction (models, WIMP, interaction styles), paradigms
- Part 2 — Design Process: interaction design basics, HCI in software lifecycle, design rules, evaluation, universal design, user support
- Part 3 — Models and Theories: cognitive models, socio-organizational, task analysis, dialog notation, system models
- Part 4 — Outside the Box: groupware, ubiquitous/augmented reality, hypertext/web
- Key design frameworks: Shneiderman's Eight Golden Rules, Nielsen's heuristics, HCI patterns
- Usability engineering: iterative design + prototyping + evaluation; usability metrics (learnability, efficiency, memorability, errors, satisfaction)
