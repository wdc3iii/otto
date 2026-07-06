---
type: paper
citekey: ames2014rapidly
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Ames, Aaron D
- Galloway, Kevin
- Sreenath, Koushil
- Grizzle, Jessy W
year: 2014
venue: IEEE TAC
doi: 10.1109/tac.2014.2299335
arxiv: null
url: https://doi.org/10.1109/tac.2014.2299335
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@ames2014rapidly.pdf
bibkeys:
- ames2014rapidly
- ames_rapidly_2014
---

# Rapidly exponentially stabilizing control lyapunov functions and hybrid zero dynamics

> [!info] Ames, Aaron D; Galloway, Kevin; Sreenath, Koushil; Grizzle, Jessy W · 2014 · IEEE TAC
> [!info]- otto authors: [[aaron-ames]]

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — Introduces *rapidly exponentially stabilizing* control Lyapunov functions (RES-CLFs) that drive the state to the hybrid zero dynamics surface fast enough to exponentially stabilize a periodic walking orbit of the full-order hybrid (impulse-effect) system.
**Problem** — Prior stabilization of periodic orbits in systems with impulse effects relied on input-output linearization of the transverse dynamics; a more general Lyapunov-based route to exponential orbital stability was missing.
**Method** — Assume the orbit lies in a C¹ submanifold Z (the zero set of an output, invariant under both continuous and discrete dynamics) with exponentially stable hybrid zero dynamics. A CLF variant that enforces *rapid* exponential convergence to Z is shown to yield exponential stability of the full-order periodic orbit, broadening the admissible class of stabilizing controllers beyond input-output linearization.
**Key results** — Demonstrated on a hybrid bipedal walking model in simulation and used to experimentally realize bipedal locomotion via CLFs.

## Takeaways
- RES-CLFs give a Lyapunov certificate for exponential orbital stability of hybrid/legged systems, decoupling the "converge to Z" requirement from a specific linearizing controller.
- Convergence to the zero dynamics surface must be *rapid* (tunable rate) so that the full-order orbit inherits the HZD's exponential stability.
- Bridges CLF-based control (often deployed via a pointwise QP) and the hybrid-zero-dynamics gait design framework, on real bipedal hardware.

## Relevance to your work
Foundational for CLF-based stabilization of underactuated legged systems and the zero-dynamics viewpoint your own work builds on; directly cited by [[@compton2024constructive]] as prior art for stabilizing to a zero dynamics surface.

## Concepts
[[reduced-order-model]]

## Source
- Cited by [[@compton2024constructive]], [[@olkin2026stability]]
- bibkeys: `ames2014rapidly`, `ames_rapidly_2014`
