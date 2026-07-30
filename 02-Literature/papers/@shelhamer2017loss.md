---
type: paper
citekey: shelhamer2017loss
tags: [rl, method]
aliases: []
created: 2026-07-29
modified: 2026-07-29
authors:
- Shelhamer, Evan
- Mahmoudieh, Parsa
- Argus, Max
- Darrell, Trevor
year: 2016
venue: ICLR 2017 workshop
doi: 10.48550/arXiv.1612.07307
arxiv: '1612.07307'
url: https://arxiv.org/abs/1612.07307
pdf: attachments/@shelhamer2017loss.pdf
zotero: null
status: to-read
mine: false
---

# Loss is its own Reward: Self-Supervision for Reinforcement Learning

> [!info] Evan Shelhamer; Parsa Mahmoudieh; Max Argus; Trevor Darrell · 2016 · ICLR 2017 workshop
> arXiv:1612.07307 (1612.07307v2, 2017-03-09)

> [!todo] metadata + abstract stub — full text not read. **The "Your take" section below is your own
> writing**, lifted verbatim from [[auxiliary-prediction-heads]] §8.1 (ref `[8]`), where you
> noted the annotations were verified against arXiv metadata on 2026-07-29. Flesh out the rest when read.

## Why it's in otto
Reference `[8]` of your auxiliary-prediction-heads design proposal ([[auxiliary-prediction-heads]]),
under *Auxiliary tasks in navigation RL*. Context for why the *choice* of aux target matters more than the count.

## Your take (your words — authoritative, not ai-draft)
> **Take:** context for why the *choice* of aux target matters more than the count.

## Abstract (from arXiv)
Reinforcement learning optimizes policies for expected cumulative reward. Need the supervision be so
narrow? Reward is delayed and sparse for many tasks, making it a difficult and impoverished signal
for end-to-end optimization. To augment reward, we consider a range of self-supervised tasks that
incorporate states, actions, and successors to provide auxiliary losses. These losses offer
ubiquitous and instantaneous supervision for representation learning even in the absence of reward.
While current results show that learning from reward alone is feasible, pure reinforcement learning
methods are constrained by computational and data efficiency issues that can be remedied by
auxiliary losses. Self-supervised pre-training and joint optimization improve the data efficiency
and policy returns of end-to-end reinforcement learning.

## Concepts
- [[auxiliary-task-learning]]

## My notes
<!-- Your own reactions beyond the take above. -->

## Source
- arXiv: https://arxiv.org/abs/1612.07307 (1612.07307v2, published 2016-12-21, updated 2017-03-09)
- DOI: https://doi.org/10.48550/arXiv.1612.07307
- Abstract quoted verbatim from arXiv. Take quoted verbatim from your [[auxiliary-prediction-heads]] §8.1.
