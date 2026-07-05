---
type: paper
citekey: williams2001robust
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Grady Williams
- Brian Goldfain
- Paul Drews
- Kamil Saigol
- James M Rehg
- Evangelos A Theodorou
year: 2001
venue: Systems \& Control Letters
doi: 10.15607/RSS.2018.XIV.042
arxiv: null
url: https://www.roboticsproceedings.org/rss14/p42.html
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@williams2001robust.pdf
bibkeys:
- Williams2001
---

# Robust Sampling Based Model Predictive Control with Sparse Objective Information

> [!info] Grady Williams; Brian Goldfain; Paul Drews; Kamil Saigol; James M Rehg; Evangelos A Theodorou · 2001 · Systems \& Control Letters

## Summary
> [!note] AI-drafted from the abstract — a base to refine. (Published at RSS 2018; the citekey's "2001"/venue are bibliographic artifacts — this is the Williams et al. MPPI robustness paper.)

**TL;DR** — A sampling-based (MPPI-style) stochastic MPC that handles cost functions with sparse, discontinuous gradients by fusing sampling with linearization-based trajectory optimization inside a tube-MPC structure for robustness.

**Problem** — Sampling-based MPC excels on non-differentiable/sparse cost landscapes but lacks robustness guarantees; gradient/linearization methods are efficient but need smooth costs. Neither alone is robust on hard real-world tasks.

**Method** — The framework combines sampling-based MPC with linearization-based trajectory optimization, and the composite algorithm is cast as a novel use of tube-based MPC: a nominal linearized optimizer is wrapped so that sampled rollouts stay within a robust tube.

**Key results** — Robust performance across simulated tasks and a real-world fast autonomous (aggressive) driving task.

## Takeaways
- Bridges sampling-based (MPPI) and gradient/linearization MPC, using a tube to inject robustness into the sampling scheme.
- Targets sparse/discontinuous cost information — exactly where pure gradient MPC fails.
- Validated on aggressive autonomous driving hardware, not just simulation.

## Relevance to your work
A reference point for robust MPC when the cost is non-smooth: the tube construction here is an alternative route to the disturbance-robustness that dynamic-tube MPC formalizes in [[@compton2025dynamic]].

## Abstract (from bib)
We present an algorithmic framework for stochastic model predictive control that is able to optimize non-linear systems with cost functions that have sparse, discontinuous gradient information. The proposed framework combines the benefits of sampling-based model predictive control with linearization-based trajectory optimization methods. The resulting algorithm consists of a novel utilization of Tube-based model predictive control. We demonstrate robust algorithmic performance on a variety of simulated tasks, and on a real-world fast autonomous driving task.

## Concepts
[[tube-mpc]]

## Source
- Cited by [[@compton2025dynamic]]
- bibkeys: `Williams2001`
