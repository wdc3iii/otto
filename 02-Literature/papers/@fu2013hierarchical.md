---
type: paper
citekey: fu2013hierarchical
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- J. Fu
- S. Shah
- H. G. Tanner
year: 2013
venue: ACC
doi: 10.1109/acc.2013.6580099
arxiv: null
url: https://ieeexplore.ieee.org/document/6580099
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@fu2013hierarchical.pdf
bibkeys:
- FuACC13
---

# Hierarchical Control via Approximate Simulation and Feedback Linearization

> [!info] J. Fu; S. Shah; H. G. Tanner · 2013 · ACC

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — Builds a hierarchical plan-and-track scheme for feedback-linearizable nonlinear systems by pairing an approximate simulation relation with feedback linearization, so a simple abstract model can plan while the full system tracks within a certified error.
**Problem** — Connecting a coarse, low-dimensional planning model to a detailed nonlinear plant while guaranteeing that the plant's behavior stays close to the plan, for the class of nonlinear systems that are feedback linearizable.
**Method** — Constructs the hierarchy on the notion of approximate simulation relations: feedback linearization exposes the plant's structure, and an interface controller is designed so the concrete system approximately simulates the abstract planning model, yielding a bounded mismatch between planned and executed trajectories.
**Key results** — Establishes hierarchical trajectory planning and control with a guaranteed approximate-simulation error bound for feedback-linearizable systems (ACC 2013).

## Takeaways
- Approximate simulation is the formal glue: it certifies a bound between abstract plan and concrete execution, which is exactly what a planner/tracker split needs to be safe.
- Feedback linearizability is the enabling assumption — it is what makes the interface and the simulation relation constructible.
- Conceptual ancestor of modern reduced-order-model + tracking-tube hierarchies used in locomotion/navigation.

## Relevance to your work
An early formalization of the reduced-order-planner / full-order-tracker hierarchy with a certified error bound — the same structure that underlies your dynamic-tube and motion-hierarchy work in [[@hierarchies2025motion]], here grounded in approximate simulation rather than tubes.

## Concepts
[[hierarchical-control]] [[reduced-order-model]] [[tracking-error-bound]]

## Source
- Cited by [[@cohen2025safety]]
- bibkeys: `FuACC13`
