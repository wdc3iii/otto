---
type: paper
citekey: chen2021fastrack
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Mo Chen
- Sylvia L. Herbert
- Haimin Hu
- Ye Pu
- Jaime Fernandez Fisac
- Somil Bansal
- Soojean Han
- Claire J. Tomlin
year: 2021
venue: IEEE Transactions on Automatic Control
doi: 10.1109/TAC.2021.3059838
arxiv: 2102.07039
url: https://arxiv.org/abs/2102.07039
zotero: null
summary: ai-draft
pdf: attachments/@chen2021fastrack.pdf
status: to-read
mine: false
bibkeys:
- Chen2021
- TomlinTAC21
- chen2021fastrack
---

# FaSTrack:A Modular Framework for Real-Time Motion Planning and Guaranteed Safe Tracking

> [!info] Mo Chen; Sylvia L. Herbert; Haimin Hu; Ye Pu; Jaime Fernandez Fisac; Somil Bansal · 2021 · IEEE Transactions on Automatic Control

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — FaSTrack lets any fast planner use a simplified planning model while a precomputed tracking error bound (TEB) and matching tracking controller guarantee the full-order system stays within a safe tube around the plan.
**Problem** — Real-time navigation planners are fast but give few safety guarantees, while provably safe planners are too expensive to replan online; the paper wants both at once.
**Method** — Decompose into a low-dimensional planning model (used online by any planner) and a higher-dimensional tracking model of the real system. Offline, solve a pursuit-evasion game between the two — here via Hamilton-Jacobi reachability — to obtain a worst-case TEB capturing model mismatch plus external disturbances, and the tracking controller that keeps error inside it. Online, the planner treats the TEB as an obstacle-inflation margin.
**Key results** — Demonstrated with three different real-time planners across three tracking-planning model pairs; the TEB precomputation needs no prior knowledge of the environment.

## Takeaways
- The safety guarantee is modular: swap in any online planner and the offline TEB still certifies the closed loop.
- The core object is a robust tracking-error tube computed once offline, decoupling planning speed from safety.
- Practicality hinges on HJ reachability, which scales poorly with tracking-model dimension — the classic bottleneck for high-DOF systems.

## Abstract (from bib)
Real-time, guaranteed safe trajectory planning is vital for navigation in unknown environments. However, real-time navigation algorithms typically sacrifice robustness for computation speed. Alternatively, provably safe trajectory planning tends to be too computationally intensive for real-time replanning. We propose FaSTrack, Fast and Safe Tracking, a framework that achieves both real-time replanning and guaranteed safety. In this framework, real-time computation is achieved by allowing any trajectory planner to use a simplified planning model of the system. The plan is tracked by the system, represented by a more realistic, higher dimensional tracking model. We precompute the tracking error bound (TEB) due to mismatch between the two models and due to external disturbances. We also obtai

## Relevance to your work
FaSTrack is the canonical planning-model/tracking-model split with a precomputed error bound — direct intellectual ancestor of [[@compton2025dynamic]]'s dynamic tubes, which relax the fixed FaSTrack TEB toward a state-dependent, learned tube.

## Concepts
[[reduced-order-model]] [[tracking-error-bound]] [[hierarchical-control]]

## Source
- Cited by [[@cohen2025safety]], [[@compton2025dynamic]], [[@compton2025learning]]
- bibkeys: `Chen2021`, `TomlinTAC21`, `chen2021fastrack`
- DOI: https://doi.org/10.1109/TAC.2021.3059838
