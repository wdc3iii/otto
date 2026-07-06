---
type: paper
citekey: lee2023terrain
tags: [navigation, control, planning]
aliases: []
created: '2026-07-06'
modified: '2026-07-06'
authors:
- Lee, Hojin
- Kim, Taekyung
- Mun, Jungwi
- Lee, Wonsuk
year: 2023
venue: IEEE Robotics and Automation Letters
doi: 10.1109/LRA.2023.3318190
arxiv: '2305.00676'
url: http://arxiv.org/abs/2305.00676
zotero: null
summary: ai-draft
pdf: attachments/@lee2023terrain.pdf
status: to-read
mine: false
bibkeys:
- leeLearningTerrainAwareKinodynamic2023
---

# Learning Terrain-Aware Kinodynamic Model for Autonomous Off-Road Rally Driving With Model Predictive Path Integral Control

> [!info] Hojin Lee; Taekyung Kim; Jungwi Mun; Wonsuk Lee · 2023 · IEEE Robotics and Automation Letters

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — A learned terrain-aware kinodynamic model conditioned on proprioceptive + exteroceptive data predicts 6-DoF motion and contact interactions, driving an MPPI controller for robust high-speed off-road rally driving.
**Problem** — High-speed off-road driving requires proactively predicting motion and adjusting control in response to environmental changes (e.g. terrain elevation), given complex vehicle-terrain interactions.
**Method** — Learn a terrain-aware kinodynamic model conditioned on both proprioceptive and exteroceptive information; it predicts 6-DoF motion and estimates contact interactions without ground-truth force data during training. Design an MPC (model predictive path integral, MPPI) with a cost that penalizes sampled trajectories with unstable motion, unsafe interactions, and high model-derived uncertainty.
**Key results** — On a simulated off-road track, the model-controller pair outperforms the baseline and delivers robust high-speed driving without control failure (no numeric figures read).

## Takeaways
- Fuses proprioception + exteroception to condition a kinodynamic model on terrain, and recovers contact interactions without force ground truth.
- Uncertainty from the learned model is baked into the MPPI cost, penalizing high-uncertainty trajectories — an uncertainty-aware sampling-MPC design.
- Sampling-based MPPI handles the nonlinear learned model where gradient-based MPC would struggle.

## Relevance to your work
Terrain-aware learned dynamics feeding sampling-based MPC is methodologically adjacent to your tube-MPC and perceptive-locomotion interests; the uncertainty-penalizing cost is a practical alternative to explicit tracking-error bounds. Wheeled off-road rather than legged, so the platform is tangential but the model+MPC pattern transfers.

## Abstract (from bib)
High-speed autonomous driving in off-road environments has immense potential for various applications, but it also presents challenges due to the complexity of vehicle-terrain interactions. In such environments, it is crucial for the vehicle to predict its motion and adjust its controls proactively in response to environmental changes, such as variations in terrain elevation. To this end, we propose a method for learning terrain-aware kinodynamic model which is conditioned on both proprioceptive and exteroceptive information. The proposed model generates reliable predictions of 6-degree-of-freedom motion and can even estimate contact interactions without requiring ground truth force data during training. This enables the design of a safe and robust model predictive controller through appropriate cost function design which penalizes sampled trajectories with unstable motion, unsafe interactions, and high levels of uncertainty derived from the model. We demonstrate the effectiveness of our approach through experiments on a simulated off-road track, showing that our proposed model-controller pair outperforms the baseline and ensures robust high-speed driving performance without control failure.

## Concepts
- [[traversability-estimation]]

## Source
- bibkeys: `leeLearningTerrainAwareKinodynamic2023`
- arXiv: http://arxiv.org/abs/2305.00676
- DOI: https://doi.org/10.1109/LRA.2023.3318190
- URL: http://arxiv.org/abs/2305.00676
