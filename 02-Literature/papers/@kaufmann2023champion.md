---
type: paper
citekey: kaufmann2023champion
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Elia Kaufmann
- Leonard Bauersfeld
- Antonio Loquercio
- Matthias Müller
- Vladlen Koltun
- Davide Scaramuzza
year: 2023
venue: Nature 2023 620:7976
doi: 10.1038/s41586-023-06419-4
arxiv: null
url: https://www.nature.com/articles/s41586-023-06419-4
zotero: null
summary: ai-draft
pdf: missing
status: to-read
mine: false
bibkeys:
- Kaufmann2023
---

# Champion-level drone racing using deep reinforcement learning

> [!info] Elia Kaufmann; Leonard Bauersfeld; Antonio Loquercio; Matthias Müller; Vladlen Koltun; Davide Scaramuzza · 2023 · Nature 2023 620:7976

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — Swift, an autonomous FPV drone-racing system trained with deep RL in simulation plus real-world data, races physical quadrotors at the level of human world champions using only onboard sensing.
**Problem** — Beating professional FPV pilots requires flying at the drone's physical limits while estimating speed and location purely from onboard sensors — a hard perception-and-control problem previously unmet by autonomous systems.
**Method** — Combine deep reinforcement learning trained in simulation with data collected in the physical world (to bridge the sim-to-real gap), yielding a vision-based policy that maps onboard sensor estimates to control commands. Deploy on physical racing quadrotors against human champions.
**Key results** — Swift won several head-to-head races against three human champions, including two international-league world champions, and set the fastest recorded race time.

## Takeaways
- A landmark demonstration that sim-trained RL policies can meet/exceed expert human performance on a real, high-speed, physical-limit robot task.
- The winning recipe is RL in simulation plus real-world data to close sim-to-real — not pure simulation.
- Success is specific to a known racing circuit with onboard perception; it is an agility/perception result, not a formal-safety one.

## Abstract (from bib)
First-person view (FPV) drone racing is a televised sport in which professional competitors pilot high-speed aircraft through a 3D circuit. Each pilot sees the environment from the perspective of their drone by means of video streamed from an onboard camera. Reaching the level of professional pilots with an autonomous drone is challenging because the robot needs to fly at its physical limits while estimating its speed and location in the circuit exclusively from onboard sensors1. Here we introduce Swift, an autonomous system that can race physical vehicles at the level of the human world champions. The system combines deep reinforcement learning (RL) in simulation with data collected in the physical world. Swift competed against three human champions, including the world champions of two i

## Relevance to your work
A headline proof point that simulation-trained RL transfers to agile real-world robots at expert level — the kind of motivating precedent [[@compton2025dynamic]] invokes for sim-to-real RL, while contrasting with the formal safety/tube guarantees that pure RL policies lack.

## Concepts


## Source
- Cited by [[@compton2025dynamic]]
- bibkeys: `Kaufmann2023`
