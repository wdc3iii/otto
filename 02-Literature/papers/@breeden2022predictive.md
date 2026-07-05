---
type: paper
citekey: breeden2022predictive
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Breeden, Joseph
- Panagou, Dimitra
year: 2022
venue: 2022 IEEE 61st Conference on Decision and Control (CDC)
doi: 10.1109/CDC51059.2022.9992926
arxiv: '2204.00208'
url: https://arxiv.org/abs/2204.00208
summary: ai-draft
pdf: attachments/@breeden2022predictive.pdf
zotero: null
status: to-read
mine: false
bibkeys:
- breeden2022predictive
---

# Predictive control barrier functions for online safety critical control

> [!info] Breeden, Joseph; Panagou, Dimitra · 2022 · 2022 IEEE 61st Conference on Decision and Control (CDC)

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — Constructs Control Barrier Functions from a receding-horizon forward propagation of the nominal trajectory, so the controller acts proactively before the trajectory would leave the safe set.

**Problem** — Standard CBFs act reactively at the boundary of the safe set and can be hard to construct for systems where future safety depends on trajectory evolution; a predictive notion of safety is needed.

**Method** — Propagates a nominal trajectory on a receding horizon and encodes the future safety of that trajectory into a CBF. If the propagated trajectory is predicted to become unsafe, a controller satisfying the CBF condition modifies the nominal trajectory before it leaves the safe set — proactive rather than reactive correction.

**Key results** — Proven safe and demonstrated in simulated scenarios where a traditional CBF is difficult to construct; compared to a traditional CBF the predictive CBF makes smaller trajectory modifications and uses smaller control inputs, and computes faster than a nonlinear MPC approach.

## Takeaways
- Bridges CBFs and receding-horizon prediction: safety of a future propagated trajectory becomes the barrier condition today.
- Proactive correction yields smaller deviations and inputs than reactive CBFs, at lower compute cost than NMPC.
- Useful precisely where hand-designing a valid CBF is hard; relies on trajectory propagation quality over the horizon.

## Relevance to your work
A predictive/receding-horizon CBF sits between reactive safety filters and full MPC — directly relevant to safe, foresightful control in learning-based locomotion pipelines ([[@compton2025learning]]).

## Concepts
[[control-barrier-function]]

## Source
- Cited by [[@compton2025learning]]
- bibkeys: `breeden2022predictive`
