---
type: paper
citekey: westervelt2018feedback
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Westervelt, Eric R.
- Grizzle, Jessy W.
- Chevallereau, Christine
- Choi, Jun Ho
- Morris, Benjamin
year: 2018
venue: CRC Press
doi: 10.1201/9781420053739
arxiv: null
url: https://doi.org/10.1201/9781420053739
zotero: null
summary: ai-draft
pdf: missing
status: to-read
mine: false
bibkeys:
- westervelt_feedback_2018
---

# Feedback Control of Dynamic Bipedal Robot Locomotion

> [!info] Westervelt, Eric R.; Grizzle, Jessy W.; Chevallereau, Christine; Choi, Jun Ho; Morris, Benjamin · 2018 · CRC Press

## Summary
> [!note] AI-drafted from the publisher abstract — a base to refine.
**TL;DR** — The foundational monograph on a mathematically rigorous, hybrid-systems approach to feedback control for stable dynamic walking and running in planar bipedal robots.
**Problem** — Most treatments handle bipedal locomotion quasi-statically, overlooking the hybrid (continuous swing + discrete impact) nature and underactuation of genuinely dynamic gaits.
**Method** — Models walking/running as hybrid dynamical systems and analyzes their periodic orbits (limit cycles). It designs feedback controllers — the hybrid zero dynamics (HZD) framework, enforcing virtual constraints so the closed loop restricts to a low-dimensional zero-dynamics manifold — and gives algorithms to synthesize them.
**Key results** — Establishes HZD as a control paradigm for provably stable underactuated locomotion; theory validated in simulation and in experiments on two bipedal testbeds.

## Takeaways
- Virtual constraints + hybrid zero dynamics reduce a high-dimensional walker to a checkable low-dimensional zero dynamics whose orbital stability is verified via a Poincaré return map.
- Marries control theory with mechanics; the scope is planar robots (the 3D extension came in later work).
- Canonical reference for provably stable dynamic bipedal locomotion.

## Relevance to your work
Foundational text for provable stability of legged locomotion; the HZD / reduced-order zero-dynamics viewpoint underpins reduced-order treatments of walking such as those in [[@olkin2026stability]].

## Concepts
[[reduced-order-model]]

## Source
- Cited by [[@olkin2026stability]]
- bibkeys: `westervelt_feedback_2018`
- DOI: https://doi.org/10.1201/9781420053739
