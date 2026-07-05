---
type: paper
citekey: fridovichkeil2017planning
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- David Fridovich-Keil
- Sylvia L. Herbert
- Jaime F. Fisac
- Sampada Deglurkar
- Claire J. Tomlin
year: 2017
venue: Proceedings - IEEE International Conference on Robotics and Automation
doi: null
arxiv: 1710.04731
url: https://arxiv.org/abs/1710.04731
zotero: null
summary: ai-draft
pdf: attachments/@fridovichkeil2017planning.pdf
status: to-read
mine: false
bibkeys:
- Frido2017
---

# Planning, Fast and Slow: A Framework for Adaptive Real-Time Safe Trajectory Planning

> [!info] David Fridovich-Keil; Sylvia L. Herbert; Jaime F. Fisac; Sampada Deglurkar; Claire J. Tomlin · 2017 · Proceedings - IEEE International Conference on Robotics and Automation

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — Extends FaSTrack with "meta-planning": a refined offline computation certifies safe switching between multiple online planners, so a robot can adaptively pick planning behaviors in unknown environments while keeping a strict safety guarantee.
**Problem** — Motion planners are either fast-but-unsafe or safe-but-slow; even FaSTrack fixes a single planner, limiting how a robot can adapt its maneuvering style to what the environment demands.
**Method** — Builds on FaSTrack's offline tracking-error-bound machinery and adds meta-planning: a further offline computation that guarantees safe transitions when switching among several online planners (each with its own tracking tube), letting the system behave differently near obstacles than in free space. Validated in simulation and on hardware.
**Key results** — Demonstrated in simulation and on a Crazyflie 2.0 quadrotor, adapting plans in real time as new obstacles are sensed while maintaining the safety guarantee.

## Takeaways
- Adds a switching layer on top of FaSTrack so multiple planners (conservative vs. aggressive) can be composed safely.
- The safety certificate covers the switches themselves, not just each planner in isolation.
- Inherits FaSTrack's reliance on offline reachability/TEB precomputation, so scaling to high-dimensional tracking models remains the constraint.

## Abstract (from bib)
Motion planning is an extremely well-studied problem in the robotics community, yet existing work largely falls into one of two categories: computationally efficient but with few if any safety guarantees, or able to give stronger guarantees but at high computational cost. This work builds on a recent development called FaSTrack in which a slow offline computation provides a modular safety guarantee for a faster online planner. We introduce the notion of "meta-planning" in which a refined offline computation enables safe switching between different online planners. This provides autonomous systems with the ability to adapt motion plans to a priori unknown environments in real-time as sensor measurements detect new obstacles, and the flexibility to maneuver differently in the presence of obs

## Relevance to your work
A FaSTrack extension toward adaptive, multi-behavior safe planning — relevant to [[@compton2025dynamic]]'s argument that a single fixed tracking tube is overly conservative and should adapt to the situation.

## Concepts
[[reduced-order-model]] [[tracking-error-bound]] [[hierarchical-control]]

## Source
- Cited by [[@compton2025dynamic]]
- bibkeys: `Frido2017`
