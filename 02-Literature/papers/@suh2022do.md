---
type: paper
citekey: suh2022do
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Suh, Hyung Ju
- Simchowitz, Max
- Zhang, Kaiqing
- Tedrake, Russ
year: 2022
venue: ICML
doi: 10.48550/arXiv.2202.00817
arxiv: '2202.00817'
url: https://arxiv.org/abs/2202.00817
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@suh2022do.pdf
bibkeys:
- suh2022differentiable
---

# Do differentiable simulators give better policy gradients?

> [!info] Suh, Hyung Ju; Simchowitz, Max; Zhang, Kaiqing; Tedrake, Russ · 2022 · ICML

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — First-order gradients from differentiable simulators are not automatically better than zeroth-order policy gradients; stiffness and discontinuities can wreck them, and an interpolating α-order estimator captures the best of both.
**Problem** — Differentiable simulators promise faster RL by replacing zeroth-order (score-function) gradient estimates with first-order (pathwise) ones, but it was unclear when the first-order estimator actually helps on long-horizon control of physical systems.
**Method** — The authors analyze both estimators through the lens of bias and variance, showing that physical characteristics such as stiffness or contact discontinuities can make the first-order estimator biased or high-variance. They propose an α-order gradient estimator (α ∈ [0,1]) that blends exact first-order gradients with robust zeroth-order estimates.
**Key results** — On numerical examples they demonstrate the pitfalls of the naive first-order estimator and show the α-order estimator recovers efficiency without sacrificing robustness (no benchmarked figures noted here).

## Takeaways
- Differentiable simulation is not a free win: on stiff/discontinuous dynamics (e.g. contact), the pathwise gradient can be arbitrarily biased or high-variance.
- The right framing is bias–variance; the α-order estimator interpolates between zeroth- and first-order rather than committing to either.
- Key caveat: analysis is on illustrative numerical examples, not large-scale robot learning benchmarks.

## Relevance to your work
For anyone using differentiable simulation to train or tune locomotion/control policies, this is the cautionary reference on why contact-rich, stiff dynamics can make analytic gradients unreliable — relevant when [[@csomayshanklin2024robust]] leans on simulation-based policy optimization.

## Concepts


## Source
- Cited by [[@csomayshanklin2024robust]]
- bibkeys: `suh2022differentiable`
