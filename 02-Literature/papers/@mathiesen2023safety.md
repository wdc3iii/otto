---
type: paper
citekey: mathiesen2023safety
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Frederik Baymler Mathiesen
- Simeon C. Calvert
- Luca Laurenti
year: 2023
venue: IEEE Control Systems Letters
doi: 10.1109/LCSYS.2022.3229865
arxiv: '2206.01463'
url: https://arxiv.org/abs/2206.01463
summary: ai-draft
pdf: attachments/@mathiesen2023safety.pdf
zotero: null
status: to-read
mine: false
bibkeys:
- Mathiesen2023
---

# Safety Certification for Stochastic Systems via Neural Barrier Functions

> [!info] Frederik Baymler Mathiesen; Simeon C. Calvert; Luca Laurenti · 2023 · IEEE Control Systems Letters

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — Parameterizes stochastic barrier functions as neural networks and uses bound-propagation plus linear programming to certify finite-horizon safety probabilities for nonlinear stochastic systems, with tighter, more scalable certificates than prior methods.
**Problem** — Certifying safety of nonlinear stochastic systems is hard; barrier-function methods work but existing searches are restricted to small function classes, yielding conservative certificates.
**Method** — Represent the barrier function (whose composition with the system dynamics forms a supermartingale, bounding the probability of staying in a safe set over a finite horizon) as a neural network. Combine neural-network bound-propagation techniques with linear programming to synthesize valid Neural Barrier Functions, and add a branch-and-bound scheme based on linear relaxations to improve scalability.
**Key results** — Across several case studies, scales to networks of hundreds of neurons and multiple hidden layers and often produces tighter safety certificates than state-of-the-art baselines.

## Takeaways
- Uses the *martingale/supermartingale* barrier-certificate formulation (probabilistic finite-horizon safety), distinct from deterministic CBF forward-invariance.
- The technical enabler is verification-style bound propagation + LP (and branch-and-bound on linear relaxations) to make the neural barrier search sound and scalable.
- Expressive NN parameterization reduces the conservativeness that comes from restricting barrier functions to low-degree polynomials.

## Relevance to your work
Bridges barrier-function safety certification with neural-network verification for stochastic systems — relevant to anyone extending CBF-style safety guarantees to learned components or uncertain dynamics in locomotion/autonomy.

## Abstract (from bib)
Providing non-trivial certificates of safety for non-linear stochastic systems is an important open problem. One promising solution to address this problem is the use of barrier functions. Barrier functions are functions whose composition with the system forms a Martingale and enable the computation of the probability that the system stays within a safe set over a finite time horizon. However, existing approaches to find barrier functions generally restrict the search to a small class of functions, often leading to conservatism. To address this problem, in this letter, we parameterize barrier functions as neural networks and show that bound propagation techniques and linear programming can be successfully employed to find Neural Barrier Functions. Further, we develop a branch-and-bound sch

## Concepts
[[control-barrier-function]]

## Source
- Cited by [[@compton2025dynamic]]
- bibkeys: `Mathiesen2023`
- DOI: https://doi.org/10.1109/LCSYS.2022.3229865
