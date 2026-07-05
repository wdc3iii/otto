---
type: paper
citekey: bujarbaruah2019adaptive
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Monimoy Bujarbaruah
- Xiaojing Zhang
- Marko Tanaskovic
- Francesco Borrelli
year: 2019
venue: Transactions on Automatic Control
doi: null
arxiv: '1909.13473'
url: https://arxiv.org/abs/1909.13473
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@bujarbaruah2019adaptive.pdf
bibkeys:
- Bujarbaruah2019
---

# Adaptive MPC under Time Varying Uncertainty: Robust and Stochastic

> [!info] Monimoy Bujarbaruah; Xiaojing Zhang; Marko Tanaskovic; Francesco Borrelli · 2019 · Transactions on Automatic Control

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — An adaptive MPC for constrained linear systems that online-identifies a slowly time-varying uncertainty offset via set membership and tightens constraints accordingly, in both robust and stochastic variants.
**Problem** — Constrained linear systems face bounded time-varying additive uncertainty; treating it as a fixed worst-case bound is overly conservative, so the controller should learn and exploit structure in the uncertainty as data arrives.
**Method** — The additive uncertainty is decoupled into a bounded process noise (known bounds) plus a time-varying offset with a known Feasible Parameter Set (FPS) and known maximum rate of change. A Set Membership Method refines the FPS online using new data and the noise bounds, and the MPC enforces constraints for all offsets in the current FPS. Two formulations are given — robust (hard) and probabilistic (chance) state constraints, with hard input constraints — each with terminal conditions ensuring recursive feasibility and stability.
**Key results** — Both robust and stochastic adaptive-MPC algorithms are validated in detailed numerical simulations; set-membership refinement shrinks the FPS over time, reducing conservatism while preserving guarantees.

## Takeaways
- Set membership gives a *guaranteed* (not probabilistic) shrinking uncertainty set, which is what lets the adaptive scheme keep robust constraint satisfaction as it learns.
- Explicitly handles a rate-bounded time-varying parameter — more general than constant-parameter adaptive MPC.
- Recursive feasibility and stability come from terminal ingredients, standard MPC machinery adapted to the shrinking FPS.

## Relevance to your work
The set-membership + constraint-tightening approach to bounding and adapting to uncertainty online is the analytic counterpart to the tube/bound designs in [[@compton2025dynamic]], and relevant to online adaptation of tracking-error bounds.

## Abstract (from bib)
This paper deals with the problem of formulating an adaptive Model Predictive Control strategy for constrained uncertain systems. We consider a linear system, in presence of bounded time varying additive uncertainty. The uncertainty is decoupled as the sum of a process noise with known bounds, and a time varying offset that we wish to identify. The time varying offset uncertainty is assumed unknown point-wise in time. Its domain, called the Feasible Parameter Set, and its maximum rate of change are known to the control designer. As new data becomes available, we refine the Feasible Parameter Set with a Set Membership Method based approach, using the known bounds on process noise. We consider two separate cases of robust and probabilistic constraints on system states, with hard constraints 

## Concepts
[[tube-mpc]]

## Source
- Cited by [[@compton2025dynamic]]
- bibkeys: `Bujarbaruah2019`
