---
type: paper
citekey: bellman1957dynamic
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Bellman, Richard
year: 1957
venue: Princeton University Press
doi: null
arxiv: null
url: null
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: missing
bibkeys:
- bellman1957dynamic
---

# Dynamic Programming

> [!info] Bellman, Richard · 1957 · Princeton University Press

## Summary
> [!note] AI-drafted from bibliographic knowledge of this canonical text (no abstract available) — a base to refine.
**TL;DR** — The founding monograph of dynamic programming: it frames sequential decision problems through the principle of optimality and solves them via recursive functional equations.
**Problem** — How to systematically solve multistage decision/optimization problems where choices at each stage couple to future outcomes, without brute-force enumeration.
**Method** — Introduces the *principle of optimality* (an optimal policy's tail is itself optimal from any intermediate state) and the resulting recursive functional equation (the Bellman equation) over a value function of the state. Bellman also names and analyzes the "curse of dimensionality" — the exponential growth of computation with state dimension.
**Key results** — Establishes dynamic programming as a general method spanning deterministic and stochastic control, resource allocation, and inventory/optimization problems; the value-function recursion becomes the backbone of optimal control and, later, reinforcement learning.

## Takeaways
- The principle of optimality and the Bellman recursion are the conceptual root of optimal control (HJB), MPC cost-to-go, and RL value functions.
- The "curse of dimensionality" is coined here — the reason exact DP is intractable in high dimensions and why approximations/receding-horizon schemes exist.
- Foundational reference, not a method paper: cited for lineage rather than a specific algorithm.

## Relevance to your work
Dynamic programming is the theoretical ancestor of the receding-horizon and value-function machinery used throughout motion planning and control; [[@hierarchies2025motion]] cites it as the optimal-control foundation beneath its planning layer.

## Concepts

## Source
- Cited by [[@hierarchies2025motion]]
- bibkeys: `bellman1957dynamic`
