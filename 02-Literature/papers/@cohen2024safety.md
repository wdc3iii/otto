---
type: paper
citekey: cohen2024safety
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Cohen, Max H
- Molnar, Tamas G
- Ames, Aaron D
year: 2024
venue: Annual Reviews in Control
doi: 10.1016/j.arcontrol.2024.100947
arxiv: '2403.09865'
url: https://doi.org/10.1016/j.arcontrol.2024.100947
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@cohen2024safety.pdf
bibkeys:
- CohenARC24
- Cohen_2024
- cohen2024safety
- cohen2025safety
---

# Safety-critical control for autonomous systems: Control barrier functions via reduced-order models

> [!info] Cohen, Max H; Molnar, Tamas G; Ames, Aaron D · 2024 · Annual Reviews in Control
> [!info]- otto authors: [[aaron-ames]]

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.

**TL;DR** — A tutorial that unifies the family of techniques for building control barrier functions (CBFs) for complex, high-dimensional robots out of CBFs designed for simple reduced-order models.

**Problem** — Modern autonomous systems (flying, legged, wheeled) have high-dimensional nonlinear dynamics for which constructing CBFs directly is intractable — the dynamics may be complicated or not even known.

**Method** — Provides a self-contained, unified formulation of literature methods that share a common foundation: constructing CBFs for complex systems from CBFs for much simpler reduced-order models, transferring safety guarantees back to the full system. Presented through formal results, simple numerical examples, and case studies of real hardware.

**Key results** — Illustrates the ROM-to-full-order CBF construction across multiple robot domains, drawing on systems to which these techniques have been experimentally applied (a tutorial/review, so it synthesizes rather than reporting new benchmark numbers).

## Takeaways
- The organizing idea: never build a CBF for the full nonlinear robot — build it on a reduced-order model and transfer the invariance guarantee upward via the ROM-to-full-order relationship.
- Key assumption/limitation: the safety transfer hinges on a valid relationship (e.g., tracking bound / simulation relation) between the ROM and the full-order dynamics; a poor ROM or loose tracking bound weakens the guarantee.
- A tutorial/review synthesizing an active research line rather than a single new result — a good entry point and citation anchor for ROM-based safety.

## Relevance to your work
This is the canonical reference for constructing safety guarantees on complex legged/humanoid systems via reduced-order models — directly foundational to layered safety-critical control; see the related [[@cohen2025safety]].

## Concepts
[[reduced-order-model]] · [[control-barrier-function]] · [[hierarchical-control]]

## Source
- Cited by [[@cohen2025safety]], [[@compton2025dynamic]], [[@compton2025learning]], [[@hierarchies2025motion]]
- bibkeys: `CohenARC24`, `Cohen_2024`, `cohen2024safety`, `cohen2025safety`
- arXiv: https://arxiv.org/abs/2411.16479
