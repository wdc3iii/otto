---
type: paper
citekey: barasuol2015reactive
tags: [locomotion, control]
aliases: []
created: '2026-07-06'
modified: '2026-07-06'
authors:
- Barasuol, Victor
- Camurri, Marco
- Bazeille, Stephane
- Caldwell, Darwin G.
- Semini, Claudio
year: 2015
venue: '2015 IEEE/RSJ International Conference on Intelligent Robots and Systems (IROS)'
doi: 10.1109/IROS.2015.7354191
arxiv: null
url: https://ieeexplore.ieee.org/document/7354191
zotero: null
summary: ai-draft
pdf: attachments/@barasuol2015reactive.pdf
status: to-read
mine: false
bibkeys:
- barasuolReactiveTrottingFoot2015
---

# Reactive Trotting with Foot Placement Corrections through Visual Pattern Classification

> [!info] Victor Barasuol; Marco Camurri; Stephane Bazeille; Darwin G. Caldwell; Claudio Semini · 2015 · 2015 IEEE/RSJ International Conference on Intelligent Robots and Systems (IROS)

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — Couples a reactive trotting controller to an online RGB-D mapping system so the 80 kg HyQ quadruped corrects footholds in real time via visual pattern classification of local heightmaps.
**Problem** — Agile locomotion on rough terrain depends on perceiving the environment; frontal leg/shin collisions with obstacles degrade stability during trotting.
**Method** — An RGB-D sensor plus motion capture build a 3D map; while trotting, the controller requests a local heightmap around the next nominal foothold, applies visual pattern classification to pick an optimized foot placement, and modifies the leg endpoint trajectory — independently per leg.
**Key results** — Tested in simulation and on the 80 kg hydraulic HyQ robot; the visual reaction increases stability and reduces frontal leg/shin collisions on irregular terrain. (no numeric figures read)

## Takeaways
- Foothold correction is posed as pattern classification over local heightmaps rather than full optimization — a lightweight, per-leg reactive layer.
- Requests the heightmap "in advance" of the nominal touchdown, giving the controller lead time to adjust the swing trajectory.
- Early (2015) demonstration of perception-in-the-loop foothold adaptation on a large hydraulic quadruped.

## Relevance to your work
Classical, pre-deep-learning counterpart to your perceptive locomotion interests: reactive foothold correction from a local heightmap is the analog planning move that RL end-to-end policies (e.g. [[@agarwal2022legged]]) later absorbed — useful contrast for the planning/control layer on the G1.

## Abstract (from bib)
Agile robot locomotion on rough terrain is highly dependent on the ability to perceive the environment. In this paper, we show how the interaction between a reactive control framework and an online mapping system can significantly improve the trotting performance on irregular terrain. In particular, this new locomotion controller increases the stability of the robot and reduces frontal leg and shin collisions with obstacles by correcting in realtime the foothold locations. The mapping system uses an RGB-D sensor and a motion capture system to build a three dimensional map of the surroundings of the robot. While the robot is trotting, the control framework requests in advance a local heightmap around the next nominal foothold position. Then, an optimized foot placement location is estimated by applying visual pattern classification on the acquired heightmaps, and the leg endpoint trajectory is modified accordingly. The foothold correction is performed independently for each leg. To show the effectiveness of our approach the controller was tested both in simulation and experimentally with our 80 kg hydraulic quadruped robot, HyQ. The results show that visual based reaction through pattern classification is a promising approach to increase locomotion robustness over challenging terrain.

## Concepts
- [[traversability-estimation]]

## Source
- bibkeys: `barasuolReactiveTrottingFoot2015`
- DOI: https://doi.org/10.1109/IROS.2015.7354191
- URL: https://ieeexplore.ieee.org/document/7354191
