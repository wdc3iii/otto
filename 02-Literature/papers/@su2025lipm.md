---
type: paper
citekey: su2025lipm
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Su, Haokai
- Luo, Haoxiang
- Yang, Shunpeng
- Jiang, Kaiwen
- Zhang, Wei
- Chen, Hua
year: 2025
venue: 2025 IEEE-RAS 24th International Conference on Humanoid Robots (Humanoids)
doi: null
arxiv: '2509.09106'
url: https://arxiv.org/abs/2509.09106
zotero: null
summary: ai-draft
pdf: attachments/@su2025lipm.pdf
status: to-read
mine: false
bibkeys:
- su2025lipm
---

# LIPM-Guided Reinforcement Learning for Stable and Perceptive Locomotion in Bipedal Robots

> [!info] Su, Haokai; Luo, Haoxiang; Yang, Shunpeng; Jiang, Kaiwen; Zhang, Wei; Chen, Hua · 2025 · 2025 IEEE-RAS 24th International Conference on Humanoid Robots (Humanoids)

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — Uses the Linear Inverted Pendulum Model (LIPM) to shape RL rewards for stable, perceptive bipedal locomotion in the wild.
**Problem** — Learned perceptive locomotion policies struggle to stay dynamically balanced and to keep a stable camera viewpoint over rough terrain, where velocity tracking and stability can conflict.
**Method** — Derives a LIPM-inspired reward that regulates CoM height and torso orientation for dynamic balance and a steady perceptual viewpoint; a Reward Fusion Module adaptively trades velocity tracking against stability, and a double-critic architecture evaluates stability and locomotion objectives separately.
**Key results** — Simulation and real-world outdoor experiments on a bipedal robot show superior terrain adaptability, disturbance rejection, and consistent performance across a range of speeds and perceptual conditions (no numeric figures read).

## Takeaways
- The LIPM here is a *reward-shaping prior*, not a planner — a reduced-order model injected into RL rather than a model-based controller.
- Regulating torso orientation explicitly for a stable camera viewpoint couples locomotion stability with perception quality — a useful framing for perceptive legged control.
- Double-critic + adaptive reward fusion is the mechanism for resolving the classic velocity-vs-stability reward conflict.

## Relevance to your work
Directly relevant to perceptive humanoid locomotion (cited by [[@terrain2026consistent]]): it shows how a reduced-order template like the LIPM can guide learned policies toward provable-ish balance behavior and a stable sensing viewpoint.

## Concepts
[[reduced-order-model]]

## Source
- Cited by [[@terrain2026consistent]]
- bibkeys: `su2025lipm`
