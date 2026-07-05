---
type: paper
citekey: pratt2006capture
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Pratt, Jerry
- Carff, John
- Drakunov, Sergey
- Goswami, Ambarish
year: 2006
venue: 2006 6th IEEE-RAS International Conference on Humanoid Robots
doi: 10.1109/ICHR.2006.321385
arxiv: null
url: https://doi.org/10.1109/ICHR.2006.321385
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: missing
bibkeys:
- pratt_capture_2006
---

# Capture Point: A Step toward Humanoid Push Recovery

> [!info] Pratt, Jerry; Carff, John; Drakunov, Sergey; Goswami, Ambarish · 2006 · 2006 6th IEEE-RAS International Conference on Humanoid Robots

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — Introduces the capture point and capture region — where a humanoid must step to come to a complete stop — with exact solutions for a linear-inverted-pendulum-plus-flywheel model, giving a principled "when and where to step" criterion for push recovery.
**Problem** — For a large push, a human or humanoid must step to avoid falling, but no principled account of *when and where* to step had emerged.
**Method** — The authors define capture points and the capture region (the ground region a robot must step to in order to stop), and use the intersection of the capture region with the base of support to select the recovery strategy. Extending the linear inverted pendulum model with a flywheel body yields exact closed-form capture regions and lets the robot exploit centroidal angular momentum, much as humans do, which significantly enlarges the capture region.
**Key results** — Simulations of a simple planar biped recover balance after a push by stepping to the capture region and using internal angular momentum; the simple-model solution is proposed as an approximation for more complex 3D bipeds with distributed mass.

## Takeaways
- Capture point / capture region give a reduced-order, geometric criterion for step-based push recovery.
- Adding a flywheel (angular-momentum) term to the LIP substantially enlarges the recoverable region — momentum matters, not just foot placement.
- Exact solutions exist only for the simple model; extension to full-body 3D robots is approximate.

## Abstract (from bib)
It is known that for a large magnitude push a human or a humanoid robot must take a step to avoid a fall. Despite some scattered results, a principled approach towards “When and where to take a step” has not yet emerged.

## Concepts
[[reduced-order-model]]

## Relevance to your work
A foundational reduced-order (LIP + flywheel) formulation of balance and step placement; the capturability notion underlies stability-oriented humanoid locomotion work such as [[@olkin2026stability]].

## Source
- Cited by [[@olkin2026stability]]
- bibkeys: `pratt_capture_2006`
- DOI: https://doi.org/10.1109/ICHR.2006.321385
