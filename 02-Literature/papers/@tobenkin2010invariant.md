---
type: paper
citekey: tobenkin2010invariant
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Mark M. Tobenkin
- Ian R. Manchester
- Russ Tedrake
year: 2010
venue: IFAC Proceedings Volumes
doi: null
arxiv: '1010.3013'
url: https://arxiv.org/abs/1010.3013
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@tobenkin2010invariant.pdf
bibkeys:
- Tobenkin2010
---

# Invariant Funnels around Trajectories using Sum-of-Squares Programming

> [!info] Mark M. Tobenkin; Ian R. Manchester; Russ Tedrake · 2010 · IFAC Proceedings Volumes

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.

**TL;DR** — Sum-of-Squares methods to compute "funnels" — regions of finite-time invariance around a trajectory — for polynomial nonlinear systems, certifying that states starting near a nominal trajectory stay within a shrinking/growing tube.

**Problem** — Verifying that a controlled nonlinear system stays near a planned trajectory is hard; one wants a rigorous, computable invariant region around a trajectory despite only having approximate (numerically integrated) trajectories.

**Method** — Two SOS-programming schemes search over time-varying polynomial Lyapunov functions: the first exactly certifies invariance conditions even with approximate trajectories, the second relaxes them by sampling in time (much faster, near-identical funnels). Candidate Lyapunov functions come from linearization about the trajectory plus time-varying Lyapunov/Riccati differential equations.

**Key results** — Demonstrated on stabilized trajectories of a six-state satellite model; the time-sampled relaxation recovers nearly the same funnels at far lower cost.

## Takeaways
- Foundational "funnel" formalism: an invariant tube around a trajectory certified via time-varying Lyapunov functions — the SOS ancestor of trajectory-tube guarantees.
- Time-sampling relaxation is the practical enabler; exact certification is expensive.
- Restricted to polynomial dynamics amenable to SOS.

## Relevance to your work
Funnels are the certified invariant tubes that dynamic-tube tracking generalizes; this is a canonical reference for bounding deviation from a nominal trajectory, connecting to [[@compton2025dynamic]].

## Abstract (from bib)
This paper presents numerical methods for computing regions of finite-time invariance (funnels) around solutions of polynomial differential equations. First, we present a method which exactly certifies sufficient conditions for invariance despite relying on approximate trajectories from numerical integration. Our second method relaxes the constraints of the first by sampling in time. In applications, this can recover almost identical funnels but is much faster to compute. In both cases, funnels are verified using Sum-of-Squares programming to search over a family of time-varying polynomial Lyapunov functions. Initial candidate Lyapunov functions are constructed using the linearization about the trajectory, and associated time-varying Lyapunov and Riccati differential equations. The methods

## Concepts
[[tracking-error-bound]] [[tube-mpc]]

## Source
- Cited by [[@compton2025dynamic]]
- bibkeys: `Tobenkin2010`
