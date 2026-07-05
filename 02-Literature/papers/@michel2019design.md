---
type: paper
citekey: michel2019design
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- N. Michel
- S. Bertrand
- S. Olaru
- G. Valmorbida
- D. Dumur.
year: 2019
venue: IFAC-PapersOnLine
doi: null
arxiv: null
url: https://www.sciencedirect.com/science/article/pii/S2405896319309930
summary: ai-draft
pdf: attachments/@michel2019design.pdf
zotero: null
status: to-read
mine: false
bibkeys:
- MICHEL2019112
---

# Design and flight experiments of a Tube-Based Model Predictive Controller for the AR.Drone 2.0 quadrotor

> [!info] N. Michel; S. Bertrand; S. Olaru; G. Valmorbida; D. Dumur. · 2019 · IFAC-PapersOnLine

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — Designs, implements, and flight-tests a tube-based MPC (TBMPC) law that stabilizes the horizontal dynamics of the AR.Drone 2.0 quadrotor with robust constraint satisfaction.
**Problem** — Applying tube-based robust MPC on real quadrotor hardware requires a disturbance/constraint model grounded in flight data and an invariant-set design that is actually implementable, not just theoretical.
**Method** — Model the horizontal dynamics as a discrete-time linear system with additive disturbance and polytopic constraints, with the model identified from experimental flight data in a form tailored to the subsequent invariant-set (tube) design. The offline-designed ancillary controller keeps the true state in an invariant tube around the nominal MPC trajectory.
**Key results** — A validation flight with the TBMPC law demonstrates robust satisfaction of both state and control-input constraints on the real drone.

## Takeaways
- An applied, experimentally validated instance of rigid-tube MPC: the emphasis is data-driven identification of the disturbance set feeding the invariant-set design.
- Works on the horizontal (linearized) dynamics with polytopic constraints — a linear-system tube MPC, not the nonlinear/dynamic-tube variant.
- Provides hardware evidence that tube MPC yields robust constraint satisfaction in flight, not just in simulation.

## Relevance to your work
A concrete hardware demonstration of tube MPC with an experimentally identified disturbance set — the applied counterpart to the tube-geometry theory behind [[@compton2025dynamic]].

## Abstract (from bib)
This paper focuses on the design, implementation and experimental validation of a Tube-Based Model Predictive Control (TBMPC) law for the stabilization of the horizontal dynamics of an Unmanned Aerial Vehicle (UAV) quadrotor. These dynamics are modelled by a discrete-time linear system subject to additive disturbance and polytopic constraints, which model is derived through an identification strategy from experimental flight data that is adapted to the subsequent design of invariant sets. The results obtained from a validation flight with the TBMPC law are presented to illustrate the robust state and control input constraints satisfaction.

## Concepts
[[tube-mpc]]

## Source
- Cited by [[@compton2025dynamic]]
- bibkeys: `MICHEL2019112`
