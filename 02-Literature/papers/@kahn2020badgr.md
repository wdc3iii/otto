---
type: paper
citekey: kahn2020badgr
tags: [navigation, rl, method]
aliases: []
created: '2026-07-06'
modified: '2026-07-07'
authors:
- Kahn, Gregory
- Abbeel, Pieter
- Levine, Sergey
year: 2020
venue: arXiv
doi: 10.48550/arXiv.2002.05700
arxiv: '2002.05700'
url: http://arxiv.org/abs/2002.05700
zotero: null
summary: ai-draft
pdf: attachments/@kahn2020badgr.pdf
status: to-read
mine: false
bibkeys:
- kahnBADGRAutonomousSelfSupervised2020
---

# BADGR: An Autonomous Self-Supervised Learning-Based Navigation System

> [!info] Gregory Kahn; Pieter Abbeel; Sergey Levine · 2020 · arXiv

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — BADGR is an end-to-end, self-supervised navigation system that learns physical navigational affordances from real-world off-policy data — moving beyond purely geometric traversability — with no simulation or human supervision.
**Problem** — Purely geometric navigation misjudges affordances (e.g. avoiding traversable tall grass as if untraversable) and can fail to reach goals.
**Method** — Learn navigational affordances from experience using self-supervised off-policy data gathered directly in real-world environments; end-to-end learning-based mobile robot navigation.
**Key results** — Navigates real-world urban and off-road environments with geometrically distracting obstacles; incorporates terrain preferences, generalizes to novel environments, and keeps improving autonomously by gathering more data (no numeric figures read).

## Takeaways
- Reframes traversability as learned physical affordance, not geometry — tall grass is passable, so don't treat it as an obstacle.
- Fully self-supervised from real off-policy data: no simulator, no human labels; improves with more experience.
- Terrain-preference conditioning lets the same system prefer smoother/faster paths.

## Relevance to your work
Core reference for learned traversability and mapless-style navigation: the affordance-over-geometry argument is directly relevant to capability-aware navigation on legged robots, where what is "traversable" depends on the platform's actual locomotion capability rather than pure geometry.

## Abstract (from bib)
Mobile robot navigation is typically regarded as a geometric problem, in which the robot's objective is to perceive the geometry of the environment in order to plan collision-free paths towards a desired goal. However, a purely geometric view of the world can can be insufficient for many navigation problems. For example, a robot navigating based on geometry may avoid a field of tall grass because it believes it is untraversable, and will therefore fail to reach its desired goal. In this work, we investigate how to move beyond these purely geometric-based approaches using a method that learns about physical navigational affordances from experience. Our approach, which we call BADGR, is an end-to-end learning-based mobile robot navigation system that can be trained with self-supervised off-policy data gathered in real-world environments, without any simulation or human supervision. BADGR can navigate in real-world urban and off-road environments with geometrically distracting obstacles. It can also incorporate terrain preferences, generalize to novel environments, and continue to improve autonomously by gathering more data. Videos, code, and other supplemental material are available on our website https://sites.google.com/view/badgr

## Concepts
- [[traversability-estimation]]
- [[capability-awareness]]
- [[forward-dynamics-model]] — learns a self-supervised predictive model of navigation outcomes (collision, bumpiness, position) from real off-policy data and plans against it: the FDM pattern (learned predictor of platform behavior) in a wheeled setting.

## Source
- bibkeys: `kahnBADGRAutonomousSelfSupervised2020`
- arXiv: http://arxiv.org/abs/2002.05700
- DOI: https://doi.org/10.48550/arXiv.2002.05700
- URL: http://arxiv.org/abs/2002.05700
