---
type: paper
citekey: robey2020learning
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Robey, Alexander
- Hu, Haimin
- Lindemann, Lars
- Zhang, Hanwen
- Dimarogonas, Dimos V
- Tu, Stephen
- Matni, Nikolai
year: 2020
venue: 2020 59th IEEE Conference on Decision and Control (CDC)
doi: 10.1109/CDC42340.2020.9303785
arxiv: 2004.03315
url: https://arxiv.org/abs/2004.03315
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@robey2020learning.pdf
bibkeys:
- robey2020learning
---

# Learning control barrier functions from expert demonstrations

> [!info] Robey, Alexander; Hu, Haimin; Lindemann, Lars; Zhang, Hanwen; Dimarogonas, Dimos V; Tu, Stephen · 2020 · 2020 59th IEEE Conference on Decision and Control (CDC)

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — Learns a provably-safe control barrier function directly from an expert's safe trajectories, via optimization.
**Problem** — Hand-designing CBFs for nonlinear systems is hard; the paper asks whether a valid CBF can instead be *learned* from demonstrated safe behavior.
**Method** — For a known nonlinear control-affine system with access to expert safe trajectories (e.g. a human driver avoiding obstacles), it poses an optimization problem that learns a CBF with provable safety guarantees under Lipschitz-smoothness assumptions. The formulation is agnostic to the CBF parameterization (only needing an efficient Lipschitz bound) and is convex when the parameterization is convex.
**Key results** — Numerical evaluations on planar and realistic examples with both random-feature and deep-neural-network CBF parameterizations; claimed as the first results learning provably safe CBFs from data.

## Takeaways
- Bridges imitation/inverse-RL intuition with safety certificates: expert demonstrations become the supervisory signal for a safety function, not a control policy.
- Guarantees hinge on Lipschitz bounds and sampling density — safety is only as tight as the smoothness assumptions and data coverage allow.
- Parameterization-agnostic and convex-when-convex, so it scales from simple features to deep nets.

## Relevance to your work
A foundational data-driven-CBF reference: it motivates learning safety certificates rather than hand-crafting them, directly relevant to layered safety-critical control such as [[@cohen2025safety]].

## Concepts
[[control-barrier-function]]

## Source
- Cited by [[@compton2025learning]]
- bibkeys: `robey2020learning`
