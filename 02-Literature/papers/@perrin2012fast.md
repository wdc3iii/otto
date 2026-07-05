---
type: paper
citekey: perrin2012fast
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Perrin, Nicolas
- Stasse, Olivier
- Baudouin, Léo
- Lamiraux, Florent
- Yoshida, Eiichi
year: 2012
venue: IEEE Transactions on Robotics
doi: 10.1109/TRO.2011.2172152
arxiv: null
url: https://doi.org/10.1109/TRO.2011.2172152
summary: ai-draft
pdf: missing
zotero: null
status: to-read
mine: false
bibkeys:
- perrin_fast_2012
---

# Fast Humanoid Robot Collision-Free Footstep Planning Using Swept Volume Approximations

> [!info] Perrin, Nicolas; Stasse, Olivier; Baudouin, Léo; Lamiraux, Florent; Yoshida, Eiichi · 2012 · IEEE Transactions on Robotics

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — A fast footstep-planning framework for humanoids on flat ground with 3-D obstacle avoidance, using offline-precomputed swept-volume approximations to slash online collision-checking cost.
**Problem** — Online collision checking dominates the cost of footstep planning for legged robots amid 3-D obstacles, making fast planning hard.
**Method** — Swept volumes of half-steps are approximated offline to cut online collision-checking time; an RRT variant then searches for collision-free sequences of half-steps (produced by a specific walking pattern generator), and an original homotopy smooths these sequences into natural, obstacle-avoiding motions.
**Key results** — Experimentally validated on the HRP-2 humanoid, producing fast, collision-free, natural walking motions among 3-D obstacles.

## Takeaways
- Offline swept-volume precomputation is the key trick: it moves the expensive geometry work out of the online loop, enabling fast sampling-based footstep search.
- Half-step primitives plus a homotopy smoothing stage bridge discrete planning and continuous natural motion.
- Assumes flat ground; obstacle avoidance is 3-D but terrain is not — a classical planning-layer contribution rather than dynamic locomotion.

## Abstract (from bib)
In this paper, we propose a novel and coherent framework for fast footstep planning for legged robots on a flat ground with 3-D obstacle avoidance. We use swept volume approximations that are computed offline in order to considerably reduce the time spent in collision checking during the online planning phase, in which a rapidly exploring random tree variant is used to find collision-free sequences of half-steps (which are produced by a specific walking pattern generator). Then, an original homotopy is used to smooth the sequences into natural motions, gently avoiding the obstacles. The results are experimentally validated on the robot HRP-2.

## Relevance to your work
A classical footstep-planning-layer reference (swept volumes + RRT) cited as prior art for collision-free humanoid navigation, relevant to the planning layer above dynamic locomotion as in [[@dai2025walk]].

## Concepts


## Source
- Cited by [[@dai2025walk]]
- bibkeys: `perrin_fast_2012`
- DOI: https://doi.org/10.1109/TRO.2011.2172152
