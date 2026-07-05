---
type: paper
citekey: dawson2022safe
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Dawson, Charles
- Qin, Zengyi
- Gao, Sicun
- Fan, Chuchu
year: 2022
venue: Conference on Robot Learning
doi: null
arxiv: null
url: https://proceedings.mlr.press/v164/dawson22a.html
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@dawson2022safe.pdf
bibkeys:
- dawson2022safe
---

# Safe nonlinear control using robust neural lyapunov-barrier functions

> [!info] Dawson, Charles; Qin, Zengyi; Gao, Sicun; Fan, Chuchu · 2022 · Conference on Robot Learning

## Summary
> [!note] AI-drafted from the abstract — a base to refine.

**TL;DR** — Learns robust control Lyapunov barrier functions (and their controllers) for nonlinear, uncertain systems, giving safety and stability guarantees at a fraction of the online cost of robust MPC.

**Problem** — Designing controllers with both safety and stability guarantees is hard for nonlinear systems with model uncertainty; existing robust methods (e.g., robust MPC) are computationally expensive online.

**Method** — A model-based learning technique that combines robust convex optimization and Lyapunov theory to synthesize robust control Lyapunov barrier functions that generalize across model uncertainties, together with the feedback controllers that certify them.

**Key results** — Evaluated on vehicle trajectory tracking, nonlinear obstacle avoidance, constrained satellite rendezvous, and flight control with learned ground-effect dynamics; matches or exceeds robust MPC performance while cutting computation roughly tenfold.

## Takeaways
- Unifies CLF (stability) and CBF (safety) into a single learned certificate that is robust to model uncertainty.
- Main selling point is online efficiency: a learned certificate replaces expensive robust-MPC optimization (~10x cheaper).
- Guarantees are relative to the assumed uncertainty set used in the robust convex training.

## Relevance to your work
A learning approach to certified safe/stable nonlinear control that trades offline synthesis for cheap online evaluation — relevant when comparing learned certificates against tube/robust-MPC baselines for locomotion. See [[@compton2025dynamic]].

## Concepts
[[control-barrier-function]]

## Source
- Cited by [[@compton2025dynamic]]
- bibkeys: `dawson2022safe`
