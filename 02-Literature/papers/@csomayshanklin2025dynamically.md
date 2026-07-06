---
type: paper
citekey: csomayshanklin2025dynamically
tags: [planning, control]
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Csomay-Shanklin, Noel
- Compton, William D.
- Ames, Aaron D.
year: 2025
venue: ICRA 2025
doi: null
arxiv: null
url: null
zotero: null
status: read
mine: true
summary: ai-draft
pdf: attachments/@csomayshanklin2025dynamically.pdf
---

# Dynamically Feasible Path Planning in Cluttered Environments via Reachable Bezier Polytopes

> [!info] Csomay-Shanklin, Noel; Compton, William D.; Ames, Aaron D. · 2025 · ICRA 2025 — **my paper**
> [!info]- otto authors: [[aaron-ames]] · [[noel-csomay-shanklin]]

## Abstract
The deployment of robotic systems in real world environments requires the ability to quickly produce paths through cluttered, non-convex spaces. These planned trajec- tories must be both kinematically feasible (i.e., collision free) and dynamically feasible (i.e., satisfy the underlying system dynamics), necessitating a consideration of both the free space and the dynamics of the robot in the path planning phase. In this work, we explore the application of reachable Bézier polytopes as an efficient tool for generating trajectories satisfy- ing both kinematic and dynamic requirements. Furthermore, we demonstrate that by offloading specific computation tasks to the GPU, such an algorithm can meet tight real time requirements. We propose a layered control architecture that efficiently produces collision free and dynamically feasible paths for nonlinear control systems, and demonstrate the framework on the tasks of 3D hopping in a cluttered environment.

## Summary
> [!note] AI-drafted from the abstract/intro — a base to refine or replace with your own framing.

**TL;DR** — Uses **reachable Bézier polytopes** to plan paths that are simultaneously kinematically (collision-free) and dynamically feasible, fast enough for real time via GPU offloading, inside a layered control architecture.
**Problem** — Real-world planning needs paths through cluttered non-convex space that also respect the robot's dynamics; top-down "assume the tracker handles dynamics" gives weak constraint-satisfaction guarantees.
**Method** — Represent reachable sets as Bézier polytopes (a kinodynamic planner); offload key computation to the GPU to hit tight real-time budgets; pair with a low-level tracker in a layered stack.
**Key results** — Demonstrated on **3D hopping in a cluttered environment**.

## Takeaways
- Baking dynamic feasibility into the *planner* (not just assuming it downstream) tightens guarantees.
- Bézier polytopes make reachability cheap enough for real-time replanning.

## Where it sits in my work
The planning layer of [[@hierarchies2025motion]]; complements the tracking-side safety of [[@compton2025dynamic|DTMPC]] for cluttered-environment navigation.

## Concepts
- [[hierarchical-control]] · [[reduced-order-model]] · _to add:_ kinodynamic-planning, reachable-set

## References (in otto)
- [[@ambrose2022creating]]
- [[@ames2019barrier]]
- [[@apgar2018fast]]
- [[@bency2019neural]]
- [[@code2024x]]
- [[@csomayshanklin2022multi]]
- [[@csomayshanklin2023nonlinear]]
- [[@csomayshanklin2024bezier]]
- [[@deits2015computing]]
- [[@deits2015efficient]]
- [[@donald1993kinodynamic]]
- [[@fernbach2017kinodynamic]]
- [[@fridovichkeil2018planning]]
- [[@ioan2021mixed]]
- [[@kamermans2020primer]]
- [[@kirillov2023segment]]
- [[@lavalle1998rapidly]]
- [[@lavalle2001randomized]]
- [[@lee2021efficient]]
- [[@marcucci2021shortest]]
- [[@marcucci2022motion]]
- [[@marcucci2023fast]]
- [[@matni2024quantitative]]
- [[@nilsson1969mobile]]
- [[@pfeiffer2017perception]]
- [[@qureshi2020motion]]
- [[@rawlings2017model]]
- [[@reeds1990optimal]]
- [[@schmerling2021kinodynamic]]
- [[@shkolnik2009reachability]]
- [[@sontag1995characterizations]]
- [[@stellato2020osqp]]
- [[@stoneman2014embedding]]
- [[@supplementalndvideo]]
- [[@wang2021survey]]
- [[@webb2013kinodynamic]]
- [[@wu2020r3t]]
