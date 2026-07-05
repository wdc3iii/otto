---
type: paper
citekey: blanchini2008set
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- F. Blanchini
- S. Miani
year: 2008
venue: Springer
doi: 10.1007/978-0-8176-4606-6
arxiv: null
url: https://link.springer.com/book/10.1007/978-0-8176-4606-6
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: missing
bibkeys:
- Blanchini
---

# Set-theoretic methods in control

> [!info] F. Blanchini; S. Miani · 2008 · Springer

## Summary
> [!note] AI-drafted from the publisher description — a base to refine.
**TL;DR** — A comprehensive monograph on the set-theoretic approach to control, centered on (positively) invariant sets and Lyapunov-like functions for analyzing and synthesizing constrained, uncertain, and disturbed dynamic systems.
**Problem** — Provides a unified theoretical and practical treatment of core control problems — Lyapunov stability and stabilization, optimal control, control under constraints, persistent-disturbance rejection, and uncertain-system analysis/synthesis — through the lens of sets rather than single trajectories.
**Method** — Develops the machinery of convex sets and their representation, Lyapunov and Lyapunov-like functions (whose sublevel sets are positively invariant), invariant-set computation, dynamic programming, and set-theoretic estimation, then applies it to parameter-varying, switched, and time-domain-constrained control.
**Key results** — A reference text establishing invariance as the organizing principle for saturating control, noise/disturbance suppression, and model-predictive control, among others.

## Takeaways
- The central idea — sublevel sets of Lyapunov functions are positively invariant — is the workhorse behind constraint satisfaction and robust invariance results across control.
- Definitive reference for (robust) controlled-invariant sets, which underpin recursive-feasibility and safety arguments in MPC and constrained control.
- Set-based reasoning is the common thread linking Lyapunov stability, MPC, disturbance rejection, and estimation.

## Relevance to your work
The set-invariance foundations here underpin both the robust-invariant-set constructions in tube MPC and the forward-invariance guarantees at the heart of CBF-based safety in [[@cohen2025safety]] — this is the theory those tools stand on.

## Concepts
[[control-barrier-function]] [[tube-mpc]]

## Source
- Cited by [[@cohen2025safety]]
- bibkeys: `Blanchini`
