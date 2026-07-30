---
type: paper
citekey: jaderberg2017reinforcement
tags: [rl, method]
aliases: []
created: 2026-07-29
modified: 2026-07-29
authors:
- Jaderberg, Max
- Mnih, Volodymyr
- Czarnecki, Wojciech Marian
- Schaul, Tom
- Leibo, Joel Z
- Silver, David
- Kavukcuoglu, Koray
year: 2016
venue: ICLR 2017
doi: 10.48550/arXiv.1611.05397
arxiv: '1611.05397'
url: https://arxiv.org/abs/1611.05397
pdf: attachments/@jaderberg2017reinforcement.pdf
zotero: null
status: to-read
mine: false
---

# Reinforcement Learning with Unsupervised Auxiliary Tasks

> [!info] Max Jaderberg; Volodymyr Mnih; Wojciech Marian Czarnecki; Tom Schaul; Joel Z Leibo; David Silver; Koray Kavukcuoglu · 2016 · ICLR 2017
> arXiv:1611.05397 (1611.05397v1, 2016-11-16)

> [!todo] metadata + abstract stub — full text not read. **The "Your take" section below is your own
> writing**, lifted verbatim from [[auxiliary-prediction-heads]] §8.1 (ref `[2]`), where you
> noted the annotations were verified against arXiv metadata on 2026-07-29. Flesh out the rest when read.

## Why it's in otto
Reference `[2]` of your auxiliary-prediction-heads design proposal ([[auxiliary-prediction-heads]]),
under *Auxiliary tasks in navigation RL*. Origin of 'aux tasks on a shared recurrent trunk'.

## Your take (your words — authoritative, not ai-draft)
> **Take:** the original "aux tasks on a shared recurrent trunk" result. Its replay mechanism is the part on-policy PPO here cannot cheaply copy.

## Abstract (from arXiv)
Deep reinforcement learning agents have achieved state-of-the-art results by directly maximising
cumulative reward. However, environments contain a much wider variety of possible training signals.
In this paper, we introduce an agent that also maximises many other pseudo-reward functions
simultaneously by reinforcement learning. All of these tasks share a common representation that,
like unsupervised learning, continues to develop in the absence of extrinsic rewards. We also
introduce a novel mechanism for focusing this representation upon extrinsic rewards, so that
learning can rapidly adapt to the most relevant aspects of the actual task. Our agent significantly
outperforms the previous state-of-the-art on Atari, averaging 880\% expert human performance, and a
challenging suite of first-person, three-dimensional \emph{Labyrinth} tasks leading to a mean
speedup in learning of 10$\times$ and averaging 87\% expert human performance on Labyrinth.

## Concepts
- [[auxiliary-task-learning]]

## My notes
<!-- Your own reactions beyond the take above. -->

## Source
- arXiv: https://arxiv.org/abs/1611.05397 (1611.05397v1, published 2016-11-16, updated 2016-11-16)
- DOI: https://doi.org/10.48550/arXiv.1611.05397
- Abstract quoted verbatim from arXiv. Take quoted verbatim from your [[auxiliary-prediction-heads]] §8.1.
