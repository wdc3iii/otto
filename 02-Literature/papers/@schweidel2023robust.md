---
type: paper
citekey: schweidel2023robust
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- K. S. Schweidel
year: 2023
venue: null
doi: null
arxiv: null
url: https://escholarship.org/uc/item/90b1d80j
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@schweidel2023robust.pdf
bibkeys:
- Schweidel
---

# Robust Hierarchical Control with Connected Layers

> [!info] K. S. Schweidel · 2023 · —

## Summary
> [!note] AI-drafted from the dissertation abstract — a base to refine.
**TL;DR** — A UC Berkeley PhD dissertation (Schweidel, advisor M. Arcak, 2023) on layered control where an offline-synthesized tracking controller keeps the error between a high-fidelity model and a lower-fidelity planning model within a bounded set, and that bound is used to make online planning provably safe.
**Problem** — Hierarchical control schemes gain efficiency by planning on a simpler model, but the model mismatch between the planning layer and the true (tracking) model creates an error that, if ignored, breaks safety guarantees.
**Method** — A lower-fidelity planning model is used for online planning while a tracking controller, synthesized offline, keeps the tracking error between the high-fidelity and planning models within a bounded set; the planner's safety constraints are then augmented (tightened) by that tracking-error bound. A robust extension uses integral quadratic constraints (IQCs) to accommodate input uncertainties such as unknown delays or unmodeled actuator dynamics in the tracking model.
**Key results** — Applied to shared human/autonomous longitudinal vehicle control via a "Driver-in-the-Loop Contingency MPC" that uses simplified dynamics to compute invariant sets guaranteeing safety with respect to other vehicles.

## Takeaways
- The core recipe — plan on a reduced model, bound the tracking error offline, tighten the planner's safety constraints by that bound — is exactly the layered-safety pattern used across dynamic-tube and reduced-order locomotion work.
- IQCs are the tool for extending the error bound to input-side uncertainty (delays, actuator dynamics), not just state mismatch.
- Contingency MPC over invariant sets treats other agents as a robustness requirement in the planning layer.

## Relevance to your work
This is squarely the layered planning/tracking-with-error-bound framework at the heart of your own work: an offline tracking-error bound that tightens online planner constraints for guaranteed safety, closely paralleling the layered safety framing in [[@cohen2025safety]].

## Concepts
[[hierarchical-control]] · [[tracking-error-bound]] · [[reduced-order-model]] · [[tube-mpc]]

## Source
- Cited by [[@cohen2025safety]]
- bibkeys: `Schweidel`
