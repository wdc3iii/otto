---
type: paper
citekey: igl2018deep
tags: [rl, generative]
aliases: []
created: 2026-07-29
modified: 2026-07-29
authors:
- Igl, Maximilian
- Zintgraf, Luisa
- Le, Tuan Anh
- Wood, Frank
- Whiteson, Shimon
year: 2018
venue: ICML 2018
doi: 10.48550/arXiv.1806.02426
arxiv: '1806.02426'
url: https://arxiv.org/abs/1806.02426
pdf: attachments/@igl2018deep.pdf
zotero: null
status: to-read
mine: false
---

# Deep Variational Reinforcement Learning for POMDPs

> [!info] Maximilian Igl; Luisa Zintgraf; Tuan Anh Le; Frank Wood; Shimon Whiteson · 2018 · ICML 2018
> arXiv:1806.02426 (1806.02426v1, 2018-06-06)

> [!todo] metadata + abstract stub — full text not read. **The "Your take" section below is your own
> writing**, lifted verbatim from [[auxiliary-prediction-heads]] §8.4 (ref `[22]`), where you
> noted the annotations were verified against arXiv metadata on 2026-07-29. Flesh out the rest when read.

## Why it's in otto
Reference `[22]` of your auxiliary-prediction-heads design proposal ([[auxiliary-prediction-heads]]),
under *Memory, POMDPs, privileged information, and cautions*. The model-based end of the spectrum: supervise memory with a generative (ELBO) objective.

## Your take (your words — authoritative, not ai-draft)
> **Take:** the model-based end of the same spectrum — supervise the memory with a learned generative objective instead of privileged targets.

## Abstract (from arXiv)
Many real-world sequential decision making problems are partially observable by nature, and the
environment model is typically unknown. Consequently, there is great need for reinforcement learning
methods that can tackle such problems given only a stream of incomplete and noisy observations. In
this paper, we propose deep variational reinforcement learning (DVRL), which introduces an inductive
bias that allows an agent to learn a generative model of the environment and perform inference in
that model to effectively aggregate the available information. We develop an n-step approximation to
the evidence lower bound (ELBO), allowing the model to be trained jointly with the policy. This
ensures that the latent state representation is suitable for the control task. In experiments on
Mountain Hike and flickering Atari we show that our method outperforms previous approaches relying
on recurrent neural networks to encode the past.

## Concepts
- [[belief-state]]
- [[world-model]]

## My notes
<!-- Your own reactions beyond the take above. -->

## Source
- arXiv: https://arxiv.org/abs/1806.02426 (1806.02426v1, published 2018-06-06, updated 2018-06-06)
- DOI: https://doi.org/10.48550/arXiv.1806.02426
- Abstract quoted verbatim from arXiv. Take quoted verbatim from your [[auxiliary-prediction-heads]] §8.4.
