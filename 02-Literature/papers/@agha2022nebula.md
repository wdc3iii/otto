---
type: paper
citekey: agha2022nebula
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Agha, Ali
- Otsu, Kyohei
- Morrell, Benjamin
- Fan, David D
- Thakker, Rohan
- Santamaria-Navarro, Angel
- Kim, Sung-Kyun
- Bouman, Amanda
- Lei, Xianmei
- Edlund, Jeffrey
- others
year: 2022
venue: Field robotics
doi: 10.55417/fr.2022047
arxiv: null
url: https://doi.org/10.55417/fr.2022047
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@agha2022nebula.pdf
bibkeys:
- agha2022nebula
---

# NeBula: TEAM CoSTAR's robotic autonomy solution that won phase II of DARPA subterranean challenge

> [!info] Agha, Ali; Otsu, Kyohei; Morrell, Benjamin; Fan, David D; Thakker, Rohan; Santamaria-Navarro, Angel · 2022 · Field robotics

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — A comprehensive system paper on NeBula, the uncertainty-aware, belief-space autonomy stack Team CoSTAR fielded to place 2nd (Tunnel) and 1st (Urban) in the DARPA Subterranean Challenge.
**Problem** — Achieving resilient, modular robotic autonomy in large, perceptually-degraded, unknown subterranean environments across heterogeneous platforms (wheeled, legged, flying).
**Method** — NeBula (Networked Belief-aware Perceptual Autonomy) performs reasoning and decision-making in belief space (distributions over robot and world states). The paper details its components: geometric/semantic mapping, a multi-modal positioning system, traversability analysis and local planning, global motion planning and exploration, risk-aware mission planning, decentralized networking, and learning-enabled adaptation.
**Key results** — Reports fielded performance across robot types and environments in the SubT competition courses (plus Martian-analog lava-tube demos), with lessons learned rather than a single headline metric.

## Takeaways
- Belief-space (uncertainty-aware) reasoning is the organizing principle tying perception, localization, planning, and mission-level decisions together.
- A full autonomy stack: traversability analysis and layered local/global planning are what let heterogeneous robots explore unknown terrain.
- Systems/lessons-learned paper, not a single-algorithm contribution — the value is the integrated architecture and field evidence.
- Related but distinct from the earlier arXiv "NeBula: Quest for Robotic Autonomy…" (2103.11470); this is the Field Robotics "Won Phase II" journal version.

## Relevance to your work
The canonical reference for perception-driven traversability analysis and layered planning on legged/heterogeneous robots in unstructured terrain — context for terrain-aware navigation autonomy in [[@terrain2026consistent]].

## Concepts


## Source
- Cited by [[@terrain2026consistent]]
- bibkeys: `agha2022nebula`
