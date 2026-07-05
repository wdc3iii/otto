---
type: paper
citekey: acosta2023bipedal
tags: []
aliases: []
created: 2026-07-05
modified: 2026-07-05
authors:
  - Acosta, Brian
  - Posa, Michael
year: 2023
venue: arXiv:2309.07993 [cs]
doi: 10.48550/arXiv.2309.07993
arxiv: "2309.07993"
url: https://arxiv.org/abs/2309.07993
zotero:
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@acosta2023bipedal.pdf
bibkeys:
  - acosta_bipedal_2023
---

# Bipedal Walking on Constrained Footholds with MPC Footstep Control

> [!info] Acosta, Brian; Posa, Michael · 2023 · arXiv:2309.07993 [cs]

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.

**TL;DR** — A single MIQP model-predictive footstep controller that jointly picks the stepping surface, footstep sequence, sagittal ankle torque, and CoM trajectory to keep an underactuated biped balanced on discontinuous terrain.

**Problem** — Agile underactuated bipeds (small feet, weak ankles) can't rely on ankle strength alone; they must continually re-plan footstep positions to stay balanced, and doing so over discrete choices of steppable surface is combinatorial.

**Method** — Formulate the problem as one Mixed-Integer Quadratic Program that jointly optimizes discrete stepping-surface choice, upcoming footstep positions, sagittal ankle torque, and CoM trajectory to track a velocity command, solved online at 50-200 Hz. A real-time elevation-mapping + convex terrain-decomposition front-end supplies convex polygons of steppable terrain.

**Key results** — Demonstrated in hardware experiments on the underactuated biped Cassie, traversing discontinuous/constrained footholds while tracking commanded velocity.

## Abstract (from bib)
Bipedal robots promise the ability to traverse rough terrain quickly and efficiently, and indeed, humanoid robots can now use strong ankles and careful foot placement to traverse discontinuous terrain. However, more agile underactuated bipeds have small feet and weak ankles, and must constantly adjust their planned footstep position to maintain balance. We introduce a new model-predictive footstep controller which jointly optimizes over the robot's discrete choice of stepping surface, impending footstep position sequence, ankle torque in the sagittal plane, and center of mass trajectory, to track a velocity command. The controller is formulated as a single Mixed Integer Quadratic Program (MIQP) which is solved at 50-200 Hz, depending on terrain complexity. We implement a state of the art r

## Takeaways
- Casting foothold-surface selection + continuous footstep/CoM/ankle optimization as one MIQP is the core idea — discrete terrain choice handled natively rather than by a separate planner.
- Convex decomposition of terrain into polygons is what keeps the mixed-integer problem real-time (50-200 Hz).
- Targets the hard regime (underactuated, weak ankles) where foot placement, not ankle torque, is the primary balance authority.

## Relevance to your work
A representative optimization-based (MIQP) perceptive footstep controller for underactuated bipeds — the classical-planning counterpoint that learning-augmented locomotion work like [[@dai2025walk]] compares against.

## Concepts
[[reduced-order-model]]

## Source
- Cited by [[@dai2025walk]]
- bibkeys: `acosta_bipedal_2023`
- arXiv: https://arxiv.org/abs/2309.07993
- DOI: https://doi.org/10.48550/arXiv.2309.07993
