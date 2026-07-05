---
type: paper
citekey: cohen2023characterizing
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- M. H. Cohen
- P. Ong
- G. Bahati
- A. D. Ames
year: 2023
venue: LCSS
doi: 10.1109/lcsys.2023.3341345
arxiv: '2309.12614'
url: https://arxiv.org/abs/2309.12614
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@cohen2023characterizing.pdf
bibkeys:
- CohenLCSS23
---

# Characterizing Smooth Safety Filters via the Implicit Function Theorem

> [!info] M. H. Cohen; P. Ong; G. Bahati; A. D. Ames · 2023 · LCSS

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — Uses the Implicit Function Theorem to characterize when a safety filter is smooth, yielding families of smooth "universal formulas" for safety-critical control that generalize CBF-QP filters.
**Problem** — CBF-based quadratic-program safety filters are continuous but generally not smooth (not continuously differentiable), which complicates higher-order designs, stability analysis, and any construction that differentiates the filtered control law.
**Method** — Characterizes smooth safety filters via the Implicit Function Theorem, deriving general families of smooth universal formulas for safety-critical controllers and quantifying the conservatism each formula introduces relative to the nominal filter.
**Key results** — Provides a unifying, IFT-based view of smooth safety-filter formulas (with Sontag-type formulas as special cases) and a handle on their conservatism.

## Takeaways
- Smoothness is not free: it trades against conservatism, and the paper makes that trade-off explicit and tunable.
- IFT gives a principled recipe for smooth CBF controllers, useful whenever you need to differentiate the safety-filtered input (e.g. cascaded/higher-order or learning-in-the-loop settings).
- Generalizes the classic universal-formula family rather than proposing one ad hoc filter.

## Relevance to your work
Smooth safety filters are a building block for the safety layer in [[@cohen2025safety]]: a differentiable filtered control law is what lets you compose CBF safety with downstream control/learning without the nonsmoothness of the raw CBF-QP breaking analysis.

## Concepts
[[control-barrier-function]]

## Source
- Cited by [[@cohen2025safety]]
- bibkeys: `CohenLCSS23`
