---
type: paper
citekey: girard2006hierarchical
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Girard, Antoine
- Pappas, George J.
year: 2006
venue: Proceedings of the 45th IEEE Conference on Decision and Control
doi: 10.1109/CDC.2006.377051
arxiv: null
url: https://doi.org/10.1109/CDC.2006.377051
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: missing
bibkeys:
- approx_sim_relation
---

# Hierarchical Control using Approximate Simulation Relations

> [!info] Girard, Antoine; Pappas, George J. · 2006 · Proceedings of the 45th IEEE Conference on Decision and Control

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — A hierarchical control framework in which a controller designed on a simple approximate model is lifted to a complex system, with a certified bound on the error between their trajectories.
**Problem** — Designing controllers directly on complex systems is hard; one wants to control a simpler surrogate yet retain guarantees on the true system, especially for safety-critical settings.
**Method** — Uses approximate simulation relations and simulation functions: the simulation function characterizes an interface that maps the approximate system's controller onto the complex system. The simulation function then upper-bounds the distance between the external (output) trajectories of the complex system and its approximation, giving a computable precision.
**Key results** — The guaranteed trajectory-error bound makes the approach suitable for safety-critical systems; demonstrated on a robot motion-control application.

## Takeaways
- The simulation function is the key object: it both defines the lifting interface and certifies a bound on output-tracking error between coarse model and true system.
- This is a formal, bounded-error version of the "plan on a simple model, track on the real robot" idea — a template-and-anchor / reduced-order-model hierarchy with guarantees.
- Bound quality depends on constructing a valid simulation function; conservatism is the practical limitation.

## Relevance to your work
This is a foundational statement of hierarchical control with a certified tracking-error bound between a reduced planning model and the full system — precisely the guarantee structure behind layered locomotion pipelines like [[@hierarchies2025motion]].

## Concepts
[[hierarchical-control]] · [[reduced-order-model]] · [[tracking-error-bound]]

## Source
- Cited by [[@hierarchies2025motion]]
- bibkeys: `approx_sim_relation`
- DOI: https://doi.org/10.1109/CDC.2006.377051
