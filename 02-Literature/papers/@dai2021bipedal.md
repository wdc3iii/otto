---
type: paper
citekey: dai2021bipedal
tags: [locomotion, control]
aliases: []
created: '2026-07-06'
modified: '2026-07-06'
authors:
- Dai, Min
- Xiong, Xiaobin
- Ames, Aaron
year: 2021
venue: arXiv
doi: 10.48550/arXiv.2104.10367
arxiv: '2104.10367'
url: http://arxiv.org/abs/2104.10367
zotero: null
summary: ai-draft
pdf: attachments/@dai2021bipedal.pdf
status: to-read
mine: false
bibkeys:
- daiBipedalWalkingConstrained2021
---

# Bipedal Walking on Constrained Footholds: Momentum Regulation via Vertical COM Control

> [!info] Min Dai; Xiaobin Xiong; Aaron Ames · 2021 · arXiv

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — An online walking-synthesis method regulates angular momentum about the contact pivot through pre-impact vertical COM velocity, enabling dynamic, stable walking on constrained footholds for underactuated bipeds.
**Problem** — Underactuated bipedal robots must walk dynamically and stably when footholds are constrained (stairs, stepping stones), where angular momentum at impact governs stability.
**Method** — Modulate the change in angular momentum about the foot-ground pivot at discrete impact using pre-impact vertical COM velocity; use an underactuated Linear Inverted Pendulum (LIP) model to approximate the walking dynamics and supply the desired post-impact angular momentum per step. Desired outputs are built via online optimization plus closed-form polynomials and tracked by a QP-based controller.
**Key results** — Demonstrated on two robots — AMBER and 3D Cassie — realizing stable walking with constrained footholds on flat ground, stairs, and randomly located stepping stones. (no numeric figures read)

## Takeaways
- Uses vertical COM velocity as the control handle to regulate impact angular momentum — a distinct knob from horizontal foot placement.
- LIP reduced-order model supplies the desired per-step post-impact angular momentum; a QP tracks the synthesized outputs on the full-order robot.
- Handles constrained footholds (stepping stones, stairs) where standard foot-placement freedom is unavailable.

## Relevance to your work
Directly in your wheelhouse (Ames group, CLF/CBF/reduced-order control): vertical-COM momentum regulation with a LIP template is exactly the reduced-order + QP tracking pattern you use, and the constrained-foothold setting maps onto humanoid stepping-stone locomotion on the G1.

## Abstract (from bib)
This paper presents an online walking synthesis methodology to enable dynamic and stable walking on constrained footholds for underactuated bipedal robots. Our approach modulates the change of angular momentum about the foot-ground contact pivot at discrete impact using pre-impact vertical center of mass (COM) velocity. To this end, we utilize the underactuated Linear Inverted Pendulum (LIP) model for approximating the underactuated walking dynamics to provide the desired post-impact angular momentum for each step. Desired outputs are constructed via online optimization combined with closed-form polynomials and tracked via a quadratic program (QP) based controller. This method is demonstrated on two robots, AMBER and 3D Cassie, for which stable walking behaviors with constrained footholds are realized on flat ground, stairs, and randomly located stepping stones.

## Concepts
- [[reduced-order-model]]

## Source
- bibkeys: `daiBipedalWalkingConstrained2021`
- arXiv: http://arxiv.org/abs/2104.10367
- DOI: https://doi.org/10.48550/arXiv.2104.10367
- URL: http://arxiv.org/abs/2104.10367
