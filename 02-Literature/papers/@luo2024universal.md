---
type: paper
citekey: luo2024universal
tags: []
aliases: []
created: '2026-07-26'
modified: '2026-07-26'
authors:
- Luo, Zhengyi
- Cao, Jinkun
- Merel, Josh
- Winkler, Alexander
- Huang, Jing
- Kitani, Kris
- Xu, Weipeng
year: 2024
venue: ICLR
doi: 10.48550/arXiv.2310.04582
arxiv: '2310.04582'
url: https://arxiv.org/abs/2310.04582
zotero: null
status: to-read
mine: false
pdf: attachments/@luo2024universal.pdf
---

# Universal Humanoid Motion Representations for Physics-Based Control

> [!info] Luo, Zhengyi; Cao, Jinkun; Merel, Josh; Winkler, Alexander; Huang, Jing; Kitani, Kris; Xu, Weipeng · 2024 · ICLR

> [!todo] metadata-only stub — flesh out from full text when read.

## Concepts
- [[motion-imitation]]

*proposed links — concept notes to be created centrally.*

## Abstract (from arXiv)
We present a universal motion representation that encompasses a comprehensive range of motor skills for physics-based humanoid control. Due to the high dimensionality of humanoids and the inherent difficulties in reinforcement learning, prior methods have focused on learning skill embeddings for a narrow range of movement styles (e.g. locomotion, game characters) from specialized motion datasets. This limited scope hampers their applicability in complex tasks. We close this gap by significantly increasing the coverage of our motion representation space. To achieve this, we first learn a motion imitator that can imitate all of human motion from a large, unstructured motion dataset. We then create our motion representation by distilling skills directly from the imitator. This is achieved by using an encoder-decoder structure with a variational information bottleneck. Additionally, we jointly learn a prior conditioned on proprioception (humanoid's own pose and velocities) to improve model expressiveness and sampling efficiency for downstream tasks. By sampling from the prior, we can generate long, stable, and diverse human motions. Using this latent space for hierarchical RL, we show that our policies solve tasks using human-like behavior. We demonstrate the effectiveness of our motion representation by solving generative tasks (e.g. strike, terrain traversal) and motion tracking using VR controllers.

## Source
- https://arxiv.org/abs/2310.04582
- DOI: https://doi.org/10.48550/arXiv.2310.04582
