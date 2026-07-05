---
type: paper
citekey: schulman2017proximal
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Schulman, John
- Wolski, Filip
- Dhariwal, Prafulla
- Radford, Alec
- Klimov, Oleg
year: 2017
venue: arXiv:1707.06347 [cs]
doi: 10.48550/arXiv.1707.06347
arxiv: '1707.06347'
url: https://arxiv.org/abs/1707.06347
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@schulman2017proximal.pdf
bibkeys:
- schulman_proximal_2017
---

# Proximal Policy Optimization Algorithms

> [!info] Schulman, John; Wolski, Filip; Dhariwal, Prafulla; Radford, Alec; Klimov, Oleg · 2017 · arXiv:1707.06347 [cs]

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — PPO is a family of first-order policy-gradient methods that approximate TRPO's trust-region benefits with a clipped surrogate objective, trading a hard KL constraint for simplicity and multi-epoch minibatch updates.
**Problem** — Vanilla policy gradients are sample-inefficient and do one update per sample; TRPO is data-efficient and stable but complex (second-order, hard KL constraint) and incompatible with architectures like dropout or parameter sharing.
**Method** — Alternate between collecting rollouts and optimizing a "surrogate" objective by SGD/Adam over multiple epochs of minibatches. The clipped-ratio objective removes the incentive to move the probability ratio outside [1-eps, 1+eps], giving a pessimistic lower bound on policy improvement without a constrained solve.
**Key results** — On simulated MuJoCo locomotion and Atari, PPO outperforms other online policy-gradient methods and strikes a favorable balance among sample complexity, implementation simplicity, and wall-clock time.

## Takeaways
- Clipped surrogate is the workhorse: cheap first-order optimization with TRPO-like monotonic-improvement intuition, no line search or Fisher-vector products.
- Multiple epochs of minibatch updates per batch of experience is what buys the sample efficiency over vanilla PG.
- Robustness and minimal tuning made it the default on-policy RL algorithm for legged/humanoid sim-to-real pipelines.

## Abstract (from bib)
We propose a new family of policy gradient methods for reinforcement learning, which alternate between sampling data through interaction with the environment, and optimizing a "surrogate" objective function using stochastic gradient ascent. Whereas standard policy gradient methods perform one gradient update per data sample, we propose a novel objective function that enables multiple epochs of minibatch updates. The new methods, which we call proximal policy optimization (PPO), have some of the benefits of trust region policy optimization (TRPO), but they are much simpler to implement, more general, and have better sample complexity (empirically). Our experiments test PPO on a collection of benchmark tasks, including simulated robotic locomotion and Atari game playing, and we show that PPO

## Relevance to your work
PPO is the on-policy RL algorithm underpinning essentially all learned locomotion policies in [[@dai2025walk]] and the broader legged-RL literature — the default optimizer once a task is posed as an MDP.

## Concepts
<!-- [[03-Concepts]] links added when read -->

## Source
- Cited by [[@dai2025walk]]
- bibkeys: `schulman_proximal_2017`
- arXiv: https://arxiv.org/abs/1707.06347
- DOI: https://doi.org/10.48550/arXiv.1707.06347
