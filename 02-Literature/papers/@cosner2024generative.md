---
type: paper
citekey: cosner2024generative
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Cosner, Ryan K
- Sadalski, Igor
- Woo, Jana K
- Culbertson, Preston
- Ames, Aaron D
year: 2024
venue: 2024 IEEE International Conference on Robotics and Automation (ICRA)
doi: null
arxiv: 2311.05802
url: https://arxiv.org/abs/2311.05802
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@cosner2024generative.pdf
bibkeys:
- CosnerICRA24
- cosner2024generative
---

# Generative modeling of residuals for real-time risk-sensitive safety with discrete-time control barrier functions

> [!info] Cosner, Ryan K; Sadalski, Igor; Woo, Jana K; Culbertson, Preston; Ames, Aaron D · 2024 · 2024 IEEE International Conference on Robotics and Automation (ICRA)

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.

**TL;DR** — Learn a generative (CVAE) model of dynamics-residual distributions and combine it with discrete-time CBFs to get a real-time, risk-sensitive safety filter that is less conservative than worst-case robust control.

**Problem** — Worst-case robust control is overly conservative, while deterministic learned dynamics models cannot capture stochastic disturbances/uncertainty; the gap is a safety controller that represents the actual disturbance *distribution*.

**Method** — Train a state-conditioned conditional variational autoencoder (CVAE) to represent the distribution of error residuals between nominal and actual dynamics. This learned generative disturbance model feeds the Online Risk-Informed Optimization controller (ORIO), which enforces discrete-time control barrier function constraints up to a chosen risk level.

**Key results** — Demonstrated in simulation and hardware on a quadrotor flying aggressively with an unmodelled slung load; the probabilistic safety controller runs at 100 Hz on an embedded computer and is less conservative while retaining theoretical safety properties.

## Takeaways
- Uses a distributional (generative) disturbance model rather than a worst-case bound — trades hard guarantees for tunable risk-sensitivity.
- Discrete-time CBF formulation makes it directly deployable in a sampled-data controller at 100 Hz on embedded hardware.
- Safety holds "up to some level of risk": the guarantee is probabilistic, contingent on the learned residual distribution being accurate.

## Relevance to your work
Directly relevant to learning-based robust safety: pairs a learned disturbance model with CBFs, a template for handling model error in locomotion safety filters. See [[@cohen2025safety]].

## Concepts
[[control-barrier-function]]

## Source
- Cited by [[@cohen2025safety]], [[@compton2025dynamic]]
- bibkeys: `CosnerICRA24`, `cosner2024generative`
