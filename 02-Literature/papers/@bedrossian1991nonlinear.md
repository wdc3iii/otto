---
type: paper
citekey: bedrossian1991nonlinear
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Bedrossian, Nazareth Sarkis
year: 1991
venue: Massachusetts Institute of Technology
doi: null
arxiv: null
url: http://hdl.handle.net/1721.1/27998
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@bedrossian1991nonlinear.pdf
bibkeys:
- bedrossian_nonlinear_nodate
---

# Nonlinear Control Using Linearizing Transformations

> [!info] Bedrossian, Nazareth Sarkis · 1991 · Massachusetts Institute of Technology

## Summary
> [!note] AI-drafted from the thesis abstract — a base to refine.
**TL;DR** — A PhD thesis developing linearizing coordinate transformations (via canonical/Hamiltonian structure and Riemannian curvature) for controlling nonlinear, especially underactuated, mechanical systems.
**Problem** — When can a nonlinear mechanical system be transformed into an equivalent linear model, and how can that structure be exploited to control underactuated systems whose linear designs have a small operating region?
**Method** — Introduces "orthogonal canonical transformations" that preserve Hamilton's equations and characterize a class of Hamiltonian systems admitting a linear representation, recovering the original solution via the inverse transformation. Uses the Riemann curvature tensor as a computational test for whether a system admits coordinates in which its equations of motion become a linear (double-integrator) model, and adopts a higher-order linear-approximation design to expand the operating region for underactuated systems.
**Key results** — Derives general existence conditions for the linearizing transformations, gives worked examples where the curvature test succeeds and the transformation is computed, and shows in simulation a substantial increase in the operating range of a linear controller applied to an underactuated example.

## Takeaways
- Frames feedback/coordinate linearizability geometrically: the Riemann curvature tensor becomes a concrete, computable obstruction to exact linearization.
- Explicitly targets underactuated mechanical systems and the failure of small-signal linear designs — directly relevant to legged/hopping dynamics.
- Higher-order (2nd+) linear approximations meaningfully enlarge the region where a linear controller works, a pragmatic middle ground between local linearization and full nonlinear design.

## Relevance to your work
A classical source on exact/approximate feedback linearization and the curvature obstruction to it — the constructive geometry underpinning controller synthesis for underactuated locomotion systems. See [[@compton2024constructive]].

## Concepts


## Source
- Cited by [[@compton2024constructive]]
- bibkeys: `bedrossian_nonlinear_nodate`
