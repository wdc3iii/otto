---
type: paper
citekey: ahmed2021self
tags: [rl, method]
aliases: []
created: 2026-07-29
modified: 2026-07-29
authors:
- Ahmed, Eltayeb
- Zintgraf, Luisa
- Witt, Christian A. Schroeder de
- Usunier, Nicolas
year: 2021
venue: arXiv preprint
doi: 10.48550/arXiv.2104.08492
arxiv: '2104.08492'
url: https://arxiv.org/abs/2104.08492
pdf: attachments/@ahmed2021self.pdf
zotero: null
status: to-read
mine: false
---

# A Self-Supervised Auxiliary Loss for Deep RL in Partially Observable Settings

> [!info] Eltayeb Ahmed; Luisa Zintgraf; Christian A. Schroeder de Witt; Nicolas Usunier · 2021 · arXiv preprint
> arXiv:2104.08492 (2104.08492v1, 2021-04-17)

> [!todo] metadata + abstract stub — full text not read. **The "Your take" section below is your own
> writing**, lifted verbatim from [[auxiliary-prediction-heads]] §8.1 (ref `[7]`), where you
> noted the annotations were verified against arXiv metadata on 2026-07-29. Flesh out the rest when read.

## Why it's in otto
Reference `[7]` of your auxiliary-prediction-heads design proposal ([[auxiliary-prediction-heads]]),
under *Auxiliary tasks in navigation RL*. The cheapest memory-supervising loss — zero privileged info. A near-free control arm.

## Your take (your words — authoritative, not ai-draft)
> **Take:** the cheapest possible memory-supervising loss — no privileged information at all. A good near-free control arm against our privileged-target heads.

## Abstract (from arXiv)
In this work we explore an auxiliary loss useful for reinforcement learning in environments where
strong performing agents are required to be able to navigate a spatial environment. The auxiliary
loss proposed is to minimize the classification error of a neural network classifier that predicts
whether or not a pair of states sampled from the agents current episode trajectory are in order. The
classifier takes as input a pair of states as well as the agent's memory. The motivation for this
auxiliary loss is that there is a strong correlation with which of a pair of states is more recent
in the agents episode trajectory and which of the two states is spatially closer to the agent. Our
hypothesis is that learning features to answer this question encourages the agent to learn and
internalize in memory representations of states that facilitate spatial reasoning. We tested this
auxiliary loss on a navigation task in a gridworld and achieved 9.6% increase in accumulative
episode reward compared to a strong baseline approach.

## Concepts
- [[auxiliary-task-learning]]
- [[belief-state]]

## My notes
<!-- Your own reactions beyond the take above. -->

## Source
- arXiv: https://arxiv.org/abs/2104.08492 (2104.08492v1, published 2021-04-17, updated 2021-04-17)
- DOI: https://doi.org/10.48550/arXiv.2104.08492
- Abstract quoted verbatim from arXiv. Take quoted verbatim from your [[auxiliary-prediction-heads]] §8.1.
