---
type: paper
citekey: fallon2015continuous
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Fallon, Maurice F.
- Marion, Pat
- Deits, Robin
- Whelan, Thomas
- Antone, Matthew
- McDonald, John
- Tedrake, Russ
year: 2015
venue: 2015 IEEE-RAS 15th International Conference on Humanoid Robots (Humanoids)
doi: 10.1109/HUMANOIDS.2015.7363465
arxiv: null
url: https://doi.org/10.1109/HUMANOIDS.2015.7363465
zotero: null
summary: ai-draft
pdf: missing
status: to-read
mine: false
bibkeys:
- fallon_continuous_2015
---

# Continuous humanoid locomotion over uneven terrain using stereo fusion

> [!info] Fallon, Maurice F.; Marion, Pat; Deits, Robin; Whelan, Thomas; Antone, Matthew; McDonald, John · 2015 · 2015 IEEE-RAS 15th International Conference on Humanoid Robots (Humanoids)

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — A perception-and-planning pipeline that lets a humanoid walk continuously over rough terrain using only passive stereo vision, with quality matching LIDAR.
**Problem** — Reliable locomotion over rugged terrain typically relies on actuated laser range sensors and stop-and-scan operation; the goal is continuous, non-stop walking driven by passive vision.
**Method** — Continuously fuses stereo imagery into a consistent 3D terrain model, which feeds a footstep planner that reasons about obstacle avoidance, kinematic reachability, and foot rotation via mixed-integer quadratic optimization (the Deits-Tedrake formulation). Both computationally intensive systems are engineered for low latency (below 1 second) to enable re-planning while walking.
**Key results** — Stereo-fused terrain estimates match the quality of LIDAR; claimed as the first use of computer vision for general-purpose terrain estimation on a robot locomoting in continuous motion, with extensive quantitative analysis.

## Takeaways
- Passive stereo fusion can replace a laser range sensor for rough-terrain footstep planning — a hardware/perception simplification.
- Sub-second latency for both perception and MIQP planning is what enables re-planning without stopping.
- Directly couples the Deits-Tedrake mixed-integer footstep planner to a real-time vision front end.

## Relevance to your work
The perception-to-footstep-planning system for continuous rough-terrain humanoid walking, cited by [[@dai2025walk]] as the sensing/planning stack behind foothold-constrained locomotion.

## Abstract (from bib)
For humanoid robots to fulfill their mobility potential they must demonstrate reliable and efficient locomotion over rugged and irregular terrain. In this paper we present the perception and planning algorithms which have allowed a humanoid robot to use only passive stereo imagery (as opposed to actuating a laser range sensor) to safely plan footsteps to continuously walk over rough and uneven surfaces without stopping. The perception system continuously integrates stereo imagery to build a consistent 3D model of the terrain which is then used by our footstep planner which reasons about obstacle avoidance, kinematic reachability and foot rotation through mixed-integer quadratic optimization to plan the required step positions. We illustrate that our stereo imagery fusion approach can measu

## Concepts

## Source
- Cited by [[@dai2025walk]]
- bibkeys: `fallon_continuous_2015`
- DOI: https://doi.org/10.1109/HUMANOIDS.2015.7363465
