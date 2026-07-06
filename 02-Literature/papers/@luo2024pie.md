---
type: paper
citekey: luo2024pie
tags: [locomotion, rl]
aliases: []
created: '2026-07-06'
modified: '2026-07-06'
authors:
- Luo, Shixin
- Li, Songbo
- Yu, Ruiqi
- Wang, Zhicheng
- Wu, Jun
- Zhu, Qiuguo
year: 2024
venue: arXiv
doi: 10.48550/arXiv.2408.13740
arxiv: '2408.13740'
url: http://arxiv.org/abs/2408.13740
zotero: null
summary: ai-draft
pdf: attachments/@luo2024pie.pdf
status: to-read
mine: false
bibkeys:
- luoPIEParkourImplicitExplicit2024
---

# PIE: Parkour with Implicit-Explicit Learning Framework for Legged Robots

> [!info] Shixin Luo; Songbo Li; Ruiqi Yu; Zhicheng Wang; Jun Wu; Qiuguo Zhu · 2024 · arXiv

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — A one-stage end-to-end parkour framework that uses dual-level implicit-explicit state/terrain estimation, letting a low-cost quadruped with an unreliable depth camera do agile parkour zero-shot from sim.
**Problem** — Legged parkour needs to understand both robot state and surrounding terrain despite unreliable perception and actuation; prior SOTA either leans on complex pre-trained terrain-reconstruction modules or caps parkour aggressiveness to avoid perception-driven failures.
**Method** — Parkour with Implicit-Explicit learning (PIE): a one-stage, end-to-end learning framework with dual-level implicit-explicit estimation, trained entirely in simulation with a relatively simple training process and reward function, using egocentric depth.
**Key results** — Real-world validation shows successful zero-shot deployment on harsh terrains with a low-cost quadruped, reported as superior parkour performance (no numeric figures read).

## Takeaways
- Combines implicit (latent) and explicit estimation at two levels, sidestepping a separate pre-trained terrain-reconstruction stage.
- Emphasizes robustness to unreliable egocentric depth and low-cost hardware.
- Deliberately simple reward/training pipeline yet zero-shot sim-to-real on challenging parkour terrain.

## Relevance to your work
Directly relevant to your RL-locomotion line: an end-to-end perceptive locomotion policy that tolerates noisy egocentric depth and transfers zero-shot, informing perceptive/terrain-aware locomotion and sim-to-real practice on legged systems (quadruped here, but the implicit-explicit estimation pattern is portable to humanoid work).

## Abstract (from bib)
Parkour presents a highly challenging task for legged robots, requiring them to traverse various terrains with agile and smooth locomotion. This necessitates comprehensive understanding of both the robot's own state and the surrounding terrain, despite the inherent unreliability of robot perception and actuation. Current state-of-the-art methods either rely on complex pre-trained high-level terrain reconstruction modules or limit the maximum potential of robot parkour to avoid failure due to inaccurate perception. In this paper, we propose a one-stage end-to-end learning-based parkour framework: Parkour with Implicit-Explicit learning framework for legged robots (PIE) that leverages dual-level implicit-explicit estimation. With this mechanism, even a low-cost quadruped robot equipped with an unreliable egocentric depth camera can achieve exceptional performance on challenging parkour terrains using a relatively simple training process and reward function. While the training process is conducted entirely in simulation, our real-world validation demonstrates successful zero-shot deployment of our framework, showcasing superior parkour performance on harsh terrains.

## Concepts
- [[rl-for-legged-locomotion]]
- [[sim-to-real-transfer]]

## Source
- bibkeys: `luoPIEParkourImplicitExplicit2024`
- arXiv: http://arxiv.org/abs/2408.13740
- DOI: https://doi.org/10.48550/arXiv.2408.13740
- URL: http://arxiv.org/abs/2408.13740
