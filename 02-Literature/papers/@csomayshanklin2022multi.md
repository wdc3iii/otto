---
type: paper
citekey: csomayshanklin2022multi
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Noel Csomay-Shanklin
- Andrew J. Taylor
- Ugo Rosolia
- Aaron D. Ames
year: 2022
venue: Proceedings of the IEEE Control and Decisions Conference
doi: 10.1109/CDC51059.2022.9992902
arxiv: 2204.00152
url: https://arxiv.org/abs/2204.00152
zotero: null
summary: ai-draft
pdf: attachments/@csomayshanklin2022multi.pdf
status: to-read
mine: false
bibkeys:
- Csomay-S2022
- csomay-shanklin_multi-rate_2022
- csomay2022multi
---

# Multi-Rate Planning and Control of Uncertain Nonlinear Systems: Model Predictive Control and Control Lyapunov Functions

> [!info] Noel Csomay-Shanklin; Andrew J. Taylor; Ugo Rosolia; Aaron D. Ames · 2022 · Proceedings of the IEEE Control and Decisions Conference
> [!info]- otto authors: [[aaron-ames]] · [[noel-csomay-shanklin]]

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — A multi-rate architecture that plans continuous reference trajectories with a linearized model and MPC, then tracks them on the full nonlinear model with CLFs, with Bézier curves stitching the two layers so constraints provably hold across the whole system.
**Problem** — Constructive nonlinear-control methods usually flatten the natural multi-timescale hierarchy onto a single rate, which limits rigorous constraint- and input-satisfaction guarantees for the complete closed loop.
**Method** — A slow MPC layer plans continuous reference trajectories over a linearized model; a fast CLF-based controller tracks them on the full-order nonlinear dynamics. Continuity and constraint satisfaction are enforced by parameterizing the reference as Bézier curves, so planning a finite sequence of control points yields a continuous constraint-respecting trajectory. Everything is posed as efficiently solvable convex programs.
**Key results** — Demonstrated in simulation; the Bézier parameterization is what lets the discrete planned points certify continuous-time constraint satisfaction.

## Takeaways
- Two-rate MPC-plans-reference / CLF-tracks split with explicit inter-layer certificates, rather than a single flattened controller.
- Bézier curves are the key device: convex-hull properties turn discrete decision variables into continuous-trajectory guarantees.
- Uses a linearized planning model, so the guarantees lean on the linearization/tracking-error accounting between layers.

## Abstract (from bib)
Modern control systems must operate in increasingly complex environments subject to safety constraints and input limits, and are often implemented in a hierarchical fashion with different controllers running at multiple time scales. Yet traditional constructive methods for nonlinear controller synthesis typically "flatten"this hierarchy, focusing on a single time scale, and thereby limited the ability to make rigorous guarantees on constraint satisfaction that hold for the entire system. In this work we seek to address the stabilization of constrained nonlinear systems through a multi-rate control architecture. This is accomplished by iteratively planning continuous reference trajectories for a nonlinear system using a linearized model and Model Predictive Control (MPC), and tracking said 

## Relevance to your work
This is the MPC-plans / CLF-tracks multi-rate template underpinning [[@csomayshanklin2024robust]] and the dynamic-tube line — it establishes the layered planning/tracking decomposition with inter-layer constraint guarantees that later work makes robust and tube-based.

## Concepts
[[hierarchical-control]] [[tracking-error-bound]] [[tube-mpc]]

## Source
- Cited by [[@compton2025dynamic]], [[@csomayshanklin2024robust]], [[@csomayshanklin2025dynamically]]
- bibkeys: `Csomay-S2022`, `csomay-shanklin_multi-rate_2022`, `csomay2022multi`
- DOI: https://doi.org/10.1109/CDC51059.2022.9992902
