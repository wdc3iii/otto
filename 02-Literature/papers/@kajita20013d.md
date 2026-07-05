---
type: paper
citekey: kajita20013d
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Kajita, S.
- Kanehiro, F.
- Kaneko, K.
- Yokoi, K.
- Hirukawa, H.
year: 2001
venue: Proceedings 2001 IEEE/RSJ International Conference on Intelligent Robots and
  Systems
doi: 10.1109/IROS.2001.973365
arxiv: null
url: https://doi.org/10.1109/IROS.2001.973365
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: missing
bibkeys:
- kajita20013d
- kajita_3d_2001
---

# The 3D linear inverted pendulum mode: a simple modeling for a biped walking pattern generation

> [!info] Kajita, S.; Kanehiro, F.; Kaneko, K.; Yokoi, K.; Hirukawa, H. · 2001 · Proceedings 2001 IEEE/RSJ International Conference on Intelligent Robots and Systems

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — Introduces the 3D Linear Inverted Pendulum Mode (3D-LIPM), a simple linear reduced-order model for generating 3D biped walking patterns.
**Problem** — 3D biped walking needs a tractable model for real-time gait/pattern generation, but full dynamics are nonlinear and high-dimensional.
**Method** — Constrains the CoM of a 3D inverted pendulum to move on an arbitrarily defined plane, which yields simple linear dynamics (the 3D-LIPM). The geometric structure of the resulting trajectories is analyzed and used to derive a walking-pattern-generation method.
**Key results** — Demonstrated in simulation with a 12-DOF biped robot model performing walking control under the 3D-LIPM.

## Takeaways
- The LIP model is the canonical reduced-order template for legged locomotion — CoM height held constant gives closed-form linear dynamics.
- Constraining motion to a plane is what linearizes the pendulum, enabling analytic trajectory design.
- A pattern-generation abstraction, not a full stabilizing controller — later work layers whole-body/ZMP control on top.

## Relevance to your work
The LIP is the workhorse reduced-order model for velocity-conditioned gait planning in both classical and learning-based locomotion pipelines. See [[@csomayshanklin2024robust]].

## Abstract (from bib)
For 3D walking control of a biped robot we analyze the dynamics of a three-dimensional inverted pendulum in which motion is constrained to move along an arbitrarily defined plane. This analysis leads us a simple linear dynamics, the Three-Dimensional Linear Inverted Pendulum Mode (SD-LIPM). Geometric nature of trajectories under the 3D-LIPM and a method for walking pattern genemtion are discussed. A simulation result of a walking control using a 12 d.0.f. biped robot model is also shown.

## Concepts
[[reduced-order-model]]

## Source
- Cited by [[@csomayshanklin2024robust]], [[@olkin2026stability]]
- bibkeys: `kajita20013d`, `kajita_3d_2001`
- DOI: https://doi.org/10.1109/IROS.2001.973365
