---
type: paper
citekey: jenelten2024dtc
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-06'
authors:
- Jenelten, Fabian
- He, Junzhe
- Farshidian, Farbod
- Hutter, Marco
year: 2024
venue: Science Robotics
doi: 10.1126/scirobotics.adh5401
arxiv: 2309.15462
url: https://arxiv.org/abs/2309.15462
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@jenelten2024dtc.pdf
bibkeys:
- jenelten2024dtc
- jenelten_dtc_2024
- jeneltenDTCDeepTracking2024
---

# Dtc: Deep tracking control

> [!info] Jenelten, Fabian; He, Junzhe; Farshidian, Farbod; Hutter, Marco · 2024 · Science Robotics
> [!info]- otto authors: [[marco-hutter]]

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — Deep Tracking Control (DTC) is a hybrid locomotion architecture in which an online model-based trajectory optimizer plans the motion and a reinforcement-learning policy is trained to *track* that plan, marrying the optimizer's accuracy and generalization with RL's real-world robustness.
**Problem** — Trajectory optimization with inverse dynamics gives accurate, interpretable, generalizable plans but breaks under model mismatch and violated assumptions (slippery/deformable ground); pure RL is robust but lacks the optimizer's precise, insightful planning.
**Method** — A model-based planner produces reference trajectories/contacts online; instead of tracking them with inverse dynamics, a learned policy (trained in simulation) tracks the optimized motion, so the RL layer compensates for model mismatch while the optimizer supplies foresight and task generality.
**Key results** — Reports superior robustness on slippery and deformable ground versus baselines, retaining accurate foothold planning across terrains (Science Robotics, 2024; quadruped hardware).

## Takeaways
- The core move is replacing inverse-dynamics tracking with a learned tracking policy — the optimizer keeps its role, RL absorbs the sim-to-real / model-mismatch gap.
- Positioned explicitly as unifying model-based planning and RL rather than choosing one; a canonical reference for "planner + learned tracker" designs.
- Robustness gains are concentrated where model assumptions fail (slip, deformable terrain), which is exactly where pure optimization degrades.

## Relevance to your work
DTC is the reference architecture for hybrid model-based-planner + learned-tracker locomotion — the exact design pattern behind reference-guided RL walking like [[@dai2025walk]], and a benchmark for how a learned policy can track an optimized plan while absorbing model mismatch.

## Reading notes (imported from prior literature vault)
> [!quote] Your own notes from reading the paper — authoritative, not AI-drafted.
- TrajOpt generates a foothold sequence (low rate), tracked by RL; the TrajOpt must run in-the-loop during training.
- Policy observes only footholds, joint positions, and contact schedule — no dynamics information, no base reference. Found this more robust; including more information led to the same pitfalls as model-based control.
- Training took 2 weeks (generated >23 years of optimized trajectories).
- Samples the heightmap **only along the line** connecting the current foot position to the desired foothold — removes learning dependency on other terrain-map regions that are more prone to perception error (drift, occlusion).
- Consistency: RL hesitancy over challenging terrain (a subset of agents earn higher reward by refusing to act) is reduced by rewarding actions consistent with previous ones, measured via similarity of adjacent motion optimizations.
- RL on GPU, optimization problems solved on CPU.
- Adds Laplace-distributed noise plus per-foot height offsets to encourage reliance on perceptive information.
- LiDAR gave improved outdoor performance and more robustness to lighting conditions than the RealSense D435 depth camera.
- **My take:** the depth-camera-vs-LiDAR reports are interesting, as is the selective heightmap (vs a large general one) — suggests dependency on the heightmap is complex.

## Concepts
[[hierarchical-control]]

## Source
- Cited by [[@dai2025walk]], [[@terrain2026consistent]]
- bibkeys: `jenelten2024dtc`, `jenelten_dtc_2024`
