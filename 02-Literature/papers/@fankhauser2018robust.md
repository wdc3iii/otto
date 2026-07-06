---
type: paper
citekey: fankhauser2018robust
tags: [locomotion, planning]
aliases: []
created: '2026-07-06'
modified: '2026-07-06'
authors:
- Fankhauser, Peter
- Bjelonic, Marko
- Dario Bellicoso, C.
- Miki, Takahiro
- Hutter, Marco
year: 2018
venue: '2018 IEEE International Conference on Robotics and Automation (ICRA)'
doi: 10.1109/ICRA.2018.8460731
arxiv: null
url: https://ieeexplore.ieee.org/document/8460731
zotero: null
summary: ai-draft
pdf: attachments/@fankhauser2018robust.pdf
status: to-read
mine: false
bibkeys:
- fankhauserRobustRoughTerrainLocomotion2018
---

# Robust Rough-Terrain Locomotion with a Quadrupedal Robot

> [!info] Peter Fankhauser; Marko Bjelonic; C. Dario Bellicoso; Takahiro Miki; Marco Hutter · 2018 · 2018 IEEE International Conference on Robotics and Automation (ICRA)

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — A perceptive rough-terrain motion planner for quadrupeds that finds safe footholds and collision-free swing-leg motions from an onboard terrain map, re-planning every step, demonstrated fully onboard on ANYmal.
**Problem** — Robots in natural/urban/industrial settings must navigate challenging environments, requiring safe foothold selection and obstacle-clearing motions without prior scene knowledge.
**Method** — A motion planner that uses an acquired terrain map to select safe footholds plus collision-free swing-leg motions, with a novel pose-optimization approach enabling the robot to climb over significant obstacles; re-plans at every step to handle disturbances and dynamic environments.
**Key results** — Experimentally validated on ANYmal autonomously traversing steps, inclines, and stairs, with all mapping, state estimation, control, and planning done in real-time onboard and no prior scene knowledge (no numeric figures read).

## Takeaways
- Per-step re-planning couples foothold search with collision-free swing-leg motion over an onboard elevation map.
- A pose-optimization step lets the base reconfigure to clear significant obstacles — the key enabler for stairs/inclines.

## Relevance to your work
Classical perceptive foothold/pose planning over a terrain map is the model-based counterpart to your RL locomotion work; the real-time onboard mapping→planning→control loop is a reference architecture for terrain-aware navigation on legged hardware.

## Abstract (from bib)
Robots working in natural, urban, and industrial settings need to be able to navigate challenging environments. In this paper, we present a motion planner for the perceptive rough-terrain locomotion with quadrupedal robots. The planner finds safe footholds along with collision-free swing-leg motions by leveraging an acquired terrain map. To this end, we present a novel pose optimization approach that enables the robot to climb over significant obstacles. We experimentally validate our approach with the quadrupedal robot ANYmal by autonomously traversing obstacles such steps, inclines, and stairs. The locomotion planner re-plans the motion at every step to cope with disturbances and dynamic environments. The robot has no prior knowledge of the scene, and all mapping, state estimation, control, and planning is performed in real-time onboard the robot.

## Concepts
- [[traversability-estimation]]
- [[hierarchical-control]]

## Source
- bibkeys: `fankhauserRobustRoughTerrainLocomotion2018`
- DOI: https://doi.org/10.1109/ICRA.2018.8460731
- URL: https://ieeexplore.ieee.org/document/8460731
