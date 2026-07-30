---
type: paper
citekey: mirowski2017learning
tags: [rl, navigation]
aliases: []
created: 2026-07-29
modified: 2026-07-29
authors:
- Mirowski, Piotr
- Pascanu, Razvan
- Viola, Fabio
- Soyer, Hubert
- Ballard, Andrew J.
- Banino, Andrea
- Denil, Misha
- Goroshin, Ross
- Sifre, Laurent
- Kavukcuoglu, Koray
- Kumaran, Dharshan
- Hadsell, Raia
year: 2016
venue: ICLR 2017
doi: 10.48550/arXiv.1611.03673
arxiv: '1611.03673'
url: https://arxiv.org/abs/1611.03673
pdf: attachments/@mirowski2017learning.pdf
zotero: null
status: to-read
mine: false
---

# Learning to Navigate in Complex Environments

> [!info] Piotr Mirowski; Razvan Pascanu; Fabio Viola; Hubert Soyer; Andrew J. Ballard; Andrea Banino; Misha Denil; Ross Goroshin; Laurent Sifre; Koray Kavukcuoglu; Dharshan Kumaran; Raia Hadsell · 2016 · ICLR 2017
> arXiv:1611.03673 (1611.03673v3, 2017-01-13) · 11 pages, 5 appendix pages, 11 figures, 3 tables, under review as a conference paper at ICLR 2017

> [!todo] metadata + abstract stub — full text not read. **The "Your take" section below is your own
> writing**, lifted verbatim from [[auxiliary-prediction-heads]] §8.1 (ref `[1]`), where you
> noted the annotations were verified against arXiv metadata on 2026-07-29. Flesh out the rest when read.

## Why it's in otto
Reference `[1]` of your auxiliary-prediction-heads design proposal ([[auxiliary-prediction-heads]]),
under *Auxiliary tasks in navigation RL*. The canonical aux-task nav-RL result, and the empirical basis for attaching heads **post-GRU**.

## Your take (your words — authoritative, not ai-draft)
> **Take:** classification > regression, and **depth-from-LSTM (D2) > depth-from-conv (D1)** — the empirical basis for attaching our heads post-GRU. Loop closure = proposal #4 in binary form.

## Abstract (from arXiv)
Learning to navigate in complex environments with dynamic elements is an important milestone in
developing AI agents. In this work we formulate the navigation question as a reinforcement learning
problem and show that data efficiency and task performance can be dramatically improved by relying
on additional auxiliary tasks leveraging multimodal sensory inputs. In particular we consider
jointly learning the goal-driven reinforcement learning problem with auxiliary depth prediction and
loop closure classification tasks. This approach can learn to navigate from raw sensory input in
complicated 3D mazes, approaching human-level performance even under conditions where the goal
location changes frequently. We provide detailed analysis of the agent behaviour, its ability to
localise, and its network activity dynamics, showing that the agent implicitly learns key navigation
abilities.

## Concepts
- [[auxiliary-task-learning]]
- [[recurrent-navigation-policy]]
- [[belief-state]]

## My notes
<!-- Your own reactions beyond the take above. -->

## Source
- arXiv: https://arxiv.org/abs/1611.03673 (1611.03673v3, published 2016-11-11, updated 2017-01-13)
- DOI: https://doi.org/10.48550/arXiv.1611.03673
- Abstract quoted verbatim from arXiv. Take quoted verbatim from your [[auxiliary-prediction-heads]] §8.1.
