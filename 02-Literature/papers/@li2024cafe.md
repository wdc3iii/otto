---
type: paper
citekey: li2024cafe
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- He Li
- Patrick M. Wensing
year: 2024
venue: preprint arXiv:2403.03995
doi: https://doi.org/10.1109/TRO.2024.3504132
arxiv: '2403.03995'
url: https://arxiv.org/abs/2403.03995
summary: ai-draft
pdf: attachments/@li2024cafe.pdf
zotero: null
status: to-read
mine: false
bibkeys:
- li2024cafempccascadedfidelitymodelpredictive
---

# Cafe-Mpc: A Cascaded-Fidelity Model Predictive Control Framework with Tuning-Free Whole-Body Control

> [!info] He Li; Patrick M. Wensing · 2024 · preprint arXiv:2403.03995

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — Cafe-Mpc is a cascaded-fidelity MPC that progressively coarsens the model, timesteps, and constraints along the horizon, and reuses its action-value function to drive a tuning-free whole-body controller.

**Problem** — Whole-body MPC and conventional whole-body QP control are usually treated as separate components, and full-fidelity MPC over a long horizon is expensive; the paper seeks computation and performance gains while unifying the two.

**Method** — Cafe-Mpc strategically relaxes the planning problem down the prediction horizon (descending model fidelity, coarser time steps, relaxed constraints), solved with a customized multiple-shooting iLQR (MS-iLQR) tailored for hybrid systems. The resulting action-value function seeds a new value-function-based whole-body control (VWBC) that unifies whole-body MPC and whole-body QP without extra WBC tuning.

**Key results** — Cafe-Mpc can improve whole-body MPC performance without necessarily raising compute; VWBC beats a Riccati feedback controller on constraint handling. It enabled a first-of-its-kind gymnastic running barrel roll on quadruped hardware (MIT Mini Cheetah), with Cafe-Mpc at 50 Hz and ~5.3 ms average per solver iteration.

## Takeaways
- Cascaded fidelity is the key idea: spend model/constraint fidelity near the current time, relax it in the far horizon — a principled way to trade accuracy for horizon length.
- The MPC action-value function directly parameterizes the WBC (VWBC), collapsing the usual MPC→WBC hand-tuning into one framework.
- Demonstrated on aggressive dynamic maneuvers (barrel roll), not just steady gaits.

## Relevance to your work
A concrete design point for the reduced-/multi-fidelity + whole-body hierarchy in legged MPC: it formalizes descending model fidelity down the horizon and links planning to a whole-body controller via the value function — squarely relevant to [[hierarchical-control]] and [[reduced-order-model]] pipelines and to work like [[@csomayshanklin2024robust]].

## Concepts
[[hierarchical-control]] · [[reduced-order-model]]

## Source
- Cited by [[@csomayshanklin2024robust]]
- bibkeys: `li2024cafempccascadedfidelitymodelpredictive`
- arXiv: https://arxiv.org/abs/2403.03995
