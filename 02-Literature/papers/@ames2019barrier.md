---
type: paper
citekey: ames2019barrier
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Ames, A. D.
- Coogan, S.
- Egerstedt, M.
- Notomista, G.
- Sreenath, K.
- Tabuada, P.
year: 2019
venue: European Control Conference (ECC)
doi: 10.23919/ECC.2019.8796030
arxiv: null
url: https://doi.org/10.23919/ECC.2019.8796030
zotero: null
summary: ai-draft
pdf: missing
status: to-read
mine: false
bibkeys:
- ames2019control
---

# Control barrier functions: Theory and applications

> [!info] Ames, A. D.; Coogan, S.; Egerstedt, M.; Notomista, G.; Sreenath, K.; Tabuada, P. · 2019 · European Control Conference (ECC)

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — A survey/tutorial introducing control barrier functions (CBFs) and their use to verify and enforce safety in optimization-based safety-critical controllers.
**Problem** — Provides a unified introduction to how forward invariance of a safe set can be certified and enforced, and how safety composes with stabilization objectives.
**Method** — Surveys the main technical results on CBFs — safe-set forward invariance conditions, the CBF-QP that filters a nominal/CLF controller pointwise, and extensions — then discusses applications across several domains including robotic systems.
**Key results** — Consolidates the CBF framework and its guarantees; documents applications to robotics (survey, no single benchmark).

## Takeaways
- Canonical reference for the CBF definition, forward-invariance guarantee, and the CBF-QP safety filter formulation.
- Frames safety (CBF) and stability (CLF) as jointly enforceable via a single quadratic program.
- Breadth over depth: an entry point and citation anchor rather than a new result.

## Relevance to your work
The standard citation for CBF theory when justifying safety filters on legged/humanoid controllers; grounds the CBF-QP machinery reused in safety-critical work like [[@cohen2025safety]].

## Concepts
[[control-barrier-function]]

## Source
- Cited by [[@compton2025learning]], [[@csomayshanklin2025dynamically]]
- bibkeys: `ames2019control`
