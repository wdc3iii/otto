---
type: paper
citekey: primbs2000receding
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Primbs, J.A.
- Nevistic, V.
- Doyle, J.C.
year: 2000
venue: IEEE Transactions on Automatic Control
doi: 10.1109/9.855550
arxiv: null
url: https://doi.org/10.1109/9.855550
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: missing
bibkeys:
- primbs_receding_2000
---

# A receding horizon generalization of pointwise min-norm controllers

> [!info] Primbs, J.A.; Nevistic, V.; Doyle, J.C. · 2000 · IEEE Transactions on Automatic Control

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — Uses control Lyapunov functions inside receding-horizon control to build a new class of RHC schemes, revealing that pointwise min-norm, receding-horizon, and optimal control are facets of one unified picture.

**Problem** — Pointwise min-norm CLF controllers and receding-horizon (MPC) control had been treated as separate approaches; the relationship between them, and their common ground with optimal control, was not made explicit.

**Method** — CLFs are combined with a receding-horizon cost to derive a CLF-based RHC law, first as an idealized continuous-time controller and then modified for discrete-time sampled implementation. A special case recovers an extension of Sontag's formula, and the construction exposes formal connections among min-norm, receding-horizon, and optimal control.

**Key results** — Shows the scheme has desirable theoretical and implementation properties, proves stronger connections to both optimal and pointwise min-norm control, and demonstrates it on a nonlinear control example.

## Abstract (from bib)
Control Lyapunov functions (CLFs) are used in conjunction with receding horizon control to develop a new class of receding horizon control schemes. In the process, strong connections between the seemingly disparate approaches are revealed, leading to a unified picture that ties together the notions of pointwise min-norm, receding horizon, and optimal control. This framework is used to develop a CLF based receding horizon scheme, of which a special case provides an appropriate extension of Sontag's formula. The scheme is first presented as an idealized continuous-time receding horizon control law. The issue of implementation under discrete-time sampling is then discussed as a modification. These schemes are shown to possess a number of desirable theoretical and implementation properties. An

## Takeaways
- Bridges CLF pointwise min-norm control and receding-horizon control as endpoints of one family, with optimal control as the unifying frame.
- A CLF terminal/stage ingredient is what gives the RHC scheme its stability guarantees — an early template for CLF-based MPC.
- Continuous-time derivation with discrete-time sampling handled as a modification; a foundational theory paper (2000), not a large-scale empirical study.

## Relevance to your work
This is a canonical reference tying CLFs to MPC and min-norm control — directly relevant to CLF-QP and CLF-informed predictive controllers that sit at the tracking layer of a locomotion stack, and cited by the layered scheme in [[@hierarchies2025motion]].

## Concepts


## Source
- Cited by [[@hierarchies2025motion]]
- bibkeys: `primbs_receding_2000`
- DOI: https://doi.org/10.1109/9.855550
