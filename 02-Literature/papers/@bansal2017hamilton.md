---
type: paper
citekey: bansal2017hamilton
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Bansal, Somil
- Chen, Mo
- Herbert, Sylvia
- Tomlin, Claire J
year: 2017
venue: 2017 IEEE 56th Annual Conference on Decision and Control (CDC)
doi: null
arxiv: 1709.07523
url: https://arxiv.org/abs/1709.07523
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@bansal2017hamilton.pdf
bibkeys:
- bansal2017hamilton
---

# Hamilton-jacobi reachability: A brief overview and recent advances

> [!info] Bansal, Somil; Chen, Mo; Herbert, Sylvia; Tomlin, Claire J · 2017 · 2017 IEEE 56th Annual Conference on Decision and Control (CDC)

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — A tutorial/overview of Hamilton–Jacobi (HJ) reachability analysis for formally verifying performance and safety of dynamical systems, plus recent advances for scaling to higher dimensions.
**Problem** — HJ reachability gives rigorous safety/performance guarantees but its computation scales exponentially with the number of state variables, limiting it to small systems.
**Method** — Reviews the basic HJ reachability formulation (reachable sets as level sets of the value function of an HJ PDE, with formal treatment of bounded disturbances and general nonlinear dynamics) and provides usage guidance for numerical tools, including a GPU-parallelized Level Set Toolbox. Surveys high-dimensional techniques — general theory plus application-specific decompositions — that alleviate the curse of dimensionality.
**Key results** — A consolidated reference: connects HJ theory, disturbance/robustness handling, and practical solvers, and catalogs current strategies for pushing reachability to higher-dimensional systems.

## Takeaways
- HJ reachability handles general nonlinear dynamics and adversarial bounded disturbances, making it a gold standard for safety verification when it is tractable.
- The core obstacle is exponential state-space complexity; recent work leans on system-specific structure (e.g., decomposition) to scale.
- Reachable sets double as the backward-reachable "avoid" or "reach" sets used to certify safe operating regions.

## Relevance to your work
Reachability supplies the formal safety certificates that safety-critical control layers (CBFs, safety filters) approximate more cheaply, which is why it is a reference point for work like [[@cohen2025safety]].

## Concepts
[[control-barrier-function]]

## Source
- Cited by [[@hierarchies2025motion]]
- bibkeys: `bansal2017hamilton`
