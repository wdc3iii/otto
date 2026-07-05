---
type: paper
citekey: burridge1999sequential
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Burridge, Robert R
- Rizzi, Alfred A
- Koditschek, Daniel E
year: 1999
venue: The International Journal of Robotics Research
doi: 10.1177/02783649922066385
arxiv: null
url: https://doi.org/10.1177/02783649922066385
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: missing
bibkeys:
- burridge1999sequential
---

# Sequential composition of dynamically dexterous robot behaviors

> [!info] Burridge, Robert R; Rizzi, Alfred A; Koditschek, Daniel E · 1999 · The International Journal of Robotics Research

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — Introduces *sequential composition* of controllers — chaining local feedback policies so each drives the state into the domain of attraction of the next — demonstrated on a dynamic paddle-juggling/batting task.
**Problem** — A single controller cannot achieve a global task when the free space is disconnected (here, an obstacle splits the ball-on-paddle contact space), so the robot must combine simpler behaviors with guarantees.
**Method** — Composes a palette of local controllers by their domains of attraction ("funnels"): a controller is deployed when the state lies in its domain, and the composition is arranged so that each controller's goal set lies inside the next's domain, yielding a switching policy with a provable overall basin. Applied to a paddle robot batting a thrown ball to a specified rest configuration despite a workspace obstacle.
**Key results** — Guarantees that any ball started in the "safe workspace" stays there and is ultimately driven to the goal; validated with a physical implementation and descriptive experimental statistics.

## Takeaways
- The "funnel"/domain-of-attraction composition is a founding idea for provably-correct switching between local controllers.
- Gives formal safety+convergence guarantees for a composed behavior library without a single global controller — the conceptual root of behavior/controller hierarchies.
- Backward-reachability ordering of controllers (goal of one ⊆ domain of next) is the reusable recipe.

## Relevance to your work
Sequential composition is the classical ancestor of layered/hierarchical control stacks that switch among certified local policies; [[@hierarchies2025motion]] cites it as foundational to composing motion behaviors with guarantees.

## Concepts
[[hierarchical-control]]

## Source
- Cited by [[@hierarchies2025motion]]
- bibkeys: `burridge1999sequential`
