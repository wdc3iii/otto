---
type: paper
citekey: tomlin1995output
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Tomlin, C.
- Lygeros, J.
- Benvenuti, L.
- Sastry, S.
year: 1995
venue: Proceedings of 1995 34th IEEE Conference on Decision and Control
doi: 10.1109/CDC.1995.480615
arxiv: null
url: https://doi.org/10.1109/CDC.1995.480615
zotero: null
summary: ai-draft
pdf: missing
status: to-read
mine: false
bibkeys:
- tomlin_output_1995
---

# Output tracking for a non-minimum phase dynamic CTOL aircraft model

> [!info] Tomlin, C.; Lygeros, J.; Benvenuti, L.; Sastry, S. · 1995 · Proceedings of 1995 34th IEEE Conference on Decision and Control

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — Studies output tracking for a non-minimum-phase longitudinal CTOL aircraft model, where naive input-output linearization leaves unstable internal dynamics.
**Problem** — For a conventional-takeoff-and-landing aircraft, generating an upward pitch moment produces a small downward force (loss of altitude); tracking center-of-mass outputs by input-output linearization exposes unstable internal (zero) dynamics, and the system is neither full-state linearizable nor differentially flat about fixed body points.
**Method** — Applies a nonlinear inversion technique to produce bounded, stable trajectories for the internal-dynamics states, then contrasts it with an approximate linearization approach that trades exactness for practicality.
**Key results** — Nonlinear inversion yields stable internal-dynamics trajectories but requires impractically large feedforward force inputs to track them; the approximate technique gives smaller-magnitude inputs at the cost of exact tracking.

## Takeaways
- A canonical worked example of the non-minimum-phase obstruction to exact output tracking: exact inversion is feasible but demands unrealistic control effort.
- Highlights the fundamental trade-off between tracking accuracy and control-input magnitude when internal dynamics are unstable.
- Motivates approximate-linearization / output-redefinition strategies for non-minimum-phase systems.

## Abstract (from bib)
A dynamic model for the longitudinal axis of a conventional takeoff and landing (CTOL) aircraft is presented. Non-minimum phase characteristics in this model result from the fact that the process of generating an upward pitch moment produces a small downward force, causing the aircraft to lose altitude. The model is not full state linearizable and the internal dynamics which remain after input-output linearization using the coordinates of the center of mass as outputs are unstable. The CTOL model is not flat with respect to fixed points on the aircraft body. The nonlinear inversion technique [l]produces stable trajectories for the states of the internal dynamics, but the corresponding feed-forward force inputs required to track these trajectories are large. A p p \textasciitilde o x imate 

## Relevance to your work
A classic non-minimum-phase output-tracking case study — the internal/zero-dynamics obstruction it exposes is exactly the difficulty the output-tracking designs in [[@compton2024constructive]] must contend with.

## Concepts


## Source
- Cited by [[@compton2024constructive]]
- bibkeys: `tomlin_output_1995`
- DOI: https://doi.org/10.1109/CDC.1995.480615
