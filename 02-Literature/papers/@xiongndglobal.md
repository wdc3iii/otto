---
type: paper
citekey: xiongndglobal
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Xiong, Xiaobin
- Reher, Jenna
- Ames, Aaron
year: null
venue: null
doi: 10.48550/arXiv.2011.06050
arxiv: '2011.06050'
url: http://arxiv.org/abs/2011.06050
summary: ai-draft
pdf: attachments/@xiongndglobal.pdf
zotero: null
status: to-read
mine: false
bibkeys:
- xiongGlobalPositionControl2021
---

# Global Position Control on Underactuated Bipedal Robots: Step-to-step Dynamics Approximation for Step Planning

> [!info] Xiong, Xiaobin; Reher, Jenna; Ames, Aaron · n.d. · —
> [!info]- otto authors: [[aaron-ames]]

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.

**TL;DR** — Uses H-LIP-based stepping plus MPC to achieve global position (and turning) control on 3D underactuated bipeds, demonstrated on Cassie.

**Problem** — Global position control is hard for underactuated bipeds because the feet provide no direct actuation to reposition the body; step planning must do the work.

**Method** — Approximates the robot's step-to-step (S2S) dynamics with the H-LIP S2S dynamics, treating step size as the input. An H-LIP-based feedback controller drives the robot to behave like the H-LIP, with the discrepancy confined to an error-invariant set. MPC is then applied to the H-LIP for global position control in 3D, generating desired step sizes for the robot to track; turning is integrated into the step planner.

**Key results** — Verified on the 3D underactuated biped Cassie in simulation with a proof-of-concept hardware experiment.

## Takeaways
- Casts global position control as MPC over the reduced-order H-LIP whose S2S dynamics approximate the true robot, with step size as the control input.
- The error-invariant set bounds the gap between H-LIP and robot, giving a tracking-error guarantee that underpins the planning layer.
- Turning is folded into the same step-planning framework, extending H-LIP stepping beyond straight-line walking.

## Relevance to your work
This is the H-LIP + MPC step-planning layer for global navigation of underactuated bipeds — a foundational reference for hierarchical, reference-guided humanoid navigation such as [[@terrain2026consistent]].

## Abstract (from bib)
Global position control for underactuated bipedal walking is a challenging problem due to the lack of actuation on the feet of the robots. In this paper, we apply the Hybrid-Linear Inverted Pendulum (H-LIP) based stepping on 3D underactuated bipedal robots for global position control. The step-to-step (S2S) dynamics of the H-LIP walking approximates the actual S2S dynamics of the walking of the robot, where the step size is considered as the input. Thus the feedback controller based on the H-LIP approximately controls the robot to behave like the H-LIP, the differences between which stay in an error invariant set. Model Predictive Control (MPC) is applied to the H-LIP for global position control in 3D. The H-LIP stepping then generates desired step sizes for the robot to track. Moreover, t

## Concepts
[[step-to-step-dynamics]] · [[reduced-order-model]] · [[tracking-error-bound]] · [[hierarchical-control]]

## Source
- Cited by [[@terrain2026consistent]]
- bibkeys: `xiongGlobalPositionControl2021`
- arXiv: https://arxiv.org/abs/2011.06050
- DOI: https://doi.org/10.48550/arXiv.2011.06050
- URL: http://arxiv.org/abs/2011.06050
