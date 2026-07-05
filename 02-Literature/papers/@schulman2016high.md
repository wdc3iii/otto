---
type: paper
citekey: schulman2016high
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- John Schulman
- Philipp Moritz
- Sergey Levine
- Michael Jordan
- Pieter Abbeel
year: 2016
venue: Procaeedings of ICLR
doi: null
arxiv: '1506.02438'
url: https://arxiv.org/abs/1506.02438
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@schulman2016high.pdf
bibkeys:
- Schulmanetal_ICLR2016
---

# High-Dimensional Continuous Control Using Generalized Advantage Estimation

> [!info] John Schulman; Philipp Moritz; Sergey Levine; Michael Jordan; Pieter Abbeel · 2016 · Procaeedings of ICLR

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — Introduces Generalized Advantage Estimation (GAE), an exponentially-weighted, TD(λ)-style advantage estimator that trades a little bias for large variance reduction in policy-gradient RL, enabling high-dimensional continuous control.
**Problem** — Policy gradient methods for continuous control suffer from poor sample efficiency (high-variance gradient estimates) and unstable training.
**Method** — Reduces variance with "an exponentially-weighted estimator of the advantage function that is analogous to TD(λ)," and stabilizes learning by applying trust-region optimization to both the policy and the value-function networks. Neural-network policies map raw kinematic state directly to motor commands (no hand-crafted policy).
**Key results** — Learns 3D locomotion in simulation, including running gaits for bipedal and quadrupedal robots and getting a biped up from a prone position; the model-free approach needs simulated experience equivalent to roughly 1–2 weeks of real time for the 3D biped.

## Takeaways
- GAE(γ, λ) is the standard advantage estimator paired with PPO/TRPO; the λ knob directly controls the bias–variance tradeoff.
- Combines two ideas: TD(λ)-style advantage smoothing (variance) + trust-region updates (stability), including a trust region on the value function.
- Demonstrates end-to-end learned neural controllers can produce dynamic legged gaits from raw state, though at a heavy sample cost.

## Relevance to your work
GAE is a core building block of the PPO-style pipelines used to train RL locomotion policies for legged/humanoid robots; it is the default advantage estimator behind the learned low-level policies your control-theoretic layers wrap or certify.

## Concepts


## Source
- Cited by [[@csomayshanklin2024robust]]
- bibkeys: `Schulmanetal_ICLR2016`
