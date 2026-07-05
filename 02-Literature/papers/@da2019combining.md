---
type: paper
citekey: da2019combining
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Da, Xingye
- Grizzle, Jessy
year: 2019
venue: The International Journal of Robotics Research
doi: 10.1177/0278364919859425
arxiv: null
url: https://doi.org/10.1177/0278364919859425
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: missing
bibkeys:
- da2017combiningtrajectoryoptimizationsupervised
- da_combining_2019
---

# Combining trajectory optimization, supervised machine learning, and model structure for mitigating the curse of dimensionality in the control of bipedal robots

> [!info] Da, Xingye; Grizzle, Jessy · 2019 · The International Journal of Robotics Research

## Summary
> [!note] AI-drafted from the abstract — a base to refine.

**TL;DR** — Embeds a stable bipedal walking gait in an attractive low-dimensional surface of the state space by combining trajectory optimization, supervised machine learning, and the mechanical structure of the robot, yielding a locally exponentially stable periodic orbit in the full-order model.

**Problem** — High-dimensional bipedal models impose a curse of dimensionality on control design; single optimized trajectories give little guidance on how to respond to disturbances.

**Method** — Trajectory optimization first designs an open-loop periodic walking motion of the high-dimensional model, augmented with a carefully chosen set of additional open-loop trajectories that steer toward the nominal motion. Supervised machine learning then extracts a low-dimensional state-variable realization of these trajectories; exploiting the special structure of mechanical/bipedal models, this low-dimensional model is embedded in the original model so the walking motion is locally exponentially stable. The procedure is developed for ODEs and extended to a class of hybrid models.

**Key results** — Realized experimentally on an Atrias-series 3D bipedal robot.

## Abstract (from bib)
To overcome the obstructions imposed by high-dimensional bipedal models, we embed a stable walking motion in an attractive low-dimensional surface of the system’s state space. The process begins with trajectory optimization to design an open-loop periodic walking motion of the high-dimensional model and then adding to this solution a carefully selected set of additional open-loop trajectories of the model that steer toward the nominal motion. A drawback of trajectories is that they provide little information on how to respond to a disturbance. To address this shortcoming, supervised machine learning is used to extract a low-dimensional state-variable realization of the open-loop trajectories. The periodic orbit is now an attractor of the low-dimensional state-variable model but is not attr

## Takeaways
- The core move is data-driven dimensionality reduction: ML compresses a bundle of optimized trajectories into a low-dimensional attractive surface, then mechanical structure is used to make that surface actually attractive in the full model.
- Combines optimization, learning, and model structure rather than betting on any one — an early, principled hybrid vs. pure end-to-end RL.
- Limitation: the attractive low-dimensional realization is learned around a nominal gait, so its validity is local; extended from ODE to hybrid (impact) dynamics for walking.

## Relevance to your work
A foundational reduced-order-model approach to stabilizing bipedal walking that blends trajectory optimization with learning — relevant background for ROM-based locomotion control; see [[@hierarchies2025motion]].

## Concepts
[[reduced-order-model]]

## Source
- Cited by [[@csomayshanklin2024robust]], [[@hierarchies2025motion]]
- bibkeys: `da2017combiningtrajectoryoptimizationsupervised`, `da_combining_2019`
- DOI: https://doi.org/10.1177/0278364919859425
