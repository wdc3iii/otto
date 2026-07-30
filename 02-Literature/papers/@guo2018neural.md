---
type: paper
citekey: guo2018neural
tags: [rl, method]
aliases: []
created: 2026-07-29
modified: 2026-07-29
authors:
- Guo, Zhaohan Daniel
- Azar, Mohammad Gheshlaghi
- Piot, Bilal
- Pires, Bernardo A.
- Munos, Rémi
year: 2018
venue: arXiv preprint
doi: 10.48550/arXiv.1811.06407
arxiv: '1811.06407'
url: https://arxiv.org/abs/1811.06407
pdf: attachments/@guo2018neural.pdf
zotero: null
status: to-read
mine: false
---

# Neural Predictive Belief Representations

> [!info] Zhaohan Daniel Guo; Mohammad Gheshlaghi Azar; Bilal Piot; Bernardo A. Pires; Rémi Munos · 2018 · arXiv preprint
> arXiv:1811.06407 (1811.06407v2, 2019-08-19)

> [!todo] metadata + abstract stub — full text not read. **The "Your take" section below is your own
> writing**, lifted verbatim from [[auxiliary-prediction-heads]] §8.4 (ref `[23]`), where you
> noted the annotations were verified against arXiv metadata on 2026-07-29. Flesh out the rest when read.

## Why it's in otto
Reference `[23]` of your auxiliary-prediction-heads design proposal ([[auxiliary-prediction-heads]]),
under *Memory, POMDPs, privileged information, and cautions*. Source of the PBL objective used in [4]; why action-conditional prediction beats plain contrastive.

## Your take (your words — authoritative, not ai-draft)
> **Take:** the source of the PBL objective used in [4], and the analysis of *why* action-conditional prediction beats plain contrastive prediction for belief content.

## Abstract (from arXiv)
Unsupervised representation learning has succeeded with excellent results in many applications. It
is an especially powerful tool to learn a good representation of environments with partial or noisy
observations. In partially observable domains it is important for the representation to encode a
belief state, a sufficient statistic of the observations seen so far. In this paper, we investigate
whether it is possible to learn such a belief representation using modern neural architectures.
Specifically, we focus on one-step frame prediction and two variants of contrastive predictive
coding (CPC) as the objective functions to learn the representations. To evaluate these learned
representations, we test how well they can predict various pieces of information about the
underlying state of the environment, e.g., position of the agent in a 3D maze. We show that all
three methods are able to learn belief representations of the environment, they encode not only the
state information, but also its uncertainty, a crucial aspect of belief states. We also find that
for CPC multi-step predictions and action-conditioning are critical for accurate belief
representations in visually complex environments. The ability of neural representations to capture
the belief information has the potential to spur new advances for learning and planning in partially
observable domains, where leveraging uncertainty is essential for optimal decision making.

## Concepts
- [[belief-state]]
- [[auxiliary-task-learning]]

## My notes
<!-- Your own reactions beyond the take above. -->

## Source
- arXiv: https://arxiv.org/abs/1811.06407 (1811.06407v2, published 2018-11-15, updated 2019-08-19)
- DOI: https://doi.org/10.48550/arXiv.1811.06407
- Abstract quoted verbatim from arXiv. Take quoted verbatim from your [[auxiliary-prediction-heads]] §8.4.
