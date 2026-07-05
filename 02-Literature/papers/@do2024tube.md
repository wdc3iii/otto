---
type: paper
citekey: do2024tube
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Do, Huu-Thinh
- Prodan, Ionela
year: 2024
venue: 2024 European Control Conference
doi: 10.23919/ECC64448.2024.10591195
arxiv: null
url: https://hal.science/hal-04620816
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@do2024tube.pdf
bibkeys:
- do:hal-04620816
---

# Tube MPC via flatness for multicopter trajectory tracking

> [!info] Do, Huu-Thinh; Prodan, Ionela · 2024 · 2024 European Control Conference

## Summary
> [!note] AI-drafted from the abstract — a base to refine.

**TL;DR** — Uses differential flatness to reformulate quadcopter trajectory tracking as a constrained linear time-invariant problem, then applies tube MPC for robust tracking under disturbances.

**Problem** — Nonlinearity and dimensionality make online optimization-based control of multicopters expensive, especially with disturbances; the flatness-induced constraints are usually crudely approximated or ignored.

**Method** — A flatness-based coordinate change renders the closed-loop dynamics linear at the cost of more convoluted constraints; with a suitable parameterization of the feasible domain, trajectory tracking becomes stabilization of a constrained LTI system under disturbances, which is then handled by a robust (tube) MPC controller.

**Key results** — Validated in simulation and hardware experiments on a quadcopter, showing robust trajectory tracking under disturbances.

## Takeaways
- Flatness turns a hard nonlinear robust-tracking problem into a tractable constrained-LTI tube-MPC problem.
- The care point is honoring the "convoluted" flatness-transformed constraints rather than approximating them away.
- Concrete instance of tube MPC applied via a reduced/transformed model for aerial trajectory tracking.

## Relevance to your work
A flatness-plus-tube-MPC recipe for robust trajectory tracking under disturbances, closely parallel to dynamic-tube approaches for locomotion. See [[@compton2025dynamic]].

## Concepts
[[tube-mpc]]

## Source
- Cited by [[@compton2025dynamic]]
- bibkeys: `do:hal-04620816`
