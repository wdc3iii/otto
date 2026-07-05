---
type: paper
citekey: salzmann2024learning
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Salzmann, Tim
- Arrizabalaga, Jon
- Andersson, Joel
- Pavone, Marco
- Ryll, Markus
year: 2024
venue: Learning for Dynamics and Control Conference (L4DC)
doi: 10.48550/arXiv.2312.05873
arxiv: '2312.05873'
url: https://arxiv.org/abs/2312.05873
summary: ai-draft
pdf: attachments/@salzmann2024learning.pdf
zotero: null
status: to-read
mine: false
bibkeys:
- salzmann2024l4casadi
---

# Learning for CasADi: Data-driven Models in Numerical Optimization

> [!info] Salzmann, Tim; Arrizabalaga, Jon; Andersson, Joel; Pavone, Marco; Ryll, Markus · 2024 · Learning for Dynamics and Control Conference (L4DC)

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — L4CasADi, a framework that lets PyTorch-learned models be used directly inside CasADi numerical optimizations, with efficient and potentially hardware-accelerated evaluation and differentiation.

**Problem** — Deep learning excels at modeling complex processes from data, but optimization frameworks like CasADi cannot readily incorporate learned (PyTorch) models into their numerical optimization, blocking their use in solver-based pipelines.

**Method** — L4CasADi bridges PyTorch and CasADi so a trained network becomes a differentiable component of a CasADi optimization problem, exposing the model (and its derivatives) to CasADi's solvers with efficient, optionally GPU-accelerated execution.

**Key results** — Demonstrated on two tutorial examples: optimizing a fish trajectory for energy efficiency through a turbulent flow represented by a PyTorch model, and leveraging an implicit Neural Radiance Field environment representation for optimal control. Released open-source (MIT) at github.com/Tim-Salzmann/l4casadi.

## Takeaways
- Closes the tooling gap between learned models and CasADi-based numerical optimization / optimal control.
- The generalization of the authors' Real-time Neural MPC idea into a reusable open-source library.
- A software/interoperability contribution; value is in making learned models first-class citizens inside solver-based (e.g. MPC) pipelines.

## Relevance to your work
L4CasADi is the practical tooling for embedding a learned model (e.g. a learned tracking-error bound or dynamics term) into a CasADi-based MPC/optimal-control problem — directly relevant to implementing learning-augmented predictive control as in [[@compton2025dynamic]].

## Concepts


## Source
- Cited by [[@compton2025dynamic]]
- bibkeys: `salzmann2024l4casadi`
