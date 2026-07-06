---
type: paper
citekey: beyer2024risk
tags: [navigation, planning]
aliases: []
created: '2026-07-06'
modified: '2026-07-06'
authors:
- Beyer, Lukas Lao
- Ryou, Gilhyun
- Spieler, Patrick
- Karaman, Sertac
year: 2024
venue: '2024 IEEE International Conference on Robotics and Automation (ICRA)'
doi: 10.1109/ICRA57147.2024.10611509
arxiv: null
url: https://ieeexplore.ieee.org/document/10611509
zotero: null
summary: ai-draft
pdf: attachments/@beyer2024risk.pdf
status: to-read
mine: false
bibkeys:
- beyerRiskPredictivePlanningOffRoad2024
---

# Risk-Predictive Planning for Off-Road Autonomy

> [!info] Lukas Lao Beyer; Gilhyun Ryou; Patrick Spieler; Sertac Karaman · 2024 · 2024 IEEE International Conference on Robotics and Automation (ICRA)

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — Plans off-road trajectories by learning to predict how future riskmaps evolve given a candidate path and speed profile, producing time-optimal trajectories under a bound on future expected risk.
**Problem** — Unstructured off-road environments give limited planning information: no high-fidelity maps, occlusions from terrain/obstacles, and perception that degrades at high speed due to resolution and latency limits.
**Method** — A model learns to predict the evolution of future riskmaps conditioned on the vehicle's future path and speed profile, trained self-supervised from recorded trajectories. A planning algorithm efficiently queries the model along candidate paths/speeds to generate time-optimal trajectories while bounding future expected risk.
**Key results** — Risk model validated against real vehicle driving logs; closed-loop simulations on benchmark scenarios show qualitatively distinct planner behavior with improvements in success rate and speed by up to 60%.

## Takeaways
- Anticipatory planning: predict the risk you will observe under a chosen path+speed, rather than reacting to the current riskmap.
- Self-supervised training from driving logs sidesteps hand-labeled risk annotations.
- Keeps a formal bound on expected future risk while optimizing for time — an explicit speed/safety trade-off knob.

## Relevance to your work
Adjacent to your capability-aware navigation line but on a wheeled off-road platform: the idea of conditioning a predicted risk/traversability field on the intended path and speed profile maps onto capability-aware planning for the G1, where achievable speed depends on terrain.

## Abstract (from bib)
Efficiently navigating off-road environments presents a number of challenges arising from their unstructured nature. In the absence of high-fidelity maps, occlusions from obstacles and terrain lead to limited information available to inform planning decisions. Furthermore, resolution and latency limitations of real-world perception systems lead to potentially of degraded perception performance when traversing such environments at high speeds. We address these problems by proposing an algorithm which plans trajectories while anticipating future observations. In particular, we introduce a model which learns to predict the evolution of future riskmaps conditioned on the future path and speed profile of the vehicle. The model is trained in a self-supervised fashion using recordings of vehicle trajectories. We then present an algorithm which leverages a way to efficiently query the model along candidate paths and speed profiles to produce time-optimal trajectories while maintaining a bound on the future expected risk. We assess the predictive performance of our risk model through a comparison with real vehicle driving logs. Furthermore, our closed-loop simulations of several benchmark scenarios demonstrate how the behavior of our planner leads to qualitatively distinct trajectories, leading to improvements in both success rate and speed by up to 60\%.

## Concepts
- [[forward-dynamics-model]]
- [[traversability-estimation]]

## Source
- bibkeys: `beyerRiskPredictivePlanningOffRoad2024`
- DOI: https://doi.org/10.1109/ICRA57147.2024.10611509
- URL: https://ieeexplore.ieee.org/document/10611509
