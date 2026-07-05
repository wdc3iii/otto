---
type: paper
citekey: bradford2019nonlinear
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Eric Bradford
- Lars Imsland
- Ehecatl Antonio Del Rio-Chanona
year: 2019
venue: Proceedings of the IEEE Conference on Decision and Control
doi: 10.1109/CDC40024.2019.9029443
arxiv: null
url: https://doi.org/10.1109/CDC40024.2019.9029443
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: missing
bibkeys:
- Bradford2019
---

# Nonlinear model predictive control with explicit back-offs for Gaussian process state space models

> [!info] Eric Bradford; Lars Imsland; Ehecatl Antonio Del Rio-Chanona · 2019 · Proceedings of the IEEE Conference on Decision and Control

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — A stochastic NMPC scheme for Gaussian-process (GP) state-space models that computes constraint back-offs offline via closed-loop simulations, guaranteeing chance-constraint satisfaction online at low computational cost.
**Problem** — GP regression is a powerful way to identify nonlinear plant models, but data sparsity leaves substantial model uncertainty; naive NMPC on such models risks poor performance and constraint violations, and open-loop uncertainty propagation is both conservative and expensive.
**Method** — Rather than propagating uncertainty online, the authors sample plausible plant models from the GP posterior and run offline closed-loop simulations to compute explicit *back-offs* (constraint tightenings). These pre-computed back-offs are then applied to the online NMPC so that chance constraints hold despite uncertainty, while keeping online computation cheap; the scheme also accommodates updating the GP with new online measurements.
**Key results** — Illustrated on a batch-reactor case study; the closed-loop back-off design prevents the open-loop growth of uncertainty that inflates other robust GP-MPC approaches.

## Takeaways
- Key idea: move the expensive uncertainty accounting *offline* (sampled closed-loop sims) so the online controller stays fast — a pragmatic robust/stochastic MPC trade.
- Back-offs from closed-loop rollouts are less conservative than open-loop uncertainty tubes because feedback is accounted for.
- Guarantees are probabilistic (chance constraints), tied to the GP posterior's calibration and the offline sampling.

## Relevance to your work
Offline-computed constraint tightening to certify online constraint satisfaction under a learned/uncertain model parallels the design-time tube-sizing philosophy in [[@compton2025dynamic]]; useful as a data-driven counterpoint to analytic tube MPC.

## Abstract (from bib)
Nonlinear model predictive control (NMPC) is an efficient control approach for multivariate nonlinear dynamic systems with process constraints. NMPC does however require a plant model to be available. A powerful tool to identify such a model is given by Gaussian process (GP) regression. Due to data sparsity this model may have considerable uncertainty though, which can lead to worse control performance and constraint violations. A major advantage of GPs in this context is its probabilistic nature, which allows to account for plant-model mismatch. In this paper we propose to sample possible plant models according to the GP and calculate explicit back-offs for constraint tightening using closed-loop simulations offline. These then in turn guarantee satisfaction of chance constraints online d

## Concepts
[[tube-mpc]]

## Source
- Cited by [[@compton2025dynamic]]
- bibkeys: `Bradford2019`
- DOI: https://doi.org/10.1109/CDC40024.2019.9029443
