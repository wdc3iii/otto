---
type: paper
citekey: stoneman2014embedding
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Stoneman, Samantha
- Lampariello, Roberto
year: 2014
venue: 53rd IEEE Conference on Decision and Control
doi: 10.1109/CDC.2014.7039971
arxiv: null
url: https://doi.org/10.1109/CDC.2014.7039971
summary: ai-draft
pdf: missing
zotero: null
status: to-read
mine: false
bibkeys:
- stoneman2014embedding
---

# Embedding nonlinear optimization in RRT for optimal kinodynamic planning

> [!info] Stoneman, Samantha; Lampariello, Roberto · 2014 · 53rd IEEE Conference on Decision and Control

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — Embeds a nonlinear-program (NLP) optimizer inside RRT* to solve optimal kinodynamic motion planning for complex robots in cluttered environments.
**Problem** — Optimal kinodynamic planning must merge sampling-based search (for global, obstacle-aware exploration) with optimal control (for dynamically feasible, cost-optimal local motions).
**Method** — Rather than embedding an LQR local steering function or solving a kinematic RRT and post-processing with an NLP, the authors embed NLP within the RRT* framework from the start, so each tree connection is a locally optimal, dynamically-constrained trajectory.
**Key results** — Demonstrated on numerical examples, including problems where differential (kinodynamic) constraints are essential.

## Takeaways
- Tightly couples sampling-based global search with per-edge nonlinear trajectory optimization, versus the more common LQR-steer or plan-then-optimize decompositions.
- The NLP steering yields dynamically feasible, asymptotically-optimal (via RRT*) motions but at higher per-connection compute cost.
- A conference-scale demonstration on numerical examples rather than a full hardware system.

## Relevance to your work
A reference point for combining sampling-based planning with optimal control, relevant to the layered planning-and-tracking motion architectures in [[@hierarchies2025motion]].

## Concepts


## Source
- Cited by [[@csomayshanklin2025dynamically]], [[@hierarchies2025motion]]
- bibkeys: `stoneman2014embedding`
