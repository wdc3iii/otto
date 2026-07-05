---
type: paper
citekey: lin2021long
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Lin, Yu-Chi
- Berenson, Dmitry
year: 2021
venue: Autonomous Robots
doi: 10.1007/s10514-021-09996-3
arxiv: null
url: https://link.springer.com/article/10.1007/s10514-021-09996-3
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: missing
bibkeys:
- lin2021long
---

# Long-horizon humanoid navigation planning using traversability estimates and previous experience

> [!info] Lin, Yu-Chi; Berenson, Dmitry · 2021 · Autonomous Robots

## Summary
> [!note] AI-drafted from the abstract/publisher summary — a base to refine.
**TL;DR** — A long-horizon humanoid navigation planner that uses learned traversability estimates plus a divide-and-conquer strategy to plan footstep and palm-contact sequences across cluttered, uneven terrain far faster than planning contacts everywhere.
**Problem** — Planning humanoid navigation over rough terrain may require non-gaited contacts (hands as well as feet) to cross gaps, avoid obstacles, or keep balance; full contact-space planning over long horizons is prohibitively expensive.
**Method** — Machine learning is used to estimate how traversable a region is (how likely feasible hand/foot placements exist for balance). A divide-and-conquer scheme splits a route into hard-to-traverse sections, where the learning-guided contact planner is invoked, and easy sections handled by cheaper path planning, reusing previous experience to speed search.
**Key results** — Reported to find goal-reaching plans faster than planning full contact sequences uniformly along the path, on stair and uneven-terrain scenarios.

## Takeaways
- Traversability learned as a heuristic is what makes long-horizon contact planning tractable — it tells the planner where the expensive contact search is even worth running.
- Divide-and-conquer (learned contact planning only on the hard segments) is the core efficiency lever; easy stretches fall back to standard path planning.
- Treats hands as first-class contacts for balance/locomotion, not just feet — relevant to loco-manipulation over rubble.

## Relevance to your work
A terrain-aware humanoid navigation reference for [[@terrain2026consistent]]: it shows how learned traversability estimates gate an expensive contact/footstep planner, a planning-side complement to learning consistent terrain representations for locomotion.

## Concepts
[[hierarchical-control]]

## Source
- Cited by [[@terrain2026consistent]]
- bibkeys: `lin2021long`
