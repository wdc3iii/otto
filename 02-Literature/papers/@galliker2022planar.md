---
type: paper
citekey: galliker2022planar
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Galliker, Manuel Y
- Csomay-Shanklin, Noel
- Grandia, Ruben
- Taylor, Andrew J
- Farshidian, Farbod
- Hutter, Marco
- Ames, Aaron D
year: 2022
venue: 2022 IEEE-RAS 21st International Conference on Humanoid Robots (Humanoids)
doi: null
arxiv: '2203.07429'
url: https://arxiv.org/abs/2203.07429
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@galliker2022planar.pdf
bibkeys:
- galliker_bipedal_2022
---

# Planar bipedal locomotion with nonlinear model predictive control: Online gait generation using whole-body dynamics

> [!info] Galliker, Manuel Y; Csomay-Shanklin, Noel; Grandia, Ruben; Taylor, Andrew J; Farshidian, Farbod; Hutter, Marco · 2022 · 2022 IEEE-RAS 21st International Conference on Humanoid Robots (Humanoids)
> [!info]- otto authors: [[aaron-ames]] · [[marco-hutter]] · [[noel-csomay-shanklin]]

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.

**TL;DR** — An online nonlinear MPC scheme that uses the *full-order* rigid-body dynamics to generate diverse planar bipedal walking in real time, optionally warm-started by an offline-synthesized gait.

**Problem** — The high dimensionality of bipedal robots has largely restricted full-order rigid-body dynamics to gaits synthesized offline and then tracked online; generating dynamic, input-constrained, underactuated walking online remained hard.

**Method** — Develops an online NMPC that optimizes over the full-order dynamics to realize varied walking behaviors. It can additionally be coupled with an offline gait supplied as a reference, which shortens the prediction horizon and enables rapid online re-planning — bridging online reactive control and offline gait planning.

**Key results** — Demonstrated on the planar robot AMBER-3M, in simulation and on hardware, both with and without an offline gait reference.

## Takeaways
- Pushes full-order dynamics into the online loop rather than tracking a fixed offline gait, enabling reactive behavior variety.
- Optional offline-gait reference is the pragmatic lever: it shortens the horizon (cheaper NMPC) while retaining online re-planning, blending the two paradigms.
- Demonstrated on a planar (2D) platform, so the 3D/underactuation and real-time-scaling questions remain open.

## Relevance to your work
A concrete point on the offline-gait-vs-online-MPC spectrum for legged locomotion, from the Ames/Csomay-Shanklin line — context for how the layered planning-and-control decomposition in [[@hierarchies2025motion]] trades horizon length against online reactivity.

## Concepts
[[hierarchical-control]]

## Source
- Cited by [[@hierarchies2025motion]]
- bibkeys: `galliker_bipedal_2022`
