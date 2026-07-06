---
type: paper
citekey: rudin2022advanced
tags: [locomotion, navigation, rl]
aliases: []
created: '2026-07-06'
modified: '2026-07-06'
authors:
- Rudin, Nikita
- Hoeller, David
- Bjelonic, Marko
- Hutter, Marco
year: 2022
venue: arXiv
doi: 10.48550/arXiv.2209.12827
arxiv: '2209.12827'
url: http://arxiv.org/abs/2209.12827
zotero: null
summary: ai-draft
pdf: attachments/@rudin2022advanced.pdf
status: to-read
mine: false
bibkeys:
- rudinAdvancedSkillsLearning2022
---

# Advanced Skills by Learning Locomotion and Local Navigation End-to-End

> [!info] Nikita Rudin; David Hoeller; Marko Bjelonic; Marco Hutter · 2022 · arXiv

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — Trains a single end-to-end RL policy for combined locomotion and local navigation, replacing the plan/follow/track pipeline with a position-goal-within-a-time-budget task that unlocks richer emergent behaviors.
**Problem** — The standard legged local-navigation stack (path planning → path following → velocity-tracking locomotion) decomposes into sub-tasks that each ignore the full solution space, limiting the robot's capabilities.
**Method** — Solve the whole problem with one end-to-end deep RL policy. Instead of tracking a precomputed path, the robot must reach a target position within a provided time; success is evaluated only at episode end, so the policy is free to choose its own path and gait. The paper argues the time dependence of the reward is critical to learning these behaviors.
**Key results** — Compared against velocity tracking; deployed on a real quadruped that crosses previously-infeasible challenging terrain with a more energy-efficient gait and higher success rate (no numeric figures read).

## Takeaways
- Reframing local navigation as "reach a position within a time budget," evaluated only at episode end, expands the solution space vs. continuous path tracking.
- Time-dependence of the reward is identified as the critical ingredient for learning the new behaviors.
- End-to-end training lets the policy jointly pick path and gait, yielding more energy-efficient, higher-success traversal.

## Relevance to your work
Central to capability-aware navigation: this is the end-to-end alternative to the hierarchical plan/follow/track decomposition you work with. The time-budgeted position-goal formulation is a concrete contrast point for how much to fold navigation into the locomotion policy on the G1.

## Abstract (from bib)
The common approach for local navigation on challenging environments with legged robots requires path planning, path following and locomotion, which usually requires a locomotion control policy that accurately tracks a commanded velocity. However, by breaking down the navigation problem into these sub-tasks, we limit the robot's capabilities since the individual tasks do not consider the full solution space. In this work, we propose to solve the complete problem by training an end-to-end policy with deep reinforcement learning. Instead of continuously tracking a precomputed path, the robot needs to reach a target position within a provided time. The task's success is only evaluated at the end of an episode, meaning that the policy does not need to reach the target as fast as possible. It is free to select its path and the locomotion gait. Training a policy in this way opens up a larger set of possible solutions, which allows the robot to learn more complex behaviors. We compare our approach to velocity tracking and additionally show that the time dependence of the task reward is critical to successfully learn these new behaviors. Finally, we demonstrate the successful deployment of policies on a real quadrupedal robot. The robot is able to cross challenging terrains, which were not possible previously, while using a more energy-efficient gait and achieving a higher success rate.

## Concepts
- [[rl-for-legged-locomotion]]
- [[hierarchical-control]]
- [[mapless-navigation]]

## Source
- bibkeys: `rudinAdvancedSkillsLearning2022`
- arXiv: http://arxiv.org/abs/2209.12827
- DOI: https://doi.org/10.48550/arXiv.2209.12827
- URL: http://arxiv.org/abs/2209.12827
