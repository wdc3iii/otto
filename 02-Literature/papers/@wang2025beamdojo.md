---
type: paper
citekey: wang2025beamdojo
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Wang, Huayi
- Wang, Zirui
- Ren, Junli
- Ben, Qingwei
- Huang, Tao
- Zhang, Weinan
- Pang, Jiangmiao
year: 2025
venue: 'Proceedings of Robotics: Science and Systems'
doi: 10.15607/RSS.2025.XXI.068
arxiv: '2502.10363'
url: https://arxiv.org/abs/2502.10363
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@wang2025beamdojo.pdf
bibkeys:
- wang_beamdojo_2025
---

# BeamDojo: Learning Agile Humanoid Locomotion on Sparse Footholds

> [!info] Wang, Huayi; Wang, Zirui; Ren, Junli; Ben, Qingwei; Huang, Tao; Zhang, Weinan · 2025 · Proceedings of Robotics: Science and Systems

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — BeamDojo is an RL framework for agile humanoid locomotion on sparse footholds (beams, stepping stones), combining a sampling-based foothold reward for polygonal feet, a double critic, and a two-stage training scheme, with real-world LiDAR deployment.
**Problem** — Risky terrain with sparse footholds demands precise foot placement and stability, but learning-based methods struggle due to sparse foothold rewards and inefficient exploration.
**Method** — Introduces a sampling-based foothold reward tailored to polygonal feet and a double critic that balances dense locomotion rewards against sparse foothold rewards. A two-stage RL curriculum first relaxes terrain dynamics (training on flat ground with task-terrain perceptive observations) then fine-tunes on the real task terrain; an onboard LiDAR-based elevation map enables real-world deployment.
**Key results** — Extensive sim and real-world experiments show efficient learning and agile locomotion with precise foot placement on sparse footholds, maintaining a high success rate even under significant external disturbances.

## Takeaways
- Double critic decouples the reward scales (dense locomotion vs. sparse foothold), a clean fix for the sparse-reward pathology.
- Two-stage "relax dynamics on flat terrain, then fine-tune on real terrain" is the key exploration trick.
- Onboard LiDAR elevation map closes the perception loop for real hardware, not just sim.

## Abstract (from bib)
Traversing risky terrains with sparse footholds poses a significant challenge for humanoid robots, requiring precise foot placements and stable locomotion. Existing learning-based approaches often struggle on such complex terrains due to sparse foothold rewards and inefficient learning processes. To address these challenges, we introduce BeamDojo, a reinforcement learning (RL) framework designed for enabling agile humanoid locomotion on sparse footholds. BeamDojo begins by introducing a sampling-based foothold reward tailored for polygonal feet, along with a double critic to balancing the learning process between dense locomotion rewards and sparse foothold rewards. To encourage sufficient trial-and-error exploration, BeamDojo incorporates a two-stage RL approach: the first stage relaxes t

## Relevance to your work
A state-of-the-art learned approach to foothold-constrained humanoid locomotion, directly comparable to the foothold-aware method in [[@dai2025walk]]; the sparse-foothold reward design and sim-to-real perception pipeline are the RL counterpoint to model-based footstep planning.

## Concepts
<!-- [[03-Concepts]] links added when read -->

## Source
- Cited by [[@dai2025walk]]
- bibkeys: `wang_beamdojo_2025`
- DOI: https://doi.org/10.15607/RSS.2025.XXI.068
