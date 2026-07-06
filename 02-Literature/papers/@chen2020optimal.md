---
type: paper
citekey: chen2020optimal
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Chen, Yuxiao
- Ahmadi, Mohamadreza
- Ames, Aaron D
year: 2020
venue: 2020 American Control Conference (ACC)
doi: 10.23919/acc45564.2020.9147721
arxiv: 1909.11798
url: https://arxiv.org/abs/1909.11798
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@chen2020optimal.pdf
bibkeys:
- chen2020optimal
---

# Optimal safe controller synthesis: A density function approach

> [!info] Chen, Yuxiao; Ahmadi, Mohamadreza; Ames, Aaron D · 2020 · 2020 American Control Conference (ACC)
> [!info]- otto authors: [[aaron-ames]]

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — Synthesizes optimal *safe* controllers using density functions, exploiting the duality between the density function (Liouville equation) and the value function (Bellman optimality).
**Problem** — Safety constraints are naturally constraints on the *distribution* of states, which are awkward to pose directly in a standard optimal-control problem.
**Method** — Uses the density function — the dual of the value function — so that state-distribution constraints like safety enter the optimal control problem straightforwardly; the constrained problem is then solved with a primal-dual algorithm. The formulation is extended to external disturbances, giving robust constrained optimal control via a modified primal-dual scheme.
**Key results** — Applies the method to find the optimal safe controller minimizing cumulative intervention, demonstrated on an adaptive cruise control (ACC) example and compared against the conventional control-barrier-function (CBF) approach.

## Takeaways
- Density/value duality (Liouville vs. Bellman) is the key trick: safety-as-distribution-constraint becomes tractable in an optimal-control formulation.
- Primal-dual solution extends cleanly to disturbances, yielding a robust safe controller.
- Positioned as an alternative to pointwise CBF-QP filters: minimizes *cumulative* intervention rather than instantaneous deviation.

## Relevance to your work
Offers an optimal-control-based route to safety guarantees as a contrast to CBF-based safety filters — directly relevant to how safe locomotion controllers trade off intervention against performance; see [[@cohen2025safety]].

## Concepts
[[control-barrier-function]]

## Source
- Cited by [[@hierarchies2025motion]]
- bibkeys: `chen2020optimal`
