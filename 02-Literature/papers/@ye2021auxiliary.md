---
type: paper
citekey: ye2021auxiliary
tags: [rl, navigation]
aliases: []
created: 2026-07-29
modified: 2026-07-29
authors:
- Ye, Joel
- Batra, Dhruv
- Das, Abhishek
- Wijmans, Erik
year: 2021
venue: ICCV 2021
doi: 10.48550/arXiv.2104.04112
arxiv: '2104.04112'
url: https://arxiv.org/abs/2104.04112
pdf: attachments/@ye2021auxiliary.pdf
zotero: null
status: to-read
mine: false
---

# Auxiliary Tasks and Exploration Enable ObjectNav

> [!info] Joel Ye; Dhruv Batra; Abhishek Das; Erik Wijmans · 2021 · ICCV 2021
> arXiv:2104.04112 (2104.04112v2, 2021-08-03)

> [!todo] metadata + abstract stub — full text not read. **The "Your take" section below is your own
> writing**, lifted verbatim from [[auxiliary-prediction-heads]] §8.1 (ref `[4]`), where you
> noted the annotations were verified against arXiv metadata on 2026-07-29. Flesh out the rest when read.

## Why it's in otto
Reference `[4]` of your auxiliary-prediction-heads design proposal ([[auxiliary-prediction-heads]]),
under *Auxiliary tasks in navigation RL*. **Coverage prediction is the biggest single ablation contributor** — the closest published analogue of proposal #4.

## Your take (your words — authoritative, not ai-draft)
> **Take:** (a) coverage prediction — our proposal #4 — is the single biggest contributor; (b) at >2 aux tasks, go per-task belief module + attention fusion, not many heads on one GRU.

## Abstract (from arXiv)
ObjectGoal Navigation (ObjectNav) is an embodied task wherein agents are to navigate to an object
instance in an unseen environment. Prior works have shown that end-to-end ObjectNav agents that use
vanilla visual and recurrent modules, e.g. a CNN+RNN, perform poorly due to overfitting and sample
inefficiency. This has motivated current state-of-the-art methods to mix analytic and learned
components and operate on explicit spatial maps of the environment. We instead re-enable a generic
learned agent by adding auxiliary learning tasks and an exploration reward. Our agents achieve 24.5%
success and 8.1% SPL, a 37% and 8% relative improvement over prior state-of-the-art, respectively,
on the Habitat ObjectNav Challenge. From our analysis, we propose that agents will act to simplify
their visual inputs so as to smooth their RNN dynamics, and that auxiliary tasks reduce overfitting
by minimizing effective RNN dimensionality; i.e. a performant ObjectNav agent that must maintain
coherent plans over long horizons does so by learning smooth, low-dimensional recurrent dynamics.
Site: https://joel99.github.io/objectnav/

## Concepts
- [[auxiliary-task-learning]]
- [[belief-state]]
- [[recurrent-navigation-policy]]

## My notes
<!-- Your own reactions beyond the take above. -->

## Source
- arXiv: https://arxiv.org/abs/2104.04112 (2104.04112v2, published 2021-04-08, updated 2021-08-03)
- DOI: https://doi.org/10.48550/arXiv.2104.04112
- Abstract quoted verbatim from arXiv. Take quoted verbatim from your [[auxiliary-prediction-heads]] §8.1.
