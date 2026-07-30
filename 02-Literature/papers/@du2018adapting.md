---
type: paper
citekey: du2018adapting
tags: [rl, method]
aliases: []
created: 2026-07-29
modified: 2026-07-29
authors:
- Du, Yunshu
- Czarnecki, Wojciech M.
- Jayakumar, Siddhant M.
- Farajtabar, Mehrdad
- Pascanu, Razvan
- Lakshminarayanan, Balaji
year: 2018
venue: arXiv preprint
doi: 10.48550/arXiv.1812.02224
arxiv: '1812.02224'
url: https://arxiv.org/abs/1812.02224
pdf: attachments/@du2018adapting.pdf
zotero: null
status: to-read
mine: false
---

# Adapting Auxiliary Losses Using Gradient Similarity

> [!info] Yunshu Du; Wojciech M. Czarnecki; Siddhant M. Jayakumar; Mehrdad Farajtabar; Razvan Pascanu; Balaji Lakshminarayanan · 2018 · arXiv preprint
> arXiv:1812.02224 (1812.02224v2, 2020-11-25)

> [!todo] metadata + abstract stub — full text not read. **The "Your take" section below is your own
> writing**, lifted verbatim from [[auxiliary-prediction-heads]] §8.4 (ref `[26]`), where you
> noted the annotations were verified against arXiv metadata on 2026-07-29. Flesh out the rest when read.

## Why it's in otto
Reference `[26]` of your auxiliary-prediction-heads design proposal ([[auxiliary-prediction-heads]]),
under *Memory, POMDPs, privileged information, and cautions*. **The negative-transfer mitigation** — and the diagnostic to log from run one.

## Your take (your words — authoritative, not ai-draft)
> **Take:** the negative-transfer mitigation, and — even if we never gate — the diagnostic to log from the first run.

## Abstract (from arXiv)
One approach to deal with the statistical inefficiency of neural networks is to rely on auxiliary
losses that help to build useful representations. However, it is not always trivial to know if an
auxiliary task will be helpful for the main task and when it could start hurting. We propose to use
the cosine similarity between gradients of tasks as an adaptive weight to detect when an auxiliary
loss is helpful to the main loss. We show that our approach is guaranteed to converge to critical
points of the main task and demonstrate the practical usefulness of the proposed algorithm in a few
domains: multi-task supervised learning on subsets of ImageNet, reinforcement learning on gridworld,
and reinforcement learning on Atari games.

## Concepts
- [[auxiliary-task-learning]]

## My notes
<!-- Your own reactions beyond the take above. -->

## Source
- arXiv: https://arxiv.org/abs/1812.02224 (1812.02224v2, published 2018-12-05, updated 2020-11-25)
- DOI: https://doi.org/10.48550/arXiv.1812.02224
- Abstract quoted verbatim from arXiv. Take quoted verbatim from your [[auxiliary-prediction-heads]] §8.4.
