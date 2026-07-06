---
type: paper
citekey: csomayshanklin2023nonlinear
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Csomay-Shanklin, Noel
- Dorobantu, Victor D
- Ames, Aaron D
year: 2023
venue: 2023 IEEE (ICRA)
doi: null
arxiv: 2209.11808
url: https://arxiv.org/abs/2209.11808
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@csomayshanklin2023nonlinear.pdf
bibkeys:
- Csomay2023
- NoelICRA23
- csomay-shanklin_nonlinear_2023
- csomay2023nonlinear
---

# Nonlinear Model Predictive Control of a 3D Hopping Robot: Leveraging Lie Group Integrators for Dynamically Stable Behaviors

> [!info] Csomay-Shanklin, Noel; Dorobantu, Victor D; Ames, Aaron D · 2023 · 2023 IEEE (ICRA)
> [!info]- otto authors: [[aaron-ames]] · [[noel-csomay-shanklin]]

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — Hybrid nonlinear MPC on top of a low-level feedback controller, arranged in a multi-rate hierarchy and made geometrically consistent via Lie group integrators, achieves dynamically stable 3D hopping.
**Problem** — Controlled hopping is hard: long underactuated flight phases combined with very short ground phases where ground interaction must be modulated to regulate global state; achieving rich behaviors on the rotation manifold requires geometrically consistent planning and control.
**Method** — A hybrid nonlinear MPC planner is paired with a low-level feedback controller in a multi-rate hierarchy. Both layers are designed on the manifold of rotations using Lie group integrators and appropriately matched feedback controllers, so the planned and tracked trajectories stay geometrically consistent through the hybrid (flight/ground) dynamics.
**Key results** — Experimentally demonstrates stable 3D hopping on hardware, and shows trajectory tracking and flipping in simulation.

## Takeaways
- The multi-rate split (slower nonlinear MPC planner + fast low-level feedback) is the organizing idea — a concrete instance of layered planning/control for hybrid legged systems.
- Geometric consistency across layers (Lie group integrators for SO(3)) matters for rich rotational behaviors like flips; naive Euclidean integration would break this.
- Hopping is the stress test because underactuation plus brief contact leaves little authority to regulate global state.

## Relevance to your work
A direct predecessor for layered / multi-rate planning-and-control on underactuated legged robots, tying nonlinear MPC planning to low-level feedback on the rotation manifold. See [[@hierarchies2025motion]].

## Concepts
[[hierarchical-control]]

## Source
- Cited by [[@cohen2025safety]], [[@compton2024constructive]], [[@compton2025dynamic]], [[@compton2025learning]], [[@csomayshanklin2024robust]], [[@csomayshanklin2025dynamically]], [[@hierarchies2025motion]]
- bibkeys: `Csomay2023`, `NoelICRA23`, `csomay-shanklin_nonlinear_2023`, `csomay2023nonlinear`
