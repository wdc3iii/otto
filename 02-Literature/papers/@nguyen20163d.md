---
type: paper
citekey: nguyen20163d
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Nguyen, Quan
- Hereid, Ayonga
- Grizzle, Jessy W.
- Ames, Aaron D.
- Sreenath, Koushil
year: 2016
venue: 2016 IEEE 55th Conference on Decision and Control (CDC)
doi: 10.1109/CDC.2016.7798370
arxiv: null
url: https://doi.org/10.1109/CDC.2016.7798370
summary: ai-draft
pdf: missing
zotero: null
status: to-read
mine: false
bibkeys:
- nguyen_3d_2016
---

# 3D dynamic walking on stepping stones with control barrier functions

> [!info] Nguyen, Quan; Hereid, Ayonga; Grizzle, Jessy W.; Ames, Aaron D.; Sreenath, Koushil · 2016 · 2016 IEEE 55th Conference on Decision and Control (CDC)
> [!info]- otto authors: [[aaron-ames]]

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — Unifies control Lyapunov functions and control barrier functions in a single optimization-based controller to achieve 3-D dynamic walking with precise, constrained footstep placement on stepping stones.
**Problem** — Navigating terrain with discrete footholds requires 3-D dynamic walking subject to precise footstep placement, which demands strict enforcement of step-length and step-width constraints.
**Method** — A single QP-based controller combines CLFs — to achieve periodic walking — with CBFs — to enforce strict constraints on step length and step width. The approach is validated numerically on the full underactuated robot model.
**Key results** — Demonstrates dynamic 3-D walking at 0.6 m/s on DURUS, a 23-DOF underactuated humanoid, with the CBFs enforcing precise footstep placement.

## Takeaways
- Early demonstration of the CLF-CBF QP paradigm extended to 3-D bipedal walking with hard footstep-placement constraints, not just safety sets.
- CBFs encode discrete-foothold reachability (step length/width) as inequality constraints directly in the walking controller.
- Numerical validation only (23-DOF DURUS model); a stepping-stone benchmark for constrained dynamic locomotion.

## Relevance to your work
A foundational CLF-CBF-QP result for enforcing precise footstep placement on discrete terrain, relevant to safety-constrained locomotion as in [[@cohen2025safety]].

## Concepts
[[control-barrier-function]]

## Source
- Cited by [[@dai2025walk]]
- bibkeys: `nguyen_3d_2016`
- DOI: https://doi.org/10.1109/CDC.2016.7798370
