---
type: paper
citekey: gordon2019splitnet
tags: [rl, navigation]
aliases: []
created: 2026-07-29
modified: 2026-07-29
authors:
- Gordon, Daniel
- Kadian, Abhishek
- Parikh, Devi
- Hoffman, Judy
- Batra, Dhruv
year: 2019
venue: ICCV 2019
doi: 10.48550/arXiv.1905.07512
arxiv: '1905.07512'
url: https://arxiv.org/abs/1905.07512
pdf: attachments/@gordon2019splitnet.pdf
zotero: null
status: to-read
mine: false
---

# SplitNet: Sim2Sim and Task2Task Transfer for Embodied Visual Navigation

> [!info] Daniel Gordon; Abhishek Kadian; Devi Parikh; Judy Hoffman; Dhruv Batra · 2019 · ICCV 2019
> arXiv:1905.07512 (1905.07512v3, 2019-10-23)

> [!todo] metadata + abstract stub — full text not read. **The "Your take" section below is your own
> writing**, lifted verbatim from [[auxiliary-prediction-heads]] §8.1 (ref `[6]`), where you
> noted the annotations were verified against arXiv metadata on 2026-07-29. Flesh out the rest when read.

## Why it's in otto
Reference `[6]` of your auxiliary-prediction-heads design proposal ([[auxiliary-prediction-heads]]),
under *Auxiliary tasks in navigation RL*. Encoder-side aux; geometry decoders buy *transfer*.

## Your take (your words — authoritative, not ai-draft)
> **Take:** encoder-side aux (which our frozen VAE pretraining already covers), plus evidence that geometry decoders help *transfer* — relevant to the MuJoCo↔Isaac gap, not to the GRU.

## Abstract (from arXiv)
We propose SplitNet, a method for decoupling visual perception and policy learning. By incorporating
auxiliary tasks and selective learning of portions of the model, we explicitly decompose the
learning objectives for visual navigation into perceiving the world and acting on that perception.
We show dramatic improvements over baseline models on transferring between simulators, an
encouraging step towards Sim2Real. Additionally, SplitNet generalizes better to unseen environments
from the same simulator and transfers faster and more effectively to novel embodied navigation
tasks. Further, given only a small sample from a target domain, SplitNet can match the performance
of traditional end-to-end pipelines which receive the entire dataset. Code is available
https://github.com/facebookresearch/splitnet

## Concepts
- [[auxiliary-task-learning]]
- [[sim-to-real-transfer]]

## My notes
<!-- Your own reactions beyond the take above. -->

## Source
- arXiv: https://arxiv.org/abs/1905.07512 (1905.07512v3, published 2019-05-18, updated 2019-10-23)
- DOI: https://doi.org/10.48550/arXiv.1905.07512
- Abstract quoted verbatim from arXiv. Take quoted verbatim from your [[auxiliary-prediction-heads]] §8.1.
