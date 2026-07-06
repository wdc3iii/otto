---
type: person
tags: [navigation, rl, planning]
aliases: [Fan Yang]
affiliation: Robotic Systems Lab (RSL), ETH Zurich
role: PhD student
homepage: https://github.com/MichaelFYang
scholar: https://scholar.google.com/citations?user=R3OeSRoAAAAJ
created: 2026-07-06
modified: 2026-07-06
---

# Fan Yang

> [!info] PhD student · Robotic Systems Lab (RSL), ETH Zurich · [homepage](https://github.com/MichaelFYang) · [scholar](https://scholar.google.com/citations?user=R3OeSRoAAAAJ)

> [!note] AI-drafted bio — grounded in public sources; verify and refine.

## Bio
Fan Yang (GitHub: `MichaelFYang`) is a PhD student in the [[marco-hutter|Marco Hutter]]-led
**Robotic Systems Lab (RSL)** at ETH Zurich, where he is a contact person for the lab's
**outdoor / perception-and-navigation** research line. He came to RSL from the **Robotics
Institute at Carnegie Mellon University**, where he was a Master's student and research fellow.
His work centers on **learning-based navigation for legged robots** — local and global planning,
traversability, and mapless/end-to-end trained policies. Listed research interests: perception,
planning, and reinforcement learning.

## Contributions to the field
His navigation stack runs from classical planning to learned end-to-end policies:
- **Autonomous exploration development environment** (2022) — a widely used simulation/planning
  benchmark stack for exploration algorithms (~150 citations).
- **FAR Planner** (2022) — fast, attemptable route planner using dynamic visibility graphs; his
  most-starred repo.
- **iPlanner** (2023) — *imperative* (self-supervised, differentiable) end-to-end path planning.
- **IN-Sight** (2024) — self-supervised interactive navigation that plans *through* obstacles.
- **SRU / Spatially-Enhanced Recurrent Memory** (2025, [[@yang2025spatially]]) — first-author work
  on long-range mapless navigation with a recurrent spatial-memory architecture.

The through-line: progressively replacing hand-built map representations with learned,
self-supervised, memory-equipped policies while keeping the geometric rigor of classical planning.

## Relevance to otto
This is the page's reason to exist: **SRU ([[@yang2025spatially]]) is the architectural anchor for
my mid-level [[recurrent-navigation-policy]].** Two findings from his work directly shape my plan:

1. **Spatial memory ≠ temporal memory.** SRU's core diagnosis is that a plain RNN encodes *temporal*
   history but fails to maintain *egocentric spatial registration* — as the robot moves, past
   observations are not correctly re-anchored to the current body frame, so long-range
   [[mapless-navigation]] degrades. SRU adds an explicit spatial-transform step to the recurrent
   state to fix this. This is the concrete mechanism my [[recurrent-navigation-policy]] note is
   built around, and it sharpens what "memory" must mean for my [[capability-awareness|capability-aware-navigation]]
   plan: I need spatial registration in the recurrent state, not just a longer temporal window.

2. **VAE depth-encoder pretraining for sim-to-real.** SRU's recipe pretrains a depth/perception
   encoder (VAE-style) and reuses it to close the [[sim-to-real-transfer]] gap on the learned
   navigation policy. This is a direct template for my planned **LiDAR encoder** in
   [[capability-awareness|capability-aware-navigation]] — pretrain the perceptual embedding, then
   attach the recurrent policy — rather than training perception and policy jointly from scratch.

**Where it agrees / where I diverge.** We agree that mapless, memory-equipped RL is the right level
of abstraction for mid-level navigation, and I adopt his encoder-pretraining recipe wholesale. The
open contrast is the *capability* axis: SRU targets long-range traversal but does not model a
learned capability boundary (what the robot *can* physically do on given terrain), which is the
candidate contribution of my [[capability-awareness]] line. His co-authored [[@haro2026path]] moves
toward terrain-aware path selection and is worth watching for overlap there.

## In otto — authored works
- **First author** — [[@yang2025spatially]] · SRU / Spatially-Enhanced Recurrent Memory for
  Long-Range Mapless Navigation (arXiv:2506.05997).
- **Co-author** — [[@haro2026path]] · path planning for legged navigation (with Haro, Richter,
  Cadena, Hutter).

> [!warning] Disambiguation — NOT this person: [[@yang2026safesage]] (Safe-SAGE) is first-authored
> by **Lizhi Yang** (Aaron Ames' group, Caltech), a *different* Yang. Do not attribute it to Fan Yang.

## Elsewhere (non-paper)
- GitHub: [MichaelFYang](https://github.com/MichaelFYang) — `far_planner`, `iPlanner`,
  `sru-pytorch-spatial-learning` (SRU reference implementation, under `leggedrobotics`).
- LinkedIn: [fyang-michael](https://www.linkedin.com/in/fyang-michael/)
- RSL group page: [Perception & Navigation](https://rsl.ethz.ch/research/researchtopics/perception-navigation.html)

## Sources
- Google Scholar profile (interests, citation record, paper list): https://scholar.google.com/citations?user=R3OeSRoAAAAJ
- GitHub profile (PhD @ RSL ETH; prior CMU Robotics Institute; pinned repos): https://github.com/MichaelFYang
- RSL Perception & Navigation page (contact person, outdoor-navigation focus): https://rsl.ethz.ch/research/researchtopics/perception-navigation.html
- otto paper frontmatter: `@yang2025spatially` (first author), `@haro2026path` (co-author).
