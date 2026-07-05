---
type: paper
citekey: nguyen2016exponential
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Nguyen, Quan
- Sreenath, Koushil
year: 2016
venue: 2016 American Control Conference (ACC)
doi: 10.1109/ACC.2016.7524935
arxiv: null
url: https://doi.org/10.1109/ACC.2016.7524935
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: missing
bibkeys:
- nguyen2016exponential
---

# Exponential control barrier functions for enforcing high relative-degree safety-critical constraints

> [!info] Nguyen, Quan; Sreenath, Koushil · 2016 · 2016 American Control Conference (ACC)

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — Introduces Exponential Control Barrier Functions to enforce high-relative-degree safety constraints for nonlinear systems, with a systematic design recipe borrowed from linear control theory.
**Problem** — Standard CBFs assume relative degree one; many physical safety constraints (positions, distances) have high relative degree, where the naive CBF condition gives no direct handle on the input.
**Method** — Defines Exponential CBFs that differentiate the constraint down to the input and place the barrier dynamics as a higher-order linear system, so a stabilizing gain (via pole placement / linear control tools) guarantees forward invariance of the safe set for the nonlinear system.
**Key results** — Validated numerically on a relative-degree-6 linear system (serial cart-spring) and a relative-degree-4 nonlinear system (two-link pendulum with elastic actuators).

## Takeaways
- The go-to construction for extending CBFs beyond relative degree one, later generalized as high-order CBFs.
- Reduces safety-controller design to choosing stable barrier dynamics via familiar linear-systems tools.
- Requires the constraint's relative degree to be well-defined and uniform; the chosen barrier-dynamics gains shape how conservatively the safe set is approached.

## Relevance to your work
Essential machinery for enforcing safety on legged/humanoid constraints that are naturally high-relative-degree; underpins predictive and layered CBF schemes such as [[@cohen2025safety]].

## Concepts
[[control-barrier-function]]


## Source
- Cited by [[@compton2025learning]]
- bibkeys: `nguyen2016exponential`
