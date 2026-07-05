---
type: paper
citekey: yu2024learning
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Yu, Shangqun
- Perera, Nisal
- Marew, Daniel
- Kim, Donghyun
year: 2024
venue: 2024 IEEE-RAS 23rd International Conference on Humanoid Robots (Humanoids)
doi: null
arxiv: '2405.17227'
url: https://arxiv.org/abs/2405.17227
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@yu2024learning.pdf
bibkeys:
- yu2024learning
---

# Learning generic and dynamic locomotion of humanoids across discrete terrains

> [!info] Yu, Shangqun; Perera, Nisal; Marew, Daniel; Kim, Donghyun · 2024 · 2024 IEEE-RAS 23rd International Conference on Humanoid Robots (Humanoids)

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — A hierarchical humanoid locomotion architecture that pairs an RL policy (trained cheaply in simplified environments) with an MPC + whole-body-impulse-control (WBIC) motion controller to dynamically traverse discrete terrains.
**Problem** — Optimization-based control (MPC) is agile but struggles with the nonlinear hybrid dynamics and real-time computation of step location/timing/forces for humanoids, while RL navigates rough terrain but is data-hungry. The paper wants the strengths of both.
**Method** — A neural-network policy learns high-level decisions — gait selection and step positioning — from ground height maps, trained via RL without full-dynamics simulation. A state-of-the-art low-level controller (MPC combined with WBIC) then executes reaction forces and whole-body tracking, so the policy need not learn full dynamics.
**Key results** — Achieves dynamic behaviors (walking, jumping, leaping) over discrete terrains with significantly fewer training samples than conventional RL, and transfers to three different humanoid platforms without retraining (extensively tested in dynamic simulation).

## Takeaways
- Hierarchical split — RL for high-level footstep/gait strategy, model-based MPC+WBIC for execution — cuts RL sample cost and yields cross-robot transfer.
- Terrain awareness comes from ground height maps fed to the policy; the abstract reports simulation validation (no hardware).
- A concrete instance of the "learn the plan, control the body" pattern that keeps the physics in the model-based layer.

## Relevance to your work
A hierarchical RL-over-MPC design for legged locomotion directly relevant to combining learned high-level planning with model-based control; a natural comparison point for [[@dai2025walk]].

## Concepts
[[hierarchical-control]]

## Source
- Cited by [[@dai2025walk]]
- bibkeys: `yu2024learning`
