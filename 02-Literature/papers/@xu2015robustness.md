---
type: paper
citekey: xu2015robustness
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Xu, Xiangru
- Tabuada, Paulo
- Grizzle, Jessy W
- Ames, Aaron D
year: 2015
venue: IFAC-PapersOnLine
doi: 10.1016/j.ifacol.2015.11.152
arxiv: '1612.01554'
url: https://arxiv.org/abs/1612.01554
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@xu2015robustness.pdf
bibkeys:
- xu2015robustness
---

# Robustness of control barrier functions for safety critical control

> [!info] Xu, Xiangru; Tabuada, Paulo; Grizzle, Jessy W; Ames, Aaron D · 2015 · IFAC-PapersOnLine
> [!info]- otto authors: [[aaron-ames]]

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.

**TL;DR** — Extends control barrier functions with ISS-style robustness to model perturbations and proves the CLF-CBF quadratic-program controller is Lipschitz continuous.

**Problem** — CBFs enforce safety via forward invariance under a Lyapunov-like condition, but their behavior under disturbances/model error and the regularity of the resulting QP controller were not rigorously characterized.

**Method** — First, input-to-state-stability conditions are derived so that, under perturbations to the vector field, a *relaxation* of the nominally invariant safe set remains forward invariant. Second, conditions are given under which the control law from the CLF-CBF quadratic program is Lipschitz continuous, guaranteeing well-defined closed-loop solutions.

**Key results** — Provides ISS-robust forward-invariance guarantees for CBFs under disturbances and establishes Lipschitz continuity (hence well-posedness) of the QP-based safe controller.

## Takeaways
- Under disturbances, exact safe-set invariance is generally lost; the ISS-CBF guarantees invariance of a bounded relaxation instead — a foundational robustness result for CBFs.
- Lipschitz continuity of the CLF-CBF QP is the key well-posedness condition that makes the pointwise-optimal safe controller usable in practice.
- The Sontag-analogy framing (CBFs to CLFs) situates safety synthesis alongside stabilization synthesis.

## Relevance to your work
A canonical robustness/well-posedness foundation for CBF-QP controllers under model error; cited by [[@compton2025learning]] as the theoretical basis for treating safety as a robust, well-posed filter when the model is imperfect.

## Concepts
[[control-barrier-function]]

## Source
- Cited by [[@compton2025learning]]
- bibkeys: `xu2015robustness`
