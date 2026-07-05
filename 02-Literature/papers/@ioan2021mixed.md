---
type: paper
citekey: ioan2021mixed
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Ioan, Daniel
- Prodan, Ionela
- Olaru, Sorin
- Stoican, Florin
- Niculescu, Silviu-Iulian
year: 2021
venue: Annual Reviews in Control
doi: 10.1016/j.arcontrol.2020.10.008
arxiv: null
url: https://doi.org/10.1016/j.arcontrol.2020.10.008
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: missing
bibkeys:
- bigM
---

# Mixed-integer programming in motion planning

> [!info] Ioan, Daniel; Prodan, Ionela; Olaru, Sorin; Stoican, Florin; Niculescu, Silviu-Iulian · 2021 · Annual Reviews in Control

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — A survey of how mixed-integer programming (MIP) is used to formulate and solve motion-planning problems.
**Problem** — Motion planning is often either a selection among a finite set of alternatives or a constrained optimization over a *non-convex* domain (obstacles, discrete mode choices) — both awkward for purely continuous solvers.
**Method** — Reviews past and present MIP-based approaches, arguing that MIP's modeling capabilities and versatility make it a natural fit for these two problem classes, and traces how increased compute and theoretical advances turned MIP from a reluctantly-used tool into a mainstream one.
**Key results** — Consolidates the MIP-in-motion-planning literature and its modeling patterns (encoding non-convex free-space and discrete decisions as integer constraints); a review rather than a new algorithm.

## Takeaways
- MIP is the canonical way to encode obstacle avoidance / discrete mode selection (e.g., big-M constraints, hence the note's `bigM` bibkey) inside an optimization-based planner.
- The practical cost is combinatorial: solve time is the recurring bottleneck, motivating relaxations and warm-starting.
- Useful as an entry-point reference into the whole MIP-planning landscape.

## Relevance to your work
Layered planning/control stacks lean on MIP to make the discrete footstep/contact and obstacle decisions the continuous controller then tracks; [[@hierarchies2025motion]] cites it for the mixed-integer formulation of its planning layer.



## Concepts

## Source
- Cited by [[@csomayshanklin2025dynamically]], [[@hierarchies2025motion]]
- bibkeys: `bigM`
