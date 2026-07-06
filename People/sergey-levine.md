---
type: person
tags: [rl, navigation, planning]
aliases: [Sergey Levine]
created: 2026-07-06
modified: 2026-07-06
affiliation: UC Berkeley — EECS (BAIR / RAIL); Physical Intelligence
role: Associate Professor of EECS; Co-founder, Physical Intelligence
homepage: https://people.eecs.berkeley.edu/~svlevine/
scholar: https://scholar.google.com/citations?user=8R35rCwAAAAJ
---

# Sergey Levine

> [!info] Associate Professor, EECS · UC Berkeley (BAIR / RAIL) · co-founder [Physical Intelligence](https://www.physicalintelligence.company/) · [homepage](https://people.eecs.berkeley.edu/~svlevine/) · [scholar](https://scholar.google.com/citations?user=8R35rCwAAAAJ)

> [!note] AI-drafted bio — grounded in public sources (below); verify and refine.

## Bio
Associate Professor in the Department of Electrical Engineering and Computer Sciences at
**UC Berkeley**, where he joined the faculty in fall 2016 and leads the **Robotic AI & Learning
Lab (RAIL)** within [BAIR](https://bair.berkeley.edu/). BS/MS (2009) and PhD (2014) in Computer
Science from **Stanford**. In 2024 he co-founded **Physical Intelligence (π)**, a startup building
general-purpose foundation models and learning algorithms for robots. One of the most-cited
researchers in deep RL and robotic learning.

## Contributions to the field
- **Deep RL for continuous control:** co-author of **GAE** ([[@schulman2016high]]), a foundational
  variance-reduction technique underpinning modern policy-gradient methods (PPO/TRPO lineage).
- **End-to-end robotic learning:** early work on training visuomotor policies end-to-end from
  pixels to torques; a leading voice for learning-centric manipulation.
- **Offline RL:** central to the offline-RL research program (CQL, AWAC, IQL) — learning
  performant policies from fixed datasets without online interaction.
- **Foundation models for robot navigation:** the **GNM → ViNT → NoMaD** line — embodiment-agnostic,
  data-driven navigation policies trained across many robots and datasets.
- **Robot foundation models (VLA):** via Physical Intelligence, generalist vision-language-action
  models (e.g. the π-series) for manipulation across embodiments.

## Relevance to otto
Levine's navigation line is the **longer-horizon foil** for my [[capability-aware-navigation]]
project — and the contrast is the payoff.
- **The GNM/ViNT/NoMaD program** ([[@shah2023gnm]], [[@shah2023vint]], [[@sridhar2024nomad]]) is the
  canonical instance of **data-driven, embodiment-agnostic foundation-model navigation**: sparse
  [[topological-navigation]] over dense geometric SLAM, [[mapless-navigation]] driven by learned
  visual goal-reaching, and *cross-robot generalization* from scale (one model drives "any robot").
  This is the direction my project is ultimately heading — learned topological graphs rather than
  hand-built metric maps.
- **Contrast (the payoff):** what this line does **not** provide is exactly what my project needs.
  It offers no notion of a *multi-gait humanoid's* capability-annotated edges, and no *certified*
  [[capability-awareness]] — the policies generalize by scale and diversity, not by construction.
  My [[capability-aware-navigation]] line wants edges labeled by whether a given gait can traverse
  them, with guarantees. Levine's answer to "will the robot make it?" is empirical breadth of
  training data; mine is control-theoretic structure.
- **Structure vs. scale axis:** more broadly, Levine anchors the **scale/generality** pole — massive
  data, offline RL, foundation models. My Ames-lab line injects **control-theoretic structure**
  ([[control-lyapunov-function]] shaping, [[control-barrier-function]] safety, reduced-order
  references) for *certifiable* behavior. He also sits at the RL-methods root of my locomotion work:
  GAE ([[@schulman2016high]]) is upstream of the PPO training my policies use, and he co-authors the
  Berkeley bipedal-RL line ([[@li2024reinforcement]]) that overlaps my humanoid locomotion.

## In otto — authored works
_Papers already in the vault that he (co-)authored:_

- **Visual-navigation foundation models (GNM→ViNT→NoMaD):**
  [[@shah2023gnm]] — GNM: A General Navigation Model to Drive Any Robot ·
  [[@shah2023vint]] — ViNT: A Foundation Model for Visual Navigation ·
  [[@sridhar2024nomad]] — NoMaD: Goal-Masked Diffusion Policies for Navigation and Exploration
- **Deep RL methods:** [[@schulman2016high]] — High-Dimensional Continuous Control Using Generalized Advantage Estimation (GAE)
- **Legged / bipedal RL:** [[@li2024reinforcement]] — RL for versatile, dynamic, and robust bipedal locomotion control

## Elsewhere (non-paper)
- Lab: [Robotic AI & Learning Lab (RAIL)](https://rail.eecs.berkeley.edu/) · [BAIR](https://bair.berkeley.edu/)
- Company: [Physical Intelligence (π)](https://www.physicalintelligence.company/) — co-founder (2024)
- Teaching: Berkeley **CS 285 — Deep Reinforcement Learning** (lectures public on YouTube)
- Profiles: [Google Scholar](https://scholar.google.com/citations?user=8R35rCwAAAAJ) · [Wikipedia](https://en.wikipedia.org/wiki/Sergey_Levine) · [X/@svlevine](https://x.com/svlevine)

## Sources
- UC Berkeley EECS homepage ([people.eecs.berkeley.edu/~svlevine](https://people.eecs.berkeley.edu/~svlevine/)) — role, RAIL lab, Stanford BS/MS/PhD, joined Berkeley fall 2016, research areas.
- Wikipedia "Sergey Levine"; Berkeley VC-Research faculty profile; Google Scholar. Physical Intelligence co-founder (2024) per company/press. Bio drafted 2026-07-06 — confirm before citing.
