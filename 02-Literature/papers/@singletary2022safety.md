---
type: paper
citekey: singletary2022safety
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Singletary, Andrew
- Guffey, William
- Molnar, Tamas G
- Sinnet, Ryan
- Ames, Aaron D
year: 2022
venue: IEEE Robotics and Automation Letters
doi: 10.1109/LRA.2022.3192634
arxiv: 2205.01026
url: https://arxiv.org/abs/2205.01026
summary: ai-draft
pdf: attachments/@singletary2022safety.pdf
zotero: null
status: to-read
mine: false
bibkeys:
- singletary2022safety
---

# Safety-critical manipulation for collision-free food preparation

> [!info] Singletary, Andrew; Guffey, William; Molnar, Tamas G; Sinnet, Ryan; Ames, Aaron D · 2022 · IEEE Robotics and Automation Letters

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — A CBF-based framework that dynamically re-shapes pre-validated manipulator trajectories to stay collision-free in cluttered, changing environments, demonstrated on a full-scale robot cooking line.

**Problem** — High-throughput food preparation demands quick, robust, collision-free manipulator behaviors; re-planning from scratch when the environment changes is slow and brittle.

**Method** — Instead of re-planning, the method modifies previously generated (and validated) trajectories online using control barrier functions, which act as a safety filter that adapts the motion to detailed dynamic collision environments while retaining rigorous safety guarantees on the resulting trajectory.

**Key results** — Validated on a full-scale robotic manipulator in a real-world cooking environment, showing substantial improvements in computation time and robustness over full re-planning.

## Takeaways
- CBFs as a trajectory-modification layer (not just an instantaneous filter) let you reuse validated motion plans under environmental change.
- Trades global re-optimization for cheap, guaranteed local deformation — the practical selling point for real-time deployment.

## Relevance to your work
A concrete case of CBF safety filtering applied to real hardware under fast timing constraints, illustrating the online-modification pattern relevant to safety-critical control as pursued in [[@compton2025learning]].

## Concepts
[[control-barrier-function]]

## Source
- Cited by [[@compton2025learning]]
- bibkeys: `singletary2022safety`
