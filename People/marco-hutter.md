---
type: person
tags: [locomotion, rl, navigation]
aliases: [Marco Hutter]
created: 2026-07-06
modified: 2026-07-06
affiliation: ETH Zurich — Robotic Systems Lab (RSL)
role: Professor of Robotic Systems; Director, Center for Robotics
homepage: https://rsl.ethz.ch/
scholar: https://scholar.google.com/citations?user=DO3quJYAAAAJ
---

# Marco Hutter

> [!info] Professor of Robotic Systems, Director of the Center for Robotics · ETH Zurich (RSL) · [homepage](https://rsl.ethz.ch/) · [scholar](https://scholar.google.com/citations?user=DO3quJYAAAAJ)

> [!note] AI-drafted bio — grounded in public sources (below); verify and refine.

## Bio
Professor for Robotic Systems at ETH Zurich (since 2015) and Director of the ETH Center for
Robotics, leading the **Robotic Systems Lab (RSL)**. MSc (2009) and PhD (2013) from ETH Zurich
on the design, actuation, and control of legged robots; Branco Weiss fellow (2014). Best known
for the **ANYmal** quadruped and for pushing legged machines into rough, real-world terrain.
Co-founder of several ETH spin-offs — **ANYbotics**, **Gravis Robotics**, **SwissMile Robotics** —
and leads the Zurich office of the **Robotics and AI (RAI) Institute**.

## Contributions to the field
- **Legged robot design → deployment:** actuation (series-elastic / quasi-direct-drive) through
  to industrial inspection with ANYmal.
- **Learning-based locomotion at scale:** among the highest-impact work turning massively
  parallel simulation + deep RL into robust, deployable locomotion.
- **Perceptive locomotion:** fusing exteroception (vision/elevation maps) with proprioception so
  robots traverse stairs, rubble, and wild terrain — including MPC and end-to-end RL variants.
- **Mapless / learned navigation** for legged and wheeled-legged platforms.

## Relevance to otto
His work sits directly on top of otto's focus areas — and offers a sharp philosophical contrast
to my own line, which is the interesting part.
- **Massively-parallel RL:** [[@rudin2021learning|Learning to Walk in Minutes]] is a foundational
  reference for [[massively-parallel-simulation]] — the exact GPU-sim recipe (thousands of
  parallel envs) that my CLF-guided RL work ([[@dai2025walk]], [[@terrain2026consistent]]) trains
  on. His group also authors [[@schwarke2025rsl|RSL-RL]], a library that pipeline uses.
- **Perceptive / terrain-aware locomotion** ([[@miki2022learning]], [[@grandia2023perceptive]],
  [[@jenelten2024dtc|DTC]], [[@he2025attention]], [[@zhang2026ame|AME-2]]) is the closest external
  analogue to [[@terrain2026consistent]] — same goal of terrain-conditioned locomotion.
- **Contrast (the payoff):** RSL leans on **data-driven generality** — end-to-end learned or MPC
  controllers for quadrupeds, scaling perception and simulation. My line (Ames lab) injects
  **control-theoretic structure** — [[control-lyapunov-function]] rewards, [[reduced-order-model]]
  references, [[control-barrier-function]] safety — into RL for humanoids/hoppers, aiming at
  *certifiable* stability rather than emergent robustness. Same target
  ([[rl-for-legged-locomotion|robust perceptive locomotion]]), opposite ends of the
  structure-vs-scale axis. See [[learning-based-locomotion]].

## In otto — authored works
_Papers already in the vault that he (co-)authored:_

- **Massively-parallel RL locomotion:** [[@rudin2021learning]] · [[@hwangbo2019learning]] · [[@schwarke2025rsl]]
- **Perceptive locomotion:** [[@miki2022learning]] · [[@grandia2023perceptive]] · [[@jenelten2024dtc]]
- **Attention / neural map encoding:** [[@he2025attention]] · [[@zhang2026ame]]
- **Learned navigation:** [[@hoeller2021learning]] · [[@lee2024learning]] · [[@haro2026path]] · [[@yang2025spatially]] · [[@roth2025learned]]
- **MPC / whole-body:** [[@galliker2022planar]]

## Elsewhere (non-paper)
- Lab: [Robotic Systems Lab, ETH Zurich](https://rsl.ethz.ch/)
- Companies: [ANYbotics](https://www.anybotics.com/) · Gravis Robotics · SwissMile · [RAI Institute](https://rai-inst.com/)
- Press: ["How robots learn to hike," ETH Zurich](https://ethz.ch/en/news-and-events/eth-news/news/2022/01/how-robots-learn-to-hike.html)
- Profiles: [Google Scholar](https://scholar.google.com/citations?user=DO3quJYAAAAJ) · [edX bio](https://www.edx.org/bio/marco-hutter)

## Sources
- ETH Zurich / RSL and NCCR pages; edX bio; ETH News "How robots learn to hike" (2022); Google Scholar. Bio drafted 2026-07-06 — confirm details before citing.
