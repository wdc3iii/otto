---
type: paper
citekey: fankhauser2018probabilistic
tags: [navigation, method]
aliases: []
created: '2026-07-06'
modified: '2026-07-06'
authors:
- Fankhauser, Péter
- Bloesch, Michael
- Hutter, Marco
year: 2018
venue: IEEE Robotics and Automation Letters
doi: 10.1109/LRA.2018.2849506
arxiv: null
url: https://ieeexplore.ieee.org/document/8392399
zotero: null
summary: ai-draft
pdf: attachments/@fankhauser2018probabilistic.pdf
status: to-read
mine: false
bibkeys:
- fankhauserProbabilisticTerrainMapping2018
---

# Probabilistic Terrain Mapping for Mobile Robots With Uncertain Localization

> [!info] Péter Fankhauser; Michael Bloesch; Marco Hutter · 2018 · IEEE Robotics and Automation Letters

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — A proprioceptive, robot-centric elevation mapping method that produces a probabilistic terrain estimate with confidence bounds, avoiding reliance on external/absolute localization.
**Problem** — Rough-terrain autonomy needs accurate real-time mapping, but existing methods rely on absolute localization via external geometric/visual feature tracking, which has reliability issues.
**Method** — Terrain mapping using proprioceptive localization from kinematic and inertial measurements only; the method folds in state-estimation drift/uncertainty and a distance-sensor noise model to yield a grid-based elevation map with upper and lower confidence bounds.
**Key results** — Validated on simulated datasets and real-world experiments for real-time terrain mapping with legged robots, comparing reconstruction to ground-truth reference maps (no numeric figures read).

## Takeaways
- Robot-centric elevation mapping that propagates localization drift and sensor noise into per-cell confidence bounds rather than a single point estimate.
- Uses proprioception (kinematics + IMU) only — sidesteps the fragility of external absolute localization.

## Relevance to your work
This is the foundational elevation-mapping substrate for perceptive/terrain-aware locomotion; the probabilistic map + confidence bounds are exactly the kind of uncertainty representation that feeds capability-aware navigation and foothold planning on the G1.

## Abstract (from bib)
Mobile robots build on accurate, real-time mapping with onboard range sensors to achieve autonomous navigation over rough terrain. Existing approaches often rely on absolute localization based on tracking of external geometric or visual features. To circumvent the reliability issues of these approaches, we propose a novel terrain mapping method, which bases on proprioceptive localization from kinematic and inertial measurements only. The proposed method incorporates the drift and uncertainties of the state estimation and a noise model of the distance sensor. It yields a probabilistic terrain estimate as a grid-based elevation map including upper and lower confidence bounds. We demonstrate the effectiveness of our approach with simulated datasets and real-world experiments for real-time terrain mapping with legged robots and compare the terrain reconstruction to ground truth reference maps.

## Concepts
- [[traversability-estimation]]

## Source
- bibkeys: `fankhauserProbabilisticTerrainMapping2018`
- DOI: https://doi.org/10.1109/LRA.2018.2849506
- URL: https://ieeexplore.ieee.org/document/8392399
