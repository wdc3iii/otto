---
type: paper
citekey: schweidel2022safe
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Schweidel, Katherine S
- Yin, He
- Smith, Stanley W
- Arcak, Murat
year: 2022
venue: Annual Reviews in Control
doi: 10.1016/j.arcontrol.2022.04.004
arxiv: 2201.04590
url: https://arxiv.org/abs/2201.04590
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@schweidel2022safe.pdf
bibkeys:
- ArcakARC22
- schweidel2022safe
---

# Safe-by-design planner--tracker synthesis with a hierarchy of system models

> [!info] Schweidel, Katherine S; Yin, He; Smith, Stanley W; Arcak, Murat · 2022 · Annual Reviews in Control

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — A tutorial-style safe-by-design framework that plans on a low-fidelity model and tracks with a high-fidelity model, certifying that the planning/tracking error stays in a bounded set.
**Problem** — How to plan trajectories online for a complex nonlinear system while formally guaranteeing the real system stays safe despite the model mismatch between the planner and the true dynamics.
**Method** — A two-layer hierarchy: the planning layer uses a low-fidelity model to generate a feasible trajectory online (e.g. via MPC), and the tracking layer uses the high-fidelity model to design a controller confining the planner-tracker error to a bounded set. The tracking controller and the error bound are computed offline (e.g. via sum-of-squares programming), and the error is allowed to depend on both planner states and inputs for flexibility in choosing the low-fidelity model.
**Key results** — Presented as a tutorial review with illustrative examples, including a vehicle obstacle-avoidance design.

## Takeaways
- Clean statement of the planner-tracker (reduced-order/full-order) decomposition with an offline-certified error tube that the online planner can treat as a robustness margin.
- Splitting the effort — online planning on the simple model, offline SOS certification on the full model — is what makes safe online planning tractable.
- Letting the tracking error depend on planner inputs (not just states) broadens which reduced-order planning models are admissible.

## Relevance to your work
This is the reference architecture behind hierarchical planner-tracker locomotion: a reduced-order planner with a certified tracking-error bound, closely aligned with your motion-planning hierarchy work in [[@hierarchies2025motion]].

## Concepts
[[reduced-order-model]] · [[hierarchical-control]] · [[tracking-error-bound]] · [[tube-mpc]]


## Source
- Cited by [[@cohen2025safety]], [[@compton2025learning]]
- bibkeys: `ArcakARC22`, `schweidel2022safe`
