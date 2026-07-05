---
type: paper
citekey: pappas2002consistent
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- G. J. Pappas
- S. Simi\'c
year: 2002
venue: TAC
doi: 10.1109/TAC.2002.1000269
arxiv: null
url: https://doi.org/10.1109/TAC.2002.1000269
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: missing
bibkeys:
- PappasTAC02
---

# Consistent Abstractions of Affine Control Systems

> [!info] G. J. Pappas; S. Simi\'c · 2002 · TAC

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — A canonical construction for abstracting affine control systems along a smooth surjective map, with conditions under which the abstraction preserves reachability / local accessibility.
**Problem** — Extends hierarchical abstraction beyond linear systems: given a nonlinear (affine) control system and a map onto coarser variables, when does the abstracted model faithfully preserve reachability properties so that reasoning at the abstract level is valid?
**Method** — Given an affine control system and a smooth surjective map, the paper gives a canonical construction that extracts an affine control system governing the abstracted variables, then derives conditions on the abstraction maps that render the original and abstracted systems equivalent from a local-accessibility standpoint.
**Key results** — These consistent, accessibility-preserving abstraction hierarchies are worked out for several classes of affine systems — linear, bilinear, drift-free, and strict-feedback.

## Takeaways
- Generalizes hierarchical consistency from controllability of linear systems to local accessibility of affine nonlinear systems.
- The abstraction of an affine system is itself constructively an affine system, so the hierarchy can be iterated.
- Consistency conditions are stated on the abstraction map, giving a recipe for *designing* valid reduced models rather than merely checking them.

## Relevance to your work
The nonlinear counterpart to hierarchically-consistent control: it formalizes when a reduced-order abstraction of a nonlinear robot model preserves what you can plan for, grounding the reduced-order planning used in layered safety schemes like [[@cohen2025safety]].

## Concepts
[[hierarchical-control]] · [[reduced-order-model]]

## Source
- Cited by [[@cohen2025safety]]
- bibkeys: `PappasTAC02`
