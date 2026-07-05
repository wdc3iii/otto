---
type: paper
citekey: apgar2018fast
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Apgar, T.
- Clary, P.
- Green, K.
- Fern, A.
- Hurst, J. W.
year: 2018
venue: 'Robotics: Science and Systems'
doi: 10.15607/RSS.2018.XIV.054
arxiv: null
url: https://doi.org/10.15607/RSS.2018.XIV.054
zotero: null
summary: ai-draft
pdf: missing
status: to-read
mine: false
bibkeys:
- apgar2018fast
---

# Fast Online Trajectory Optimization for the Bipedal Robot Cassie.

> [!info] Apgar, T.; Clary, P.; Green, K.; Fern, A.; Hurst, J. W. · 2018 · Robotics: Science and Systems

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — An online MPC trajectory optimizer for the bipedal robot Cassie that jointly plans center-of-mass motion, footholds, and center of pressure over a reduced-order model, feeding a QP operational-space controller on the full robot.
**Problem** — Multi-step motion planning for a compliant spring-mass biped must run online yet capture the natural locomotion dynamics of lightweight legs.
**Method** — Uses a simplified model combining transverse linear inverted pendulum with vertical spring dynamics; a vertex-based representation of the support area plus closed-form integration yields a fast nonlinear program solved continuously in an MPC loop. The reduced-order plan is tracked by a QP-based operational-space controller on the full-order system.
**Key results** — Simulation shows the planning/control framework performs and rejects disturbances; preliminary hardware results demonstrate the operational-space controller, with planner integration on the physical robot still in progress.

## Takeaways
- Reduced-order (TLIP + vertical spring) model chosen specifically to keep the online NLP fast while respecting compliant-leg dynamics.
- Vertex/support-area representation with closed-form integration is the trick that makes the NLP tractable at MPC rates.
- Classic layered locomotion stack: reduced-order MPC planner on top, QP operational-space controller below.

## Relevance to your work
A concrete instance of the reduced-order-planner / full-order-tracker layering that underpins modern locomotion pipelines like [[@csomayshanklin2025dynamically]], and an early online-MPC baseline for spring-legged bipeds.

## Concepts
[[reduced-order-model]] · [[hierarchical-control]]

## Source
- Cited by [[@csomayshanklin2025dynamically]]
- bibkeys: `apgar2018fast`
