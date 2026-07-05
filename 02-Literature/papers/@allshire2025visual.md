---
type: paper
citekey: allshire2025visual
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Allshire, Arthur
- Choi, Hongsuk
- Zhang, Junyi
- McAllister, David
- Zhang, Anthony
- Kim, Chung Min
- Darrell, Trevor
- Abbeel, Pieter
- Malik, Jitendra
- Kanazawa, Angjoo
year: 2025
venue: arXiv preprint arXiv:2505.03729
doi: null
arxiv: '2505.03729'
url: https://arxiv.org/abs/2505.03729
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@allshire2025visual.pdf
bibkeys:
- allshire2025visual
---

# Visual imitation enables contextual humanoid control

> [!info] Allshire, Arthur; Choi, Hongsuk; Zhang, Junyi; McAllister, David; Zhang, Anthony; Kim, Chung Min · 2025 · arXiv preprint arXiv:2505.03729

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — VIDEOMIMIC is a real-to-sim-to-real pipeline that mines everyday videos, jointly reconstructs the humans and their environment, and produces context-conditioned whole-body humanoid control policies.
**Problem** — Teaching humanoids environment-aware whole-body skills (climbing stairs, sitting on furniture) at scale, without hand-authored motions or per-skill engineering.
**Method** — From ordinary videos, the system jointly reconstructs human motion and surrounding scene geometry, then trains whole-body control policies in simulation and transfers them to the real robot. A single policy is conditioned on the environment (terrain/context) and a movement command, so behavior adapts to what is around the robot.
**Key results** — Demonstrates contextual behaviors — stair navigation, sitting, and other terrain-dependent skills — on a real humanoid from one environment-conditioned policy (qualitative demos; no benchmark numbers noted).

## Takeaways
- Real-to-sim-to-real from in-the-wild video is a scalable data source for context-aware humanoid skills, sidestepping motion-capture.
- Jointly reconstructing human and scene is what lets the policy be conditioned on environmental context rather than blind whole-body imitation.
- A single environment-conditioned policy covers multiple terrain-dependent behaviors; breadth of skills shown is qualitative.

## Relevance to your work
A data-driven route to terrain- and context-aware whole-body humanoid control — a learning counterpart to the perception-conditioned terrain locomotion in [[@terrain2026consistent]].

## Concepts


## Source
- Cited by [[@terrain2026consistent]]
- bibkeys: `allshire2025visual`
- arXiv: https://arxiv.org/abs/2505.03729
