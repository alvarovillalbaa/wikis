# AI Labor Market Canaries

Stanford Digital Economy Lab + ADP Research dashboard (updated monthly; this compile uses the July 22, 2026 release). Correlation with occupational AI exposure, not a causal estimator. Sample: ~25k ADP firms with 5-year employment history, 4.6M occupation-matched workers in Nov 2022, 730+ occupations. Not nationally representative; shuts down firm entry/exit.

## Compiled Truth
- "Canaries" are occupation×experience cells that move first. Exposure (Eloundou et al. 2024) is uneven: most-exposed quintile was 38.3% of the Nov 2022 sample vs 6.4% least-exposed.
- All exposure groups grew employment after ChatGPT (Nov 2022), but growth is slowest in the two most-exposed occupation groups. Differences remain modest at the aggregate.
- Divergence is concentrated in early career (22–25, then muted through ~34). Less-exposed young occupations grow; most-exposed young occupations decline and the gap has deepened. Software developers and customer-service reps (high exposure) show large early-career declines and expansion at older ages. Stock clerks and home-health aides (low exposure) do not show that age split; home-health early-career employment rose.
- Automation vs augmentation (Anthropic Economic Index): higher occupation-level *automation* share correlates with declines or muted growth for early-career workers. Augmentation share has no clear monotonic employment relationship.
- Gender: early-career women grew slower. Composition dominates: 43.8% of women vs 32.4% of men were in the most-exposed quintile. Within the most-exposed quintile, early-career women contracted ~4.5%/yr vs men ~2.5%/yr since Nov 2022. Treat as occupational mix plus a smaller within-cell gap, not a separate AI mechanism.
- Feb 2026 paper update: with the broadest controls, exposed-occupation declines become statistically significant in 2024; earlier moves likely include non-AI confounders. Dashboard reports correlation in this ADP sample.

## Open Threads
- Map Clous HR product surfaces (entry-level hiring, CS, software) against these canary occupations.
- Do not treat dashboard indexes as causal displacement estimates.

## Sources
- https://digitaleconomy.stanford.edu/project/indicators/canaries-dashboard/
- Brynjolfsson, Chandar, Chen 2025, "Canaries in the Coal Mine?"
