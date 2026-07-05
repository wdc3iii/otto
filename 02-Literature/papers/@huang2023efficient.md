---
type: paper
citekey: huang2023efficient
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Huang, Jiunn-Kai
- Grizzle, Jessy W
year: 2023
venue: IEEE Transactions on Robotics
doi: 10.1109/TRO.2022.3228713
arxiv: 2108.06699
url: https://arxiv.org/abs/2108.06699
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@huang2023efficient.pdf
bibkeys:
- huang2023efficient
---

# Efficient anytime clf reactive planning system for a bipedal robot on undulating terrain

> [!info] Huang, Jiunn-Kai; Grizzle, Jessy W · 2023 · IEEE Transactions on Robotics

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — A two-rate reactive planning system that guides a bipedal robot (Cassie Blue) to a distant goal over unexplored undulating terrain by pairing a 5-Hz anytime planner with a 300-Hz CLF-based reactive controller.
**Problem** — Bipedal navigation on unknown, challenging terrain needs both globally sensible paths and fast local correction of the robot's inevitable deviations, at rates a full planner cannot sustain.
**Method** — A low-frequency (5 Hz) planning thread builds a multi-layer local map for traversability, uses an anytime omnidirectional Control-Lyapunov-Function within an RRT* to produce an asymptotically optimal path and a vector field between nodes, plus a sub-goal finder (for goals beyond the map) and a finite-state machine for mission logic; a high-frequency (300 Hz) CLF reactive thread tracks the vector field and absorbs deviations.
**Key results** — Evaluated in simulation and on the 20-DoF Cassie Blue over varied outdoor undulating terrain and cluttered indoor scenes, enabling autonomous traversal of sinusoidally varying terrain.

## Takeaways
- The CLF is used as an anytime steering primitive inside RRT* (vector-field between nodes), tying Lyapunov-based control directly into the sampling-based planner.
- Clean separation of timescales (5 Hz plan / 300 Hz react) is the architectural idea — the reactive CLF layer is what makes the slow plan robust to real-world deviation.
- Demonstrated on real bipedal hardware over undulating terrain, not just flat ground or simulation.

## Relevance to your work
A concrete CLF-in-the-loop reactive navigation architecture for a biped on rough terrain — directly comparable to the reference-guided navigation stack in [[@terrain2026consistent]], and a data point on layering fast Lyapunov-based control under a slow planner.

## Concepts
[[hierarchical-control]]

## Source
- Cited by [[@terrain2026consistent]]
- bibkeys: `huang2023efficient`
