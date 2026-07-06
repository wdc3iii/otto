---
type: paper
citekey: xiong2019orbit
tags: [locomotion, control]
aliases: []
created: '2026-07-06'
modified: '2026-07-06'
authors:
- Xiong, Xiaobin
- Ames, Aaron D.
year: 2019
venue: '2019 IEEE/RSJ International Conference on Intelligent Robots and Systems (IROS)'
doi: 10.1109/IROS40897.2019.8968162
arxiv: null
url: https://ieeexplore.ieee.org/document/8968162
zotero: null
summary: ai-draft
pdf: attachments/@xiong2019orbit.pdf
status: to-read
mine: false
bibkeys:
- xiongOrbitCharacterizationStabilization2019
---

# Orbit Characterization, Stabilization and Composition on 3D Underactuated Bipedal Walking via Hybrid Passive Linear Inverted Pendulum Model

> [!info] Xiaobin Xiong; Aaron D. Ames · 2019 · 2019 IEEE/RSJ International Conference on Intelligent Robots and Systems (IROS)

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — Introduces the Hybrid passive Linear Inverted Pendulum (H-LIP) model to geometrically characterize P1/P2 periodic walking orbits and designs step-to-step stepping controllers that globally stabilize them for 3D underactuated bipedal walking.
**Problem** — Generating and stabilizing continuous 3D underactuated bipedal walking gaits is difficult.
**Method** — Propose an H-LIP model to characterize, stabilize, and compose periodic orbits. Period-1 (P1) and Period-2 (P2) orbits are geometrically characterized in the H-LIP state space; stepping controllers are designed for global stabilization, with valid gain ranges and optimality derived. The optimal stepping controller creates and stabilizes robot walking; an actuated Spring-Loaded Inverted Pendulum (aSLIP) model and the underactuated robot Cassie serve as illustrations.
**Key results** — aSLIP walking with P1/P2 orbits and Cassie walking with all 3D compositions of P1/P2 orbits are smoothly generated and stabilized starting from a stepping-in-place motion (no numeric figures read).

## Takeaways
- H-LIP reduced-order model gives a geometric characterization of P1/P2 walking orbits and a step-to-step (stepping) controller with derived valid/optimal gain ranges.
- Global stabilization of the orbits, composable into 3D gaits and initiated from stepping-in-place.
- Demonstrated across an aSLIP template and the underactuated Cassie biped.

## Relevance to your work
Foundational for your reduced-order-model + classical-control line on bipeds: the H-LIP and its step-to-step stepping controller are a standard tool for gait generation and stabilization that ports to humanoid platforms like the G1, and pairs naturally with tube-MPC / tracking-error-bound approaches you use.

## Abstract (from bib)
A Hybrid passive Linear Inverted Pendulum (H-LIP) model is proposed for characterizing, stabilizing and composing periodic orbits for 3D underactuated bipedal walking. Specifically, Period-l (P1) and Period -2 (P2) orbits are geometrically characterized in the state space of the H-LIP. Stepping controllers are designed for global stabilization of the orbits. Valid ranges of the gains and their optimality are derived. The optimal stepping controller is used to create and stabilize the walking of bipedal robots. An actuated Spring-loaded Inverted Pendulum (aSLIP) model and the underactuated robot Cassie are used for illustration. Both the aSLIP walking with PI or P2 orbits and the Cassie walking with all 3D compositions of the PI and P2 orbits can be smoothly generated and stabilized from a stepping-in-place motion. This approach provides a perspective and a methodology towards continuous gait generation and stabilization for 3D underactuated walking robots.

## Concepts
- [[reduced-order-model]]
- [[hierarchical-control]]

## Source
- bibkeys: `xiongOrbitCharacterizationStabilization2019`
- DOI: https://doi.org/10.1109/IROS40897.2019.8968162
- URL: https://ieeexplore.ieee.org/document/8968162
