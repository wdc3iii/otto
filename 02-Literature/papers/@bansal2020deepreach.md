---
type: paper
citekey: bansal2020deepreach
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Somil Bansal
- Claire J. Tomlin
year: 2020
venue: Proceedings - IEEE International Conference on Robotics and Automation
doi: null
arxiv: '2011.02082'
url: https://arxiv.org/abs/2011.02082
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@bansal2020deepreach.pdf
bibkeys:
- Bansal2020
---

# DeepReach: A Deep Learning Approach to High-Dimensional Reachability

> [!info] Somil Bansal; Claire J. Tomlin · 2020 · Proceedings - IEEE International Conference on Robotics and Automation

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — DeepReach trains a sinusoidal neural network as a PDE solver for Hamilton-Jacobi reachability, making backward-reachable-set computation tractable in high state dimensions.
**Problem** — HJ reachability gives formal safety/performance guarantees for general nonlinear systems with bounded disturbances and state/input constraints, but requires solving a PDE whose grid-based complexity scales exponentially with state dimension, capping it at roughly 5-6D systems.
**Method** — DeepReach represents the value function with a sinusoidal (SIREN-style) network and trains it to satisfy the HJ PDE via a self-supervised residual loss (no ground-truth supervision), so cost scales with the complexity of the reachable tube rather than directly with state dimension. The learned value function yields the reachable set and an induced safety controller, and it handles disturbances and constraints.
**Key results** — Demonstrated on a 9D multi-vehicle collision-avoidance problem and a 10D narrow-passage problem for autonomous vehicles — regimes far beyond grid-based solvers.

## Takeaways
- Trades the exponential grid blow-up for neural approximation: scalable, but the safety guarantee is only as good as the learned value function's PDE-residual accuracy (no hard certificate).
- Self-supervised on the PDE itself — no need to precompute solutions, which is what enables the high-dimensional cases.
- Produces both the reachable set and a controller, so it doubles as a synthesis tool, not just verification.

## Relevance to your work
A learning-based route to high-dimensional safety/backward-reachable sets is directly relevant to certifying tracking-error or safety bounds for whole-body/legged systems; it connects to the reachability-vs-tube framing in [[@compton2025dynamic]].

## Abstract (from bib)
Hamilton-Jacobi (HJ) reachability analysis is an important formal verification method for guaranteeing performance and safety properties of dynamical control systems. Its advantages include compatibility with general nonlinear system dynamics, formal treatment of bounded disturbances, and the ability to deal with state and input constraints. However, it involves solving a PDE, whose computational and memory complexity scales exponentially with respect to the number of state variables, limiting its direct use to small-scale systems. We propose DeepReach, a method that leverages new developments in sinusoidal networks to develop a neural PDE solver for high-dimensional reachability problems. The computational requirements of DeepReach do not scale directly with the state dimension, but rathe

## Concepts


## Source
- Cited by [[@compton2025dynamic]]
- bibkeys: `Bansal2020`
