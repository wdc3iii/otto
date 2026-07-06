---
type: paper
citekey: molnar2022model
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Molnar, Tamas G.
- Cosner, Ryan K.
- Singletary, Andrew W.
- Ubellacker, Wyatt
- Ames, Aaron D.
year: 2022
venue: IEEE Robotics Automation Letters
doi: 10.1109/LRA.2021.3135569
arxiv: '2109.09047'
url: https://arxiv.org/abs/2109.09047
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@molnar2022model.pdf
bibkeys:
- Molnar2022
- TamasRAL22
---

# Model-Free Safety-Critical Control for Robotic Systems

> [!info] Molnar, Tamas G.; Cosner, Ryan K.; Singletary, Andrew W.; Ubellacker, Wyatt; Ames, Aaron D. · 2022 · IEEE Robotics Automation Letters
> [!info]- otto authors: [[aaron-ames]]

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.

**TL;DR** — Enforce safety with a control barrier function at the velocity level and track that safe velocity, avoiding any need for a high-fidelity robot dynamics model.

**Problem** — Safety-critical control via CBFs normally requires an accurate, often complicated, full-order dynamical model of the robot, which is impractical across diverse platforms.

**Method** — Safety is defined on safe regions in configuration space; a safe velocity is synthesized from CBF theory using only kinematics (model-free), then handed to a lower-level tracking controller that realizes it. The authors prove safety guarantees for the composed scheme.

**Key results** — Application-agnostic demonstration: obstacle avoidance for a Segway in high-fidelity simulation, plus hardware experiments on a drone and a quadruped.

## Takeaways
- Decouples safety (kinematic, CBF-based safe velocity) from dynamics (tracking layer) — the tracking error is what must be bounded for the guarantee to hold.
- "Model-free" here means no high-fidelity dynamics model, not zero model; it still assumes velocity can be tracked adequately.
- Clean template for porting CBF safety across robots without re-deriving dynamics.

## Relevance to your work
The safe-velocity-plus-tracking split is the same reduced-order-safety pattern that underlies dynamic-tube and safety-filter work like [[@cohen2025safety]]: safety is certified on a simple model and the residual tracking error must be accounted for.

## Concepts
[[control-barrier-function]] [[reduced-order-model]] [[tracking-error-bound]]


## Source
- Cited by [[@cohen2025safety]], [[@compton2025dynamic]], [[@compton2025learning]]
- bibkeys: `Molnar2022`, `TamasRAL22`
