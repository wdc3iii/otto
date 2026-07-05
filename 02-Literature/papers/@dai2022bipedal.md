---
type: paper
citekey: dai2022bipedal
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Dai, Min
- Xiong, Xiaobin
- Ames, Aaron
year: 2022
venue: 2022 International Conference on Robotics and Automation (ICRA)
doi: 10.1109/ICRA46639.2022.9812247
arxiv: null
url: https://doi.org/10.1109/ICRA46639.2022.9812247
zotero: null
summary: ai-draft
pdf: missing
status: to-read
mine: false
bibkeys:
- dai_bipedal_2022
---

# Bipedal Walking on Constrained Footholds: Momentum Regulation via Vertical COM Control

> [!info] Dai, Min; Xiong, Xiaobin; Ames, Aaron · 2022 · 2022 International Conference on Robotics and Automation (ICRA)

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — An online walking-synthesis method that regulates angular momentum via pre-impact vertical COM velocity to achieve dynamic, stable underactuated bipedal walking on constrained footholds.
**Problem** — Underactuated bipeds must place feet on prescribed footholds (stairs, stepping stones) while remaining dynamically stable, which requires shaping the momentum transferred at each impact.
**Method** — Uses an underactuated Linear Inverted Pendulum (LIP) model to set the desired post-impact angular momentum about the foot-ground pivot for each step, then modulates that momentum through the pre-impact vertical COM velocity. Desired outputs are built from online optimization plus closed-form polynomials and tracked by a QP-based controller.
**Key results** — Demonstrated on AMBER and 3D Cassie, achieving stable walking with constrained footholds on flat ground, stairs, and randomly located stepping stones (no numeric metrics seen).

## Takeaways
- Vertical-COM velocity is used as the control knob for regulating discrete-impact angular momentum — a compact handle on foothold-constrained gait.
- Leans on the reduced-order (underactuated LIP) template to specify per-step momentum targets, tracked by a QP controller.
- Model-based counterpart to learning approaches for the same stepping-stone problem.

## Relevance to your work
A model-based, momentum-regulating template for foothold-constrained walking, cited by [[@dai2025walk]] as prior art on walking across constrained footholds.

## Abstract (from bib)
This paper presents an online walking synthesis methodology to enable dynamic and stable walking on constrained footholds for underactuated bipedal robots. Our approach modulates the change of angular momentum about the foot-ground contact pivot at discrete impact using pre-impact vertical center of mass (COM) velocity. To this end, we utilize the underactuated Linear Inverted Pendulum (LIP) model for approximating the underactuated walking dynamics to provide the desired post-impact angular momentum for each step. Desired outputs are constructed via online optimization combined with closed-form polynomials and tracked via a quadratic program (QP) based controller. This method is demonstrated on two robots, AMBER and 3D Cassie, for which stable walking behaviors with constrained footholds 

## Concepts
[[reduced-order-model]]

## Source
- Cited by [[@dai2025walk]]
- bibkeys: `dai_bipedal_2022`
- DOI: https://doi.org/10.1109/ICRA46639.2022.9812247
