---
type: paper
citekey: griffin2019footstep
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Griffin, Robert J.
- Wiedebach, Georg
- McCrory, Stephen
- Bertrand, Sylvain
- Lee, Inho
- Pratt, Jerry
year: 2019
venue: 2019 IEEE-RAS 19th International Conference on Humanoid Robots (Humanoids)
doi: 10.1109/Humanoids43949.2019.9035046
arxiv: 1907.08673
url: https://arxiv.org/abs/1907.08673
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@griffin2019footstep.pdf
bibkeys:
- griffin_footstep_2019
---

# Footstep Planning for Autonomous Walking Over Rough Terrain

> [!info] Griffin, Robert J.; Wiedebach, Georg; McCrory, Stephen; Bertrand, Sylvain; Lee, Inho; Pratt, Jerry · 2019 · 2019 IEEE-RAS 19th International Conference on Humanoid Robots (Humanoids)

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — An A* footstep planner over a planar-region terrain model that lets humanoids autonomously plan steps across rough, cluttered ground.
**Problem** — Autonomous humanoid operation needs fast, efficient computation of feasible footsteps to a goal over rough terrain, without operator teleoperation.
**Method** — The environment is represented as planar regions, and an A* search plans footsteps over a discretized footstep graph. Partial footholds are admitted to expand the set of usable steps, and solutions are post-processed to recover better placements lying between lattice cells.
**Key results** — Demonstrated across virtual and real-world environments, including cases requiring partial footholds and rough terrain, on the Atlas and Valkyrie humanoids.

## Takeaways
- Planar-region terrain abstraction plus A* is a practical route to real-time footstep planning on hardware.
- Allowing partial footholds materially increases the number of viable steps in constrained terrain.
- Purely a graph-search planner: it produces footstep sequences, leaving dynamic tracking/balance to a lower-level controller.

## Relevance to your work
Classical perceptive footstep planning of exactly the kind a learned or hierarchical walking controller like [[@dai2025walk]] must either replace or sit on top of; a useful baseline for how rough-terrain foothold selection was handled before RL.

## Abstract (from bib)
To increase the speed of operation and reduce operator burden, humanoid robots must be able to function autonomously, even in complex, cluttered environments. For this to be possible, they must be able to quickly and efficiently compute desired footsteps to reach a goal. In this work, we present a new A * footstep planner that utilizes a planar region representation of the environment enable footstep planning over rough terrain. To increase the number of available footholds, we present an approach to allow the use of partial footholds during the planning process. The footstep plan solutions are then post-processed to capture better solutions that lie between the lattice discretization of the footstep graph. We then demonstrate this planner over a variety of virtual and real world environme

## Concepts


## Source
- Cited by [[@dai2025walk]]
- bibkeys: `griffin_footstep_2019`
- DOI: https://doi.org/10.1109/Humanoids43949.2019.9035046
