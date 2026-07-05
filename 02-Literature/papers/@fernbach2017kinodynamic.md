---
type: paper
citekey: fernbach2017kinodynamic
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Fernbach, Pierre
- Tonneau, Steve
- Del Prete, Andrea
- Ta\"\ix, Michel
year: 2017
venue: 2017 IEEE/RSJ International Conference on Intelligent Robots and Systems (IROS)
doi: https://doi.org/10.1109/IROS.2017.8206217
arxiv: null
url: https://ieeexplore.ieee.org/document/8206217
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: missing
bibkeys:
- fernbach2017kinodynamic
---

# A kinodynamic steering-method for legged multi-contact locomotion

> [!info] Fernbach, Pierre; Tonneau, Steve; Del Prete, Andrea; Ta\"\ix, Michel · 2017 · 2017 IEEE/RSJ International Conference on Intelligent Robots and Systems (IROS)

## Summary
> [!note] AI-drafted from the paper abstract/metadata — a base to refine.

**TL;DR** — A kinodynamic steering method that connects two robot states with a dynamically-feasible trajectory respecting the state-dependent centroidal dynamics of a legged robot, formulated as an efficient linear program for use inside sampling-based multi-contact planners.

**Problem** — Sampling-based planners for legged multi-contact locomotion need a steering (two-point boundary-value) primitive that accounts for the state-dependent, centroidal dynamic and contact-force constraints, which generic steering methods ignore.

**Method** — Poses the trajectory connecting two states as a Linear Program that enforces the centroidal dynamic constraints implied by the current contacts, making it fast enough to call repeatedly. The approach is automatic and generic — non-gaited motions with arbitrary contact postures on arbitrary terrain.

**Key results** — Generates diverse dynamic behaviors including jumping, descending a very steep slope, and recovering from a push using the arms, with LP-level computational efficiency.

## Takeaways
- Reduces the legged steering problem to an LP by working in the centroidal (reduced-order) dynamics, trading full-body fidelity for tractable, contact-aware feasibility.
- Enables non-gaited, arbitrary-contact motion generation rather than being tied to a fixed gait, useful for acyclic/multi-contact tasks.
- Feasibility is centroidal, not whole-body: whole-body realizability of the arms/contacts must be handled elsewhere in the stack.

## Relevance to your work
A concrete instance of embedding reduced-order (centroidal) dynamic feasibility into the planning layer of a legged-locomotion hierarchy — directly relevant to the dynamically-feasible planning stack of [[@hierarchies2025motion]].

## Concepts
[[reduced-order-model]]

## Source
- Cited by [[@csomayshanklin2025dynamically]], [[@hierarchies2025motion]]
- bibkeys: `fernbach2017kinodynamic`
