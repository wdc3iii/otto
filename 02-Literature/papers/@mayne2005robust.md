---
type: paper
citekey: mayne2005robust
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- D.Q. Mayne
- M.M. Seron
- S.V. Raković
year: 2005
venue: Automatica
doi: https://doi.org/10.1016/j.automatica.2004.08.019
arxiv: null
url: null
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: missing
bibkeys:
- fixed_tube
---

# Robust model predictive control of constrained linear systems with bounded disturbances

> [!info] D.Q. Mayne; M.M. Seron; S.V. Raković · 2005 · Automatica

## Summary
> [!note] AI-drafted from the abstract — a base to refine.

**TL;DR** — The foundational *tube* MPC: robustly controls constrained linear discrete-time systems under bounded disturbances by keeping the true state inside a disturbance-invariant tube around an optimized nominal trajectory.

**Problem** — Robust MPC for constrained, linear, discrete-time systems with bounded disturbances, with a rigorous stability guarantee and complexity comparable to nominal MPC.

**Method** — The online optimal control problem uniquely includes the *initial state of the nominal model* as a decision variable; a local feedback keeps the real state within a disturbance-invariant set around the nominal path. The value function is zero on that invariant set, which plays the role of the "origin" under disturbances.

**Key results** — Proves robust exponential stability of the disturbance-invariant set for the closed loop, and the resulting online problem is a quadratic program of essentially the same complexity as conventional MPC.

## Takeaways
- Canonical *fixed-tube* construction: nominal trajectory optimized online + fixed disturbance-invariant tube from a fixed ancillary feedback = robust constraint satisfaction and stability.
- Making the nominal initial state a decision variable is the key trick that yields the strong (invariant-set) stability result at QP cost.
- The tube is fixed/rigid (independent of the trajectory), which is conservative — later dynamic-tube methods shrink/reshape it along the trajectory.

## Relevance to your work
This is the fixed-tube MPC that dynamic-tube approaches generalize; it is the baseline your [[@compton2025dynamic]] work builds on when the tube size is made state/plan-dependent rather than a single invariant set.

## Abstract (from bib)
This paper provides a novel solution to the problem of robust model predictive control of constrained, linear, discrete-time systems in the presence of bounded disturbances. The optimal control problem that is solved online includes, uniquely, the initial state of the model employed in the problem as a decision variable. The associated value function is zero in a disturbance invariant set that serves as the ‘origin’ when bounded disturbances are present, and permits a strong stability result, namely robust exponential stability of the disturbance invariant set for the controlled system with bounded disturbances, to be obtained. The resultant online algorithm is a quadratic program of similar complexity to that required in conventional model predictive control.

## Concepts
[[tube-mpc]], [[dynamic-tube]], [[tracking-error-bound]]

## Source
- Cited by [[@hierarchies2025motion]]
- bibkeys: `fixed_tube`
- DOI: https://doi.org/https://doi.org/10.1016/j.automatica.2004.08.019
