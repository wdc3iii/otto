---
type: paper
citekey: wang2017safe
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Wang, Li
- Ames, Aaron D
- Egerstedt, Magnus
year: 2017
venue: 2017 IEEE International Conference on Robotics and Automation (ICRA)
doi: 10.1109/icra.2017.7989375
arxiv: '1702.01075'
url: https://arxiv.org/abs/1702.01075
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@wang2017safe.pdf
bibkeys:
- wang2017safe
---

# Safe certificate-based maneuvers for teams of quadrotors using differential flatness

> [!info] Wang, Li; Ames, Aaron D; Egerstedt, Magnus · 2017 · 2017 IEEE International Conference on Robotics and Automation (ICRA)
> [!info]- otto authors: [[aaron-ames]]

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.

**TL;DR** — Control-barrier-function "safety barrier certificates" minimally modify differentially-flat quadrotor trajectories to guarantee collision-free multi-robot flight.

**Problem** — Teams of quadrotors following independently planned trajectories can collide; existing flight-planning/control stacks lack provable inter-robot collision-avoidance guarantees.

**Method** — Safety barrier certificates are synthesized with control barrier functions and applied to the differential-flatness-based quadrotor model. They correct the nominal trajectory in a minimally invasive way (a QP-style modification) whenever safety would be violated, layering on top of existing planners/controllers.

**Key results** — Collision avoidance is established both theoretically (provable safety) and experimentally on a team of five quadrotors.

## Takeaways
- Barrier certificates act as a safety filter that minimally alters a nominal (flatness-planned) trajectory — the composable "safety layer" pattern.
- Differential flatness lets safety be enforced in the flat output space, keeping the correction tractable for real-time multi-agent flight.
- Demonstrated on hardware (five quadrotors), an early instance of provably-safe multi-robot coordination via CBFs.

## Relevance to your work
An early, canonical CBF-as-safety-filter result — the minimally-invasive trajectory-modification pattern underpins learning-augmented safe control, which is why it is cited by [[@compton2025learning]].

## Concepts
[[control-barrier-function]]

## Source
- Cited by [[@compton2025learning]]
- bibkeys: `wang2017safe`
