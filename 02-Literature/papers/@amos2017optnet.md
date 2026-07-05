---
type: paper
citekey: amos2017optnet
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Amos, Brandon
- Kolter, J Zico
year: 2017
venue: International conference on machine learning
doi: null
arxiv: 1703.00443
url: https://arxiv.org/abs/1703.00443
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@amos2017optnet.pdf
bibkeys:
- amos2017optnet
- amos_optnet_2017
---

# Optnet: Differentiable optimization as a layer in neural networks

> [!info] Amos, Brandon; Kolter, J Zico · 2017 · International conference on machine learning

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — OptNet embeds a (convex) quadratic program as a differentiable layer inside an end-to-end trainable neural network.
**Problem** — Standard convolutional/fully-connected layers struggle to encode hard constraints and complex dependencies between hidden states; the authors want optimization itself to be a first-class network primitive.
**Method** — A layer solves a QP whose parameters are learned; using sensitivity analysis, bilevel optimization, and implicit differentiation, gradients are computed exactly by differentiating the KKT conditions. A custom primal–dual interior-point solver does fast GPU batch solves and returns backprop gradients at essentially no extra cost over the forward solve.
**Key results** — Demonstrated on several tasks; notably learns to play 4x4 mini-Sudoku from input/output pairs alone, capturing hard combinatorial constraints better than generic architectures.

## Takeaways
- Differentiating through the KKT/optimality conditions lets an optimization problem sit anywhere in a differentiable pipeline — the enabling trick for "optimization as a layer."
- Batched interior-point solve makes it practical, but each forward pass still pays for solving a QP; scale is bounded by solver cost.
- Foundational for differentiable control/QP layers (e.g., differentiable CLF/CBF-QP safety filters).

## Relevance to your work
The exact-differentiation-through-a-QP machinery underlies differentiable safety filters and layered controllers where a QP (CLF/CBF or MPC) is trained jointly with a policy, which is why it is cited by [[@csomayshanklin2024robust]].

## Concepts

## Source
- Cited by [[@csomayshanklin2024robust]], [[@hierarchies2025motion]]
- bibkeys: `amos2017optnet`, `amos_optnet_2017`
