---
type: paper
citekey: lyle2021effect
tags: [rl, open-question]
aliases: []
created: 2026-07-29
modified: 2026-07-29
authors:
- Lyle, Clare
- Rowland, Mark
- Ostrovski, Georg
- Dabney, Will
year: 2021
venue: AISTATS 2021 (PMLR v130)
doi: 10.48550/arXiv.2102.13089
arxiv: '2102.13089'
url: https://arxiv.org/abs/2102.13089
pdf: attachments/@lyle2021effect.pdf
zotero: null
status: to-read
mine: false
---

# On The Effect of Auxiliary Tasks on Representation Dynamics

> [!info] Clare Lyle; Mark Rowland; Georg Ostrovski; Will Dabney · 2021 · AISTATS 2021 (PMLR v130)
> arXiv:2102.13089 (2102.13089v1, 2021-02-25) · AISTATS 2021

> [!todo] metadata + abstract stub — full text not read. **The "Your take" section below is your own
> writing**, lifted verbatim from [[auxiliary-prediction-heads]] §8.4 (ref `[25]`), where you
> noted the annotations were verified against arXiv metadata on 2026-07-29. Flesh out the rest when read.

## Why it's in otto
Reference `[25]` of your auxiliary-prediction-heads design proposal ([[auxiliary-prediction-heads]]),
under *Memory, POMDPs, privileged information, and cautions*. The theory argument for choosing few, well-aligned targets.

## Your take (your words — authoritative, not ai-draft)
> **Take:** the theory argument for choosing few, well-aligned targets instead of stacking heads.

## Abstract (from arXiv)
While auxiliary tasks play a key role in shaping the representations learnt by reinforcement
learning agents, much is still unknown about the mechanisms through which this is achieved. This
work develops our understanding of the relationship between auxiliary tasks, environment structure,
and representations by analysing the dynamics of temporal difference algorithms. Through this
approach, we establish a connection between the spectral decomposition of the transition operator
and the representations induced by a variety of auxiliary tasks. We then leverage insights from
these theoretical results to inform the selection of auxiliary tasks for deep reinforcement learning
agents in sparse-reward environments.

## Concepts
- [[auxiliary-task-learning]]

## My notes
<!-- Your own reactions beyond the take above. -->

## Source
- arXiv: https://arxiv.org/abs/2102.13089 (2102.13089v1, published 2021-02-25, updated 2021-02-25)
- DOI: https://doi.org/10.48550/arXiv.2102.13089
- Abstract quoted verbatim from arXiv. Take quoted verbatim from your [[auxiliary-prediction-heads]] §8.4.
