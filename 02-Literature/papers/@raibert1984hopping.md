---
type: paper
citekey: raibert1984hopping
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Raibert, Marc H
year: 1984
venue: IEEE Transactions on Systems, Man, and Cybernetics
doi: 10.1109/TSMC.1984.6313238
arxiv: null
url: https://doi.org/10.1109/TSMC.1984.6313238
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: missing
bibkeys:
- raibert1984hopping
---

# Hopping in legged systems—modeling and simulation for the two-dimensional one-legged case

> [!info] Raibert, Marc H · 1984 · IEEE Transactions on Systems, Man, and Cybernetics

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — Models and simulates a planar one-legged hopper and shows that its running control decomposes cleanly into three near-independent parts: hopping height, forward velocity, and body attitude.
**Problem** — To understand balance, dynamic stability, and resonant oscillation in legged systems that hop and run, using the simplest nontrivial case.
**Method** — A 2D model — springy leg with nonzero mass, a body, and an actuated hinge-type hip — is simulated. Control is decomposed into three parts: total-system-energy estimates regulate hopping height (initiate hopping, maintain a level, change height, terminate); forward velocity is controlled via foot placement/balance; and body attitude is controlled during stance. Three algorithms are explored.
**Key results** — Simulations verify the feasibility of decomposing running control into these three parts, establishing the height/velocity/attitude decomposition as a workable control architecture.

## Takeaways
- The enduring contribution is the three-part decomposition (hop energy, foot-placement for speed, hip torque for attitude) — the conceptual root of essentially all subsequent hopping/running controllers.
- Energy-based regulation of hop height and foot-placement for balance are treated as separable channels, a template-level abstraction of legged dynamics.
- A simulation study of an idealized planar monoped, not a physical-robot or full-3D result.

## Relevance to your work
Foundational precedent for reduced-order / template models of legged locomotion: Raibert's decomposition is the intellectual ancestor of the structured, low-dimensional gait generators underlying modern hierarchies such as [[@compton2024constructive]].

## Concepts
[[reduced-order-model]]

## Source
- Cited by [[@compton2024constructive]]
- bibkeys: `raibert1984hopping`
