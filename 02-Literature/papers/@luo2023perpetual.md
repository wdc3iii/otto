---
type: paper
citekey: luo2023perpetual
tags: [rl, imitation]
aliases: []
created: '2026-07-26'
modified: '2026-07-26'
authors:
- Luo, Zhengyi
- Cao, Jinkun
- Winkler, Alexander
- Kitani, Kris
- Xu, Weipeng
year: 2023
venue: ICCV
doi: 10.48550/arXiv.2305.06456
arxiv: '2305.06456'
url: https://arxiv.org/abs/2305.06456
zotero: null
status: to-read
mine: false
pdf: attachments/@luo2023perpetual.pdf
---

# Perpetual Humanoid Control for Real-time Simulated Avatars

> [!info] Luo, Zhengyi; Cao, Jinkun; Winkler, Alexander; Kitani, Kris; Xu, Weipeng · 2023 · ICCV

> [!todo] metadata-only stub — flesh out from full text when read.

## Concepts
- [[motion-imitation]]

*proposed link — concept note to be created centrally.*

## Abstract (from arXiv)
We present a physics-based humanoid controller that achieves high-fidelity motion imitation and fault-tolerant behavior in the presence of noisy input (e.g. pose estimates from video or generated from language) and unexpected falls. Our controller scales up to learning ten thousand motion clips without using any external stabilizing forces and learns to naturally recover from fail-state. Given reference motion, our controller can perpetually control simulated avatars without requiring resets. At its core, we propose the progressive multiplicative control policy (PMCP), which dynamically allocates new network capacity to learn harder and harder motion sequences. PMCP allows efficient scaling for learning from large-scale motion databases and adding new tasks, such as fail-state recovery, without catastrophic forgetting. We demonstrate the effectiveness of our controller by using it to imitate noisy poses from video-based pose estimators and language-based motion generators in a live and real-time multi-person avatar use case.

## Source
- https://arxiv.org/abs/2305.06456
- DOI: https://doi.org/10.48550/arXiv.2305.06456
