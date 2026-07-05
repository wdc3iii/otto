---
type: paper
citekey: lee2024integrating
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Lee, Ho Jae
- Hong, Seungwoo
- Kim, Sangbae
year: 2024
venue: 2024 IEEE/RSJ International Conference on Intelligent Robots and Systems (IROS)
doi: null
arxiv: 2408.02662
url: https://arxiv.org/abs/2408.02662
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@lee2024integrating.pdf
bibkeys:
- lee2024integrating
- lee_integrating_2024
---

# Integrating model-based footstep planning with model-free reinforcement learning for dynamic legged locomotion

> [!info] Lee, Ho Jae; Hong, Seungwoo; Kim, Sangbae · 2024 · 2024 IEEE/RSJ International Conference on Intelligent Robots and Systems (IROS)

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — A control framework that derives desired footstep patterns from Linear Inverted Pendulum (LIP) dynamics and trains an RL policy to track those foot placements, rather than tracking full reference motions, giving dynamic legged locomotion with model-based footstep guidance.
**Problem** — Model-based footstep planners give interpretable, dynamically grounded gaits but rely on simplified models and whole-body tracking; model-free RL is robust but hard to steer with precise, physically meaningful footstep intent.
**Method** — The LIP model forward-predicts robot states and computes desired foot placements for a commanded velocity; an RL policy is then trained to track only those footstep targets (not the full LIP trajectory), coupling a lightweight model-based planner with a model-free tracking policy.
**Key results** — On hardware, achieves forward walking up to 1.5 m/s on a treadmill and executes dynamic 90° and 180° turns.

## Takeaways
- Tracking *foot placements* rather than full reference motion is the key design choice — it hands the RL policy just enough structure (where to step) while leaving whole-body execution to learning.
- LIP-based footstep planning is a reduced-order guidance signal, keeping the interface between planner and policy low-dimensional and interpretable.
- Demonstrated dynamic maneuvers (fast walk, sharp turns) on real hardware, arguing the hybrid steers RL better than velocity commands alone.

## Relevance to your work
A clean instance of reduced-order (LIP) footstep planning feeding an RL tracker — the same planner-guides-policy pattern central to reference-guided walking like [[@dai2025walk]], and useful for thinking about what minimal signal (foot placement) best steers a learned locomotion policy.

## Concepts
[[reduced-order-model]] · [[hierarchical-control]]

## Source
- Cited by [[@dai2025walk]], [[@terrain2026consistent]]
- bibkeys: `lee2024integrating`, `lee_integrating_2024`
