---
type: paper
citekey: acosta2025perceptive
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Acosta, Brian
- Posa, Michael
year: 2025
venue: arXiv:2501.19391 [cs]
doi: 10.48550/arXiv.2501.19391
arxiv: '2501.19391'
url: https://arxiv.org/abs/2501.19391
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@acosta2025perceptive.pdf
bibkeys:
- acosta_perceptive_2025
---

# Perceptive Mixed-Integer Footstep Control for Underactuated Bipedal Walking on Rough Terrain

> [!info] Acosta, Brian; Posa, Michael · 2025 · arXiv:2501.19391 [cs]

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.

**TL;DR** — A full-stack perception + control system for underactuated perceptive bipedal walking on rough terrain, pairing a mixed-integer footstep MPC with an online convex-polygon terrain decomposition.

**Problem** — Online footstep planning on rough terrain is hard because safe-terrain geometry is non-convex and perception/state estimation are imperfect, so a biped must place feet to stabilize while avoiding unsafe regions.

**Method** — (1) Model-predictive footstep control (MPFC): a single mixed-integer QP over a convex-polygon terrain decomposition optimizing discrete foothold choice, footstep position, ankle torque, template dynamics, and footstep timing at >100 Hz. (2) A novel online convex-polygon terrain decomposition whose perception stack decouples safe-terrain classification from planar-polygon fitting, yielding temporally consistent segmentation in real time on a single CPU thread.

**Key results** — Outdoor hardware experiments on the underactuated biped Cassie achieve state-of-the-art perceptive walking on discontinuous terrain.

## Abstract (from bib)
Traversing rough terrain requires dynamic bipeds to stabilize themselves through foot placement without stepping in unsafe areas. Planning these footsteps online is challenging given non-convexity of the safe terrain, and imperfect perception and state estimation. This paper addresses these challenges with a full-stack perception and control system for achieving underactuated walking on discontinuous terrain. First, we develop model-predictive footstep control (MPFC), a single mixed-integer quadratic program which assumes a convex polygon terrain decomposition to optimize over discrete foothold choice, footstep position, ankle torque, template dynamics, and footstep timing at over 100 Hz. We then propose a novel approach for generating convex polygon terrain decompositions online. Our perc

## Takeaways
- The controller (MPFC) is the mature successor to the earlier MIQP footstep controller, now adding footstep *timing* as a decision variable and running >100 Hz.
- The perception contribution — decoupling safe-terrain classification from polygon fitting to get temporally consistent segmentation on one CPU thread — is as central as the controller.
- Validated outdoors, closing the sim-to-real / perception-to-control loop for underactuated rough-terrain walking.

## Relevance to your work
A full-stack optimization+perception baseline for perceptive underactuated walking; its emphasis on temporally consistent terrain segmentation connects directly to [[@terrain2026consistent]].

## Concepts
[[reduced-order-model]]

## Source
- Cited by [[@dai2025walk]]
- bibkeys: `acosta_perceptive_2025`
- arXiv: https://arxiv.org/abs/2501.19391
- DOI: https://doi.org/10.48550/arXiv.2501.19391
