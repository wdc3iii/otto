---
type: paper
citekey: tracy2025trajectory
tags: [planning, control, method]
aliases: []
created: '2026-07-06'
modified: '2026-07-06'
authors:
- Tracy, Kevin
- Zhang, John Z.
- Arrizabalaga, Jon
- Schaal, Stefan
- Tassa, Yuval
- Erez, Tom
- Manchester, Zachary
year: 2025
venue: arXiv
doi: 10.48550/arXiv.2509.26575
arxiv: '2509.26575'
url: http://arxiv.org/abs/2509.26575
zotero: null
summary: ai-draft
pdf: attachments/@tracy2025trajectory.pdf
status: to-read
mine: false
bibkeys:
- tracyTrajectoryBundleMethod2025
---

# The Trajectory Bundle Method: Unifying Sequential-Convex Programming and Sampling-Based Trajectory Optimization

> [!info] Kevin Tracy; John Z. Zhang; Jon Arrizabalaga; Stefan Schaal; Yuval Tassa; Tom Erez; Zachary Manchester · 2025 · arXiv

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — A derivative-free trajectory optimization framework that builds convex approximations from samples of the dynamics/cost/constraints, unifying sequential convex programming with sampling-based methods like MPPI.
**Problem** — Nonconvex trajectory optimization is usually solved as a sequence of convex problems using Taylor-series (derivative-based) local approximations, which breaks down when differentiation is expensive or unavailable.
**Method** — Form the convex approximations in a derivative-free manner by sampling the dynamics, cost, and constraint functions and letting the solver interpolate between the samples (sequential convex programming without gradients). The framework subsumes model-predictive path integral (MPPI) control as a special case and generalizes it to support multiple shooting and general equality/inequality constraints normally tied to derivative-based SCP.
**Key results** — Presented as simple, flexible, and capable of solving a wide variety of practical motion planning and control problems; unifies sampling-based and SCP families (no numeric figures read).

## Takeaways
- Derivative-free convexification: sample dynamics/cost/constraints and interpolate instead of Taylor-expanding — useful when gradients are costly or unavailable.
- MPPI falls out as a special case; the method adds multiple shooting and general (in)equality constraints on top.
- Bridges the sampling-based vs. sequential-convex-programming divide under one framework.

## Relevance to your work
Relevant to your classical planning/control side (MPC, optimal control, tube-MPC): a derivative-free SCP that generalizes MPPI and adds hard constraints is a candidate tool for motion planning on contact-rich, hard-to-differentiate legged dynamics.

## Abstract (from bib)
We present a unified framework for solving trajectory optimization problems in a derivative-free manner through the use of sequential convex programming. Traditionally, nonconvex optimization problems are solved by forming and solving a sequence of convex optimization problems, where the cost and constraint functions are approximated locally through Taylor series expansions. This presents a challenge for functions where differentiation is expensive or unavailable. In this work, we present a derivative-free approach to form these convex approximations by computing samples of the dynamics, cost, and constraint functions and letting the solver interpolate between them. Our framework includes sample-based trajectory optimization techniques like model-predictive path integral (MPPI) control as a special case and generalizes them to enable features like multiple shooting and general equality and inequality constraints that are traditionally associated with derivative-based sequential convex programming methods. The resulting framework is simple, flexible, and capable of solving a wide variety of practical motion planning and control problems.

## Concepts
<!-- [[03-Concepts]] links added when read -->

## Source
- bibkeys: `tracyTrajectoryBundleMethod2025`
- arXiv: http://arxiv.org/abs/2509.26575
- DOI: https://doi.org/10.48550/arXiv.2509.26575
- URL: http://arxiv.org/abs/2509.26575
