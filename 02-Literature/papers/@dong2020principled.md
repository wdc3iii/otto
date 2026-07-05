---
type: paper
citekey: dong2020principled
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Dong, Yunlong
- Tang, Xiuchuan
- Yuan, Ye
year: 2020
venue: Neurocomputing
doi: 10.1016/j.neucom.2020.02.008
arxiv: null
url: https://doi.org/10.1016/j.neucom.2020.02.008
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: missing
bibkeys:
- dong_principled_2020
---

# Principled reward shaping for reinforcement learning via lyapunov stability theory

> [!info] Dong, Yunlong; Tang, Xiuchuan; Yuan, Ye · 2020 · Neurocomputing

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — Uses Lyapunov stability theory to shape RL reward functions, accelerating convergence while preserving optimality.
**Problem** — RL is hampered by hand-designed reward functions and slow convergence; principled reward shaping is needed.
**Method** — A Lyapunov-function-based potential is used to shape the reward, steering the agent toward the region of maximal reward. The shaping is proven potential-based/optimality-invariant, with a convergence guarantee via stochastic approximation and an asymptotically unbiased greedy policy.
**Key results** — On standard RL benchmarks the method substantially accelerates convergence and improves final performance versus unshaped baselines.

## Takeaways
- Ties reward shaping to Lyapunov stability, giving a principled (not ad hoc) shaping signal with formal optimality-invariance.
- Convergence guaranteed via stochastic approximation; shaping is asymptotically unbiased.
- Validated on generic RL benchmarks, not locomotion — transfer to legged control is by analogy.

## Relevance to your work
A theoretical basis for Lyapunov/CLF-derived reward shaping, directly relevant to work stabilizing CLF-guided RL locomotion policies. See [[@olkin2026stability]].

## Abstract (from bib)
Reinforcement learning (RL) suffers from the designation in reward function and the large computational iterating steps until convergence. How to accelerate the training process in RL plays a vital role. In this paper, we proposed a Lyapunov function based approach to shape the reward function which can effectively accelerate the training. Furthermore, the shaped reward function leads to convergence guarantee via stochastic approximation, an invariant optimality condition using Bellman Equation and an asymptotical unbiased policy. Moreover, suﬃcient RL benchmarks have been experimented to demonstrate the effectiveness of our proposed method. It has been veriﬁed that our proposed method substantially accelerates the convergence process as well as improves the performance in terms of a highe

## Concepts

## Source
- Cited by [[@olkin2026stability]]
- bibkeys: `dong_principled_2020`
- DOI: https://doi.org/10.1016/j.neucom.2020.02.008
