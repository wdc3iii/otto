---
type: person
tags: [locomotion, control, rl]
aliases: [Zachary Olkin]
created: 2026-07-06
modified: 2026-07-06
affiliation: Caltech — AMBER Lab (Control & Dynamical Systems)
role: PhD student (Control & Dynamical Systems); advisor Aaron D. Ames
homepage: https://www.zacholkin.com/
scholar: https://scholar.google.com/citations?user=9bsrJHQAAAAJ
---

# Zachary Olkin

> [!info] PhD student, Control & Dynamical Systems · Caltech AMBER Lab (advisor [[aaron-ames|Aaron D. Ames]]) · [homepage](https://www.zacholkin.com/) · [scholar](https://scholar.google.com/citations?user=9bsrJHQAAAAJ)

> [!note] AI-drafted bio — grounded in public sources (below); verify and refine.

## Bio
PhD student in **Control & Dynamical Systems** at Caltech, in Aaron Ames's **AMBER Lab**,
working on control theory and legged robotics. Undergraduate in Computer Engineering at
Georgia Tech; prior industry experience at Left Hand Robotics (autonomous snow-clearing /
lawn-mowing robots). Research interests span controls, legged locomotion, and autonomous
flight systems, with a stated emphasis on real-world deployment. *(Details from his
personal site; specific dates/awards not verified — treat as inferred where unconfirmed.)*

## Contributions to the field
His central line is **CLF-guided reinforcement learning (CLF-RL)** for humanoid locomotion —
injecting model-based structure into RL rather than scaling data alone:
- **CLF-RL reward shaping** ([[@li2025clf]], [[@li2026clf]]): embed a [[control-lyapunov-function]]
  and optimized reference trajectories into the RL reward during *training only*, yielding a
  lightweight deployable policy. Reported ~34% lower cost of transport and ~75% lower position
  error vs. pure RL on the Unitree G1.
- **Dynamic humanoid running** ([[@olkin2025chasing]], [[@olkin2026chasing]]): multi-domain
  trajectory optimization + CLFs + RL for a running controller with a true flight phase,
  demonstrated on the G1 on a treadmill and outdoors, with accurate velocity/position tracking
  and robustness to ground clutter.
- **Stability analysis of CLF-RL** ([[@olkin2026stability]]): formal grounding for *why* the
  CLF-shaped policy inherits stability guarantees — the theory backing the empirical method.

See [[rl-for-legged-locomotion]] and [[learning-based-locomotion]] for the surrounding landscape.

## Relevance to otto
Olkin is a **core AMBER-lab collaborator** and a co-author on several of my own papers — the
person whose CLF-RL locomotion work is the *substrate* my navigation project builds on.
- **He owns the frozen LLC.** My [[capability-aware-navigation]] project layers a mid-level
  navigation policy over a **frozen CLF-RL locomotion controller** — precisely the controller
  from [[@li2025clf]] / [[@olkin2025chasing]] (running) and its terrain-aware sibling
  [[@terrain2026consistent]]. His controller is the fixed capability primitive my policy
  commands SE(2) velocities to.
- **He is the source of the $V_t$ signal.** My candidate contribution repurposes the LLC's own
  CLF Lyapunov value $V_t = \eta^\top P\eta$ — which *exists because* of Olkin/Li's CLF-RL
  training ([[@li2025clf]]) — as a navigation-level **comfort signal** to penalize commands that
  drive the LLC out of distribution. Without his CLF-shaped controller there is no $V_t$ to read.
  See [[capability-awareness]], [[control-lyapunov-function]].
- **Named on the target publication.** My navigation paper targets an IEEE conference with the
  **Olkin / Bena / Ames** authorship (TII support) — he is a listed collaborator, not just an
  upstream reference.
- **Shared philosophy (agreement, not contrast).** Unlike the structure-vs-scale contrast with
  [[marco-hutter|Hutter]]'s data-driven line, Olkin sits squarely on my side of that axis:
  inject control-theoretic structure (CLF rewards, reduced-order references) into RL for
  certifiable stability. The tension is internal/methodological — analytical ROM capability vs.
  the *learned* controller's emergent capability boundary — which is exactly what
  [[capability-awareness]] tries to operationalize.

## In otto — authored works
_Papers in the vault he (co-)authored:_

- **First author:**
  - [[@olkin2025chasing]] — Chasing Stability: Humanoid Running via CLF-Guided RL (arXiv 2509.19573)
  - [[@olkin2026chasing]] — Chasing Autonomy: Dynamic Retargeting and Control-Guided RL for Humanoid Running (IROS 2026)
  - [[@olkin2026stability]] — Stability of CLF-Guided RL (CDC 2026)
- **Co-author (CLF-RL, w/ Kejun Li):**
  - [[@li2025clf]] · [[@li2026clf]] — CLF-RL: Control Lyapunov Function Guided Reinforcement Learning (arXiv 2508.09354 → RA-L 2026)
- **Co-author (my work):**
  - [[@terrain2026consistent]] — Terrain-Consistent Reference-Guided RL for Humanoid Navigation Autonomy (Compton, Olkin, Ames)
- **Other:**
  - [[@gu2025evolution]] — Evolution of Humanoid Locomotion Control (contributor)

Concepts his work grounds: [[control-lyapunov-function]] · [[rl-for-legged-locomotion]] · [[capability-awareness]].

## Elsewhere (non-paper)
- Personal site: [zacholkin.com](https://www.zacholkin.com/) — incl. [CLF-RL research page](https://www.zacholkin.com/research/clf_rl/)
- Lab: [AMBER Lab / bipedalrobotics.com](http://www.bipedalrobotics.com/people.html)
- [Google Scholar](https://scholar.google.com/citations?user=9bsrJHQAAAAJ)

## Sources
- [zacholkin.com/about](https://www.zacholkin.com/about/) (role, training, lab, interests); AMBER Lab people page; Google Scholar; arXiv 2508.09354 / 2509.19573 abstracts. Bio drafted 2026-07-06 — some biographical details (dates, awards) unverified and flagged inferred; confirm before citing.
