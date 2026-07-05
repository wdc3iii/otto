---
type: paper
citekey: lavalle2001randomized
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- LaValle, Steven M.
- Kuffner, James J.
year: 2001
venue: The International Journal of Robotics Research
doi: 10.1177/02783640122067453
arxiv: null
url: https://doi.org/10.1177/02783640122067453
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: missing
bibkeys:
- lavalle2001randomized
---

# Randomized Kinodynamic Planning

> [!info] LaValle, Steven M.; Kuffner, James J. · 2001 · The International Journal of Robotics Research

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — The first randomized (RRT-based) approach to kinodynamic planning: finding control inputs that drive a robot between states while respecting nonlinear dynamics and avoiding obstacles.
**Problem** — Kinodynamic planning must satisfy first-order differential constraints on top of obstacle constraints; standard randomized path planners operate in configuration space and do not directly transfer to planning trajectories in the higher-dimensional state space.
**Method** — Recast planning as a motion-planning problem in the state space (configuration + velocity) subject to differential constraints, and solve it by building rapidly-exploring random trees tailored to high-dimensional state spaces. Includes theoretical analysis of the algorithm.
**Key results** — Computes dynamically feasible trajectories in cluttered environments for hovercraft and satellite systems, with state spaces of up to 12 dimensions.

## Takeaways
- Establishes the state-space RRT formulation that underpins most modern kinodynamic sampling planners.
- Differential constraints are handled implicitly by forward-propagating admissible controls rather than by explicit steering, which is the enabling trick for high dimensions.
- Journal companion to LaValle's 1998 RRT technical report ([[@lavalle1998rapidly]]); provides the theoretical grounding.

## Relevance to your work
Foundational reference for planning under dynamics; cited as the sampling-based baseline that reduced-order / reachable-set planners such as [[@csomayshanklin2025dynamically]] aim to make tractable for legged systems by planning over templates instead of the full kinodynamic state space.

## Concepts

## Source
- Cited by [[@csomayshanklin2025dynamically]], [[@hierarchies2025motion]]
- bibkeys: `lavalle2001randomized`
