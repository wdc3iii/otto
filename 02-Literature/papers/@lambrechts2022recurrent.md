---
type: paper
citekey: lambrechts2022recurrent
tags: [rl, open-question]
aliases: []
created: 2026-07-29
modified: 2026-07-29
authors:
- Lambrechts, Gaspard
- Bolland, Adrien
- Ernst, Damien
year: 2022
venue: TMLR 2022
doi: 10.48550/arXiv.2208.03520
arxiv: '2208.03520'
url: https://arxiv.org/abs/2208.03520
pdf: attachments/@lambrechts2022recurrent.pdf
zotero: null
status: to-read
mine: false
---

# Recurrent networks, hidden states and beliefs in partially observable environments

> [!info] Gaspard Lambrechts; Adrien Bolland; Damien Ernst · 2022 · TMLR 2022
> arXiv:2208.03520 (2208.03520v1, 2022-08-06) · 12 pages, 28 pages total, 20 figures. Transactions on Machine Learning Research (2022)

> [!todo] metadata + abstract stub — full text not read. **The "Your take" section below is your own
> writing**, lifted verbatim from [[auxiliary-prediction-heads]] §8.4 (ref `[21]`), where you
> noted the annotations were verified against arXiv metadata on 2026-07-29. Flesh out the rest when read.

## Why it's in otto
Reference `[21]` of your auxiliary-prediction-heads design proposal ([[auxiliary-prediction-heads]]),
under *Memory, POMDPs, privileged information, and cautions*. How well do RNN hidden states approximate belief states — exactly what the Step-0 probe measures.

## Your take (your words — authoritative, not ai-draft)
> **Take:** background for interpreting a `post_rnn` probe result — "how much belief is in the hidden state" is precisely what our Step-0 probe measures.

## Abstract (from arXiv)
Reinforcement learning aims to learn optimal policies from interaction with environments whose
dynamics are unknown. Many methods rely on the approximation of a value function to derive
near-optimal policies. In partially observable environments, these functions depend on the complete
sequence of observations and past actions, called the history. In this work, we show empirically
that recurrent neural networks trained to approximate such value functions internally filter the
posterior probability distribution of the current state given the history, called the belief. More
precisely, we show that, as a recurrent neural network learns the Q-function, its hidden states
become more and more correlated with the beliefs of state variables that are relevant to optimal
control. This correlation is measured through their mutual information. In addition, we show that
the expected return of an agent increases with the ability of its recurrent architecture to reach a
high mutual information between its hidden states and the beliefs. Finally, we show that the mutual
information between the hidden states and the beliefs of variables that are irrelevant for optimal
control decreases through the learning process. In summary, this work shows that in its hidden
states, a recurrent neural network approximating the Q-function of a partially observable
environment reproduces a sufficient statistic from the history that is correlated to the relevant
part of the belief for taking optimal actions.

## Concepts
- [[belief-state]]
- [[recurrent-navigation-policy]]

## My notes
<!-- Your own reactions beyond the take above. -->

## Source
- arXiv: https://arxiv.org/abs/2208.03520 (2208.03520v1, published 2022-08-06, updated 2022-08-06)
- DOI: https://doi.org/10.48550/arXiv.2208.03520
- Abstract quoted verbatim from arXiv. Take quoted verbatim from your [[auxiliary-prediction-heads]] §8.4.
