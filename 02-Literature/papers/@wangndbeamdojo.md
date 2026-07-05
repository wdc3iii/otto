---
type: paper
citekey: wangndbeamdojo
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
year: null
venue: null
doi: 10.48550/arXiv.2502.10363
arxiv: '2502.10363'
url: http://arxiv.org/abs/2502.10363
zotero: null
summary: ai-draft
pdf: attachments/@wangndbeamdojo.pdf
status: to-read
mine: false
bibkeys:
- wangBeamDojoLearningAgile2025
---

# BeamDojo: Learning Agile Humanoid Locomotion on Sparse Footholds

> [!info] Wang, Huayi; Wang, Zirui; Ren, Junli; Ben, Qingwei; Huang, Tao; Zhang, Weinan · n.d. · —

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — BeamDojo is an RL framework that teaches humanoids agile locomotion over sparse footholds (beams, stepping stones) with precise foot placement.
**Problem** — Sparse-foothold terrain demands precise foot placement, but sparse foothold rewards and inefficient exploration make learning-based approaches struggle on such terrain.
**Method** — Introduces a sampling-based foothold reward tailored for polygonal feet plus a double critic to balance dense locomotion rewards against sparse foothold rewards; uses a two-stage RL scheme (first stage on flat ground with terrain-aware observations, then refinement on the real challenging terrain) and an onboard LiDAR-based elevation map for real-world deployment.
**Key results** — Achieves efficient learning in simulation and agile real-world locomotion with precise foot placement on sparse footholds, maintaining a high success rate even under significant external disturbances (no numeric figures read).

## Takeaways
- The polygonal-foot sampling-based foothold reward is the core trick for making sparse-contact rewards learnable.
- Double-critic separates dense (locomotion) and sparse (foothold) reward signals — a recurring pattern for multi-objective locomotion RL.
- Two-stage curriculum (flat-with-terrain-observations → real terrain) plus onboard elevation mapping is what bridges sim training to deployment.

## Relevance to your work
A learning-based counterpart to model-based foothold-constrained locomotion; cited by [[@terrain2026consistent]] as prior art on perceptive humanoid locomotion over sparse footholds requiring consistent terrain estimation.

## Abstract (from bib)
Traversing risky terrains with sparse footholds poses a significant challenge for humanoid robots, requiring precise foot placements and stable locomotion. Existing learning-based approaches often struggle on such complex terrains due to sparse foothold rewards and inefficient learning processes. To address these challenges, we introduce BeamDojo, a reinforcement learning (RL) framework designed for enabling agile humanoid locomotion on sparse footholds. BeamDojo begins by introducing a sampling-based foothold reward tailored for polygonal feet, along with a double critic to balancing the learning process between dense locomotion rewards and sparse foothold rewards. To encourage sufficient trial-and-error exploration, BeamDojo incorporates a two-stage RL approach: the first stage relaxes t

## Concepts
<!-- [[03-Concepts]] links added when read -->

## Source
- Cited by [[@terrain2026consistent]]
- bibkeys: `wangBeamDojoLearningAgile2025`
- arXiv: https://arxiv.org/abs/2502.10363
- DOI: https://doi.org/10.48550/arXiv.2502.10363
- URL: http://arxiv.org/abs/2502.10363
