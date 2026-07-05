---
type: paper
citekey: langson2004robust
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- W. Langson
- I. Chryssochoos
- S. V. Raković
- D. Q. Mayne
year: 2004
venue: Automatica
doi: 10.1016/J.AUTOMATICA.2003.08.009
arxiv: null
url: https://doi.org/10.1016/j.automatica.2003.08.009
summary: ai-draft
pdf: missing
zotero: null
status: to-read
mine: false
bibkeys:
- Langson2004
- langson2004robust
---

# Robust model predictive control using tubes

> [!info] W. Langson; I. Chryssochoos; S. V. Raković; D. Q. Mayne · 2004 · Automatica

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — Introduces the "tube" formulation of robust MPC: an online optimization yields a tube plus a piecewise-affine control law that confines uncertain trajectories inside it, with complexity linear (not exponential) in horizon length.
**Problem** — Feedback (min-max) MPC handles disturbances but optimizing over feedback policies is computationally intractable; conventional open-loop MPC is cheap but conservative/fragile under uncertainty.
**Method** — Solve on-line for a nominal trajectory together with a state tube and an associated piecewise-affine feedback law that keeps all realizations of the uncertain system within the tube. The construction reduces the cost of feedback MPC so complexity grows linearly rather than exponentially in the prediction horizon.
**Key results** — Establishes asymptotic stability of the closed-loop controlled system and demonstrates the tractable tube-based feedback formulation.

## Takeaways
- Foundational reference for tube MPC: separate a nominal online trajectory from an ancillary feedback law that holds the true state in an invariant tube.
- Its contribution is making feedback MPC affordable — linear-in-horizon complexity — while retaining robust constraint satisfaction and stability.
- Predates the rigid-tube (Mayne) and dynamic-tube refinements; the tube here is optimized online rather than fixed offline.

## Relevance to your work
The seminal tube-MPC formulation that underpins dynamic-tube approaches like [[@compton2025dynamic]]; anyone bounding tracking error around a nominal plan for a legged/locomotion system builds on this decomposition.

## Abstract (from bib)
A form of feedback model predictive control (MPC) that overcomes disadvantages of conventional MPC but which has manageable computational complexity is presented. The optimal control problem, solved on-line, yields a 'tube' and an associated piecewise affine control law that maintains the controlled trajectories in the tube despite uncertainty; computational complexity is linear (rather than exponential) in horizon length. Asymptotic stability of the controlled system is established. © 2003 Elsevier Ltd. All rights reserved.

## Concepts
[[tube-mpc]] · [[tracking-error-bound]]

## Source
- Cited by [[@compton2025dynamic]], [[@compton2025learning]]
- bibkeys: `Langson2004`, `langson2004robust`
- DOI: https://doi.org/10.1016/J.AUTOMATICA.2003.08.009
