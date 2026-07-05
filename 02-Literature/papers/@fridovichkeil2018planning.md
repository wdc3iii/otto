---
type: paper
citekey: fridovichkeil2018planning
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Fridovich-Keil, David
- Herbert, Sylvia L
- Fisac, Jaime F
- Deglurkar, Sampada
- Tomlin, Claire J
year: 2018
venue: 2018 IEEE International Conference on Robotics and Automation (ICRA)
doi: null
arxiv: '1710.04731'
url: https://arxiv.org/abs/1710.04731
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@fridovichkeil2018planning.pdf
bibkeys:
- fridovich-keil_planning_2018
---

# Planning, fast and slow: A framework for adaptive real-time safe trajectory planning

> [!info] Fridovich-Keil, David; Herbert, Sylvia L; Fisac, Jaime F; Deglurkar, Sampada; Tomlin, Claire J · 2018 · 2018 IEEE International Conference on Robotics and Automation (ICRA)

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.

**TL;DR** — A FaSTrack-based "meta-planning" framework that enables safe, real-time trajectory planning by letting a fast online planner adapt (and switch between planners) while a slow offline reachability computation supplies a strict safety guarantee.

**Problem** — Motion planners are typically either computationally efficient with few safety guarantees, or provide strong guarantees at high computational cost; neither adapts safely in real time to unknown environments.

**Method** — Builds on FaSTrack, where a slow offline computation yields a modular tracking-error safety guarantee for a faster online planner. Introduces *meta-planning*: a refined offline computation that enables safe switching between different online planners, so the system can maneuver differently near obstacles than in free space while always maintaining the safety bound as new obstacles are sensed.

**Key results** — Demonstrated in simulation and on hardware — a small Crazyflie 2.0 quadrotor — planning safely in a priori unknown environments in real time.

## Takeaways
- Fast/slow decomposition: precompute a tracking-error bound (a "safety tube" between the simplified planner model and the true dynamics) offline, then plan cheaply online inside it.
- Meta-planning adds a layer that safely switches among planners, trading conservativeness for agility depending on the local obstacle situation.
- The offline guarantee is per planner-tracker pair (HJ reachability), so richer dynamics mean heavier offline computation.

## Relevance to your work
FaSTrack's precomputed tracking-error bound between a planning model and full dynamics is the archetypal reduced-order-planner + certified-tube guarantee that the locomotion hierarchy in [[@hierarchies2025motion]] generalizes.

## Concepts
[[tracking-error-bound]], [[hierarchical-control]], [[reduced-order-model]]

## Source
- Cited by [[@csomayshanklin2025dynamically]], [[@hierarchies2025motion]]
- bibkeys: `fridovich-keil_planning_2018`
- arXiv: https://arxiv.org/abs/1710.04731
