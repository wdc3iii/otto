---
type: paper
citekey: mayne2000constrained
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- D.Q. Mayne
- J.B. Rawlings
- C.V. Rao
- P.O.M. Scokaert
year: 2000
venue: Automatica
doi: https://doi.org/10.1016/S0005-1098(99)00214-9
arxiv: null
url: https://doi.org/10.1016/S0005-1098(99)00214-9
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: missing
bibkeys:
- mayne2000constrained
---

# Constrained model predictive control: Stability and optimality

> [!info] D.Q. Mayne; J.B. Rawlings; C.V. Rao; P.O.M. Scokaert · 2000 · Automatica

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — The canonical review of constrained model predictive control, laying out the ingredients that make receding-horizon control provably stabilizing and (near-)optimal.

**Problem** — MPC solves a finite-horizon open-loop optimal control problem at each sampling instant using the current state and applies only the first control, repeating each step. Its strength is handling hard constraints on states and controls (why it's widely used in process industries), but this raises the central question the review addresses: when does the receding-horizon policy actually yield closed-loop stability and optimality?

**Method** — A review/synthesis (not experiments) of constrained MPC. It organizes the stability machinery around terminal cost, terminal constraint set, and a terminal (local) controller, using a control Lyapunov / value-function argument to establish closed-loop stability, and discusses how these ingredients relate nominal MPC to infinite-horizon optimality.

**Key results** — Consolidates the field into a common framework showing how terminal conditions guarantee stability of constrained MPC, and surveys robustness considerations for uncertain/disturbed systems.

## Takeaways
- The reference for the terminal-cost + terminal-set + local-controller recipe for stabilizing MPC — the standard vocabulary the whole field still uses.
- Frames MPC stability via value-function/Lyapunov arguments, connecting finite-horizon MPC to infinite-horizon optimal control.
- A survey, so it is a map of results rather than a single new method; specifics live in the cited primary works.

## Relevance to your work
This is the foundational stability-and-optimality reference behind essentially all MPC-based locomotion and robust-MPC work; it is the theoretical bedrock that robust tube-style formulations such as [[@csomayshanklin2024robust]] extend to handle disturbances.

## Abstract (from bib)
Model predictive control is a form of control in which the current control action is obtained by solving, at each sampling instant, a finite horizon open-loop optimal control problem, using the current state of the plant as the initial state; the optimization yields an optimal control sequence and the first control in this sequence is applied to the plant. An important advantage of this type of control is its ability to cope with hard constraints on controls and states. It has, therefore, been widely applied in petro-chemical and related industries where satisfaction of constraints is particularly important because efficiency demands operating points on or close to the boundary of the set of admissible states and controls. In this review, we focus on model predictive control of constrained

## Concepts
[[tube-mpc]]

## Source
- Cited by [[@csomayshanklin2024robust]]
- bibkeys: `mayne2000constrained`
- DOI: https://doi.org/https://doi.org/10.1016/S0005-1098(99)00214-9
