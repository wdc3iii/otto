---
type: paper
citekey: jiang2023abstraction
tags: [navigation, planning, control]
aliases: []
created: '2026-07-06'
modified: '2026-07-06'
authors:
- Jiang, Jesse
- Coogan, Samuel
- Zhao, Ye
year: 2023
venue: IEEE Open Journal of Control Systems
doi: 10.1109/OJCSYS.2023.3296000
arxiv: null
url: https://ieeexplore.ieee.org/document/10184473
zotero: null
summary: ai-draft
pdf: attachments/@jiang2023abstraction.pdf
status: to-read
mine: false
bibkeys:
- jiangAbstractionBasedPlanningUncertaintyAware2023
---

# Abstraction-Based Planning for Uncertainty-Aware Legged Navigation

> [!info] Jesse Jiang; Samuel Coogan; Ye Zhao · 2023 · IEEE Open Journal of Control Systems

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — An Interval-MDP abstraction of bipedal locomotion with Gaussian-process-learned perturbations enables LTL-specified navigation with formal probabilistic guarantees, learning unknown dynamics iteratively until the spec is met.
**Problem** — Temporal-logic-based planning for bipedal robots in uncertain environments, with formal guarantees under motion perturbations from multiple uncertainty sources.
**Method** — Build an Interval Markov Decision Process abstraction of bipedal locomotion (IMDP-BL); incorporate perturbations via stacked Gaussian process learning; specify tasks in Linear Temporal Logic (LTL); construct a product IMDP combining IMDP-BL with a Deterministic Rabin Automaton (DRA) of the specification; synthesize policies that traverse safely, iteratively learning unknown dynamics until the spec is satisfied with satisfactory probability.
**Key results** — Demonstrated in simulation case studies (no numeric figures read).

## Takeaways
- IMDP abstraction gives interval (bounded) transition probabilities — the formal machinery for robustness against model uncertainty.
- Stacked Gaussian processes fold multi-source motion perturbation into the abstraction to preserve guarantees.
- Product IMDP × DRA turns an LTL task into a synthesizable, probabilistically-guaranteed control policy.

## Relevance to your work
Formal, uncertainty-aware planning over a bipedal locomotion abstraction connects to your capability-aware navigation and reduced-order-model thinking: the IMDP-BL is essentially a coarse locomotion model with bounded error, close in spirit to tracking-error-bound / tube reasoning but posed for temporal-logic guarantees.

## Abstract (from bib)
This article addresses the problem of temporal-logic-based planning for bipedal robots in uncertain environments. We first propose an Interval Markov Decision Process abstraction of bipedal locomotion (IMDP-BL). Motion perturbations from multiple sources of uncertainty are incorporated into our model using stacked Gaussian process learning in order to achieve formal guarantees on the behavior of the system. We consider tasks which can be specified using Linear Temporal Logic (LTL). Through a product IMDP construction combining the IMDP-BL of the bipedal robot and a Deterministic Rabin Automaton (DRA) of the specifications, we synthesize control policies which allow the robot to safely traverse the environment, iteratively learning the unknown dynamics until the specifications can be satisfied with satisfactory probability. We demonstrate our methods with simulation case studies.

## Concepts
- [[capability-awareness]]
- [[reduced-order-model]]

## Source
- bibkeys: `jiangAbstractionBasedPlanningUncertaintyAware2023`
- DOI: https://doi.org/10.1109/OJCSYS.2023.3296000
- URL: https://ieeexplore.ieee.org/document/10184473
