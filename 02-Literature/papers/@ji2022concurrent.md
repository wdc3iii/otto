---
type: paper
citekey: ji2022concurrent
tags: [locomotion, rl, control]
aliases: []
created: '2026-07-06'
modified: 2026-07-29
authors:
- Ji, Gwanghyeon
- Mun, Juhyeok
- Kim, Hyeongjun
- Hwangbo, Jemin
year: 2022
venue: IEEE Robotics and Automation Letters
doi: 10.1109/LRA.2022.3151396
arxiv: '2202.05481'
url: http://arxiv.org/abs/2202.05481
zotero: null
summary: ai-draft
pdf: attachments/@ji2022concurrent.pdf
status: to-read
mine: false
bibkeys:
- jiConcurrentTrainingControl2022
---

# Concurrent Training of a Control Policy and a State Estimator for Dynamic and Robust Legged Locomotion

> [!info] Gwanghyeon Ji; Juhyeok Mun; Hyeongjun Kim; Jemin Hwangbo · 2022 · IEEE Robotics and Automation Letters

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — Jointly training an RL control policy alongside a learned state estimator (base velocity, foot height, contact probability) yields dynamic, robust legged locomotion transferable to hardware.
**Problem** — Robust dynamic legged locomotion needs good state information the robot cannot directly measure.
**Method** — A policy network outputs desired joint positions; a state-estimation network outputs estimates of base linear velocity, foot height, and contact probability. Both are trained concurrently in a fast simulator, then transferred to the real robot.
**Key results** — Traverses diverse terrains (hill, slippery plate, bumpy road); runs up to 3.75 m/s on flat ground and 3.54 m/s on a slippery plate with friction coefficient 0.22.

## Takeaways
- Co-training the estimator with the policy couples estimation to what the controller actually needs, rather than a fixed observer.
- Explicit learned outputs — base velocity, foot height, contact probability — are the states hardest to sense directly on legged robots.
- High measured speeds even under low friction (μ = 0.22) argue for robustness of the joint scheme.

## Relevance to your work
State estimation (base velocity, contacts) is a core bottleneck for RL locomotion transfer on the G1; the concurrent-training idea is a clean alternative to a separate estimator and relevant to your sim-to-real locomotion policies.

## Abstract (from bib)
In this paper, we propose a locomotion training framework where a control policy and a state estimator are trained concurrently. The framework consists of a policy network which outputs the desired joint positions and a state estimation network which outputs estimates of the robot's states such as the base linear velocity, foot height, and contact probability. We exploit a fast simulation environment to train the networks and the trained networks are transferred to the real robot. The trained policy and state estimator are capable of traversing diverse terrains such as a hill, slippery plate, and bumpy road. We also demonstrate that the learned policy can run at up to 3.75 m/s on normal flat ground and 3.54 m/s on a slippery plate with the coefficient of friction of 0.22.

## Concepts
- [[rl-for-legged-locomotion]]
- [[sim-to-real-transfer]]
- [[state-estimation]] — a co-headline contribution: a learned proprioceptive estimator (base velocity, foot height, contact probability) trained concurrently with the policy.
- [[privileged-information]] · [[auxiliary-task-learning]] — *added 2026-07-29.* Ref `[15]` of [[auxiliary-prediction-heads]]: the same concurrent-supervision pattern one layer down, and your evidence that the recipe is robust enough for hardware.

## Source
- bibkeys: `jiConcurrentTrainingControl2022`
- arXiv: http://arxiv.org/abs/2202.05481
- DOI: https://doi.org/10.1109/LRA.2022.3151396
- URL: http://arxiv.org/abs/2202.05481
