---
type: paper
citekey: barto2021reinforcement
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Barto, Andrew G
year: 2021
venue: SIAM Rev
doi: null
arxiv: null
url: http://incompleteideas.net/book/the-book.html
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: missing
bibkeys:
- barto2021reinforcement
---

# Reinforcement learning: An introduction. by richard’s sutton

> [!info] Barto, Andrew G · 2021 · SIAM Rev

## Summary
> [!note] AI-drafted from general knowledge of the work — a base to refine. The bib entry is garbled; it resolves to the canonical textbook *Reinforcement Learning: An Introduction* by Richard S. Sutton and Andrew G. Barto (2nd ed., MIT Press, 2018), the "SIAM Rev 2021" being a book review of it.
**TL;DR** — The standard graduate textbook introducing reinforcement learning: learning to act from reward via interaction with an environment.
**Problem** — Provides a unified, self-contained foundation for the field of RL — the agent–environment formalism, value functions, and the algorithms that estimate them.
**Method** — Builds up from multi-armed bandits and Markov decision processes through dynamic programming, Monte Carlo methods, temporal-difference learning (TD, Sarsa, Q-learning), eligibility traces, and function approximation; the second edition adds policy-gradient methods and connections to psychology and neuroscience.
**Key results** — Not an empirical paper; it establishes the concepts, notation, and algorithmic templates that essentially all modern RL (including deep RL) is built on.

## Takeaways
- Canonical reference for the RL vocabulary — MDPs, Bellman equations, value vs. policy methods, on- vs. off-policy — used to situate any RL contribution.
- The value-function / policy-gradient split it lays out is the backbone of the actor-critic and PPO-style methods used to train locomotion policies.
- Cited for foundations, not a specific result.

## Relevance to your work
This is the foundational reference for the RL formalism behind learned locomotion policies, cited to ground the MDP/policy-gradient machinery used in work like [[@compton2025learning]].

## Concepts

## Source
- Cited by [[@hierarchies2025motion]]
- bibkeys: `barto2021reinforcement`
