---
type: paper
citekey: sontag1989universal
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Sontag, Eduardo D
year: 1989
venue: Systems \& control letters
doi: null
arxiv: null
url: null
zotero: null
summary: ai-draft
pdf: missing
status: to-read
mine: false
bibkeys:
- Sontag
- sontag1989universal
---

# A ‘universal’construction of Artstein's theorem on nonlinear stabilization

> [!info] Sontag, Eduardo D · 1989 · Systems \& control letters

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — Gives an explicit ("universal") formula that turns any smooth control-Lyapunov function into a smooth stabilizing feedback, proving Artstein's theorem constructively.
**Problem** — Artstein's theorem asserts that the existence of a smooth CLF implies smooth stabilizability, but the original argument is non-constructive; a concrete feedback law is missing.
**Method** — Constructs an explicit feedback given by an algebraic function of the relevant Lie derivatives (L_f V and L_g V), the now-standard "Sontag formula," which arises from solving a simple Riccati equation pointwise.
**Key results** — The formula yields a feedback that is smooth away from the origin (and continuous at it under the small-control property), and the result is extended to the real-analytic and rational cases.

## Takeaways
- The canonical constructive bridge from a CLF to an actual stabilizing controller — foundational to CLF-QP and, by extension, CBF-QP pointwise-optimal control designs.
- Smoothness/continuity of the feedback hinges on the CLF satisfying the small-control property.
- Purely a state-feedback existence-plus-formula result; no input constraints or robustness are treated.

## Relevance to your work
Sontag's universal formula is the constructive CLF-to-feedback result underpinning the Lyapunov-based stabilization analysis in [[@olkin2026stability]].

## Concepts


## Source
- Cited by [[@compton2024constructive]], [[@contract2025theory]], [[@olkin2026stability]]
- bibkeys: `Sontag`, `sontag1989universal`
