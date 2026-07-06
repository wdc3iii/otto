---
type: paper
citekey: reher2021lyapunov
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Reher, Jenna
- Ames, Aaron D
year: 2021
venue: preprint arXiv:2107.04241
doi: null
arxiv: '2107.04241'
url: https://arxiv.org/abs/2107.04241
summary: ai-draft
pdf: attachments/@reher2021lyapunov.pdf
zotero: null
status: to-read
mine: false
bibkeys:
- reher2021control
---

# Control lyapunov functions for compliant hybrid zero dynamic walking

> [!info] Reher, Jenna; Ames, Aaron D · 2021 · preprint arXiv:2107.04241
> [!info]- otto authors: [[aaron-ames]]

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — An end-to-end realization of provably stable 3D bipedal walking on the compliant, underactuated Cassie robot, combining hybrid zero dynamics (HZD) gait libraries with control-Lyapunov-function QP controllers.

**Problem** — Nonlinear controllers with formal guarantees promise richer robot behaviors, but actually realizing them on dynamic, underactuated, compliant hardware is difficult in practice.

**Method** — Cassie is modeled as a compliant hybrid system to set up trajectory optimization; a library of compliant walking motions across speeds and directions is compiled and parameterized for real-time use. Control Lyapunov functions are synthesized on top of this gait library and coupled with inverse dynamics to yield optimization-based (QP) controllers, with a theoretical analysis of the controller's stability and tuning properties.

**Key results** — Proves the controller achieves stable locomotion, then demonstrates it end-to-end on Cassie: 3D walking via optimization-based torque control at varied speeds and on different terrains.

## Takeaways
- Bridges formal HZD/CLF theory and messy compliant hardware — the emphasis is "experimentally realizable" CLF control on a real 3D biped.
- CLF-QP + inverse dynamics on a parameterized gait library is the practical recipe; the gait library makes the formal controller real-time.
- Explicit stability proof plus properties useful for tuning, not just an empirical demo.

## Relevance to your work
A reference realization of CLF-based, formally-guaranteed walking on hardware — core lineage for anyone building Lyapunov/QP controllers for legged systems, and the kind of guarantee-carrying locomotion controller that robust-MPC work like [[@csomayshanklin2024robust]] positions itself against.

## Concepts


## Source
- Cited by [[@csomayshanklin2024robust]]
- bibkeys: `reher2021control`
- arXiv: https://arxiv.org/abs/2107.04241
