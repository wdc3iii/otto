---
type: paper
citekey: long2025learning
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-06'
authors:
- Long, Junfeng
- Ren, Junli
- Shi, Moji
- Wang, Zirui
- Huang, Tao
- Luo, Ping
- Pang, Jiangmiao
year: 2025
venue: 2025 IEEE International Conference on Robotics and Automation (ICRA)
doi: null
arxiv: '2411.14386'
url: https://arxiv.org/abs/2411.14386
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@long2025learning.pdf
bibkeys:
- long2025learning
- longLearningHumanoidLocomotion2024
---

# Learning humanoid locomotion with perceptive internal model

> [!info] Long, Junfeng; Ren, Junli; Shi, Moji; Wang, Zirui; Huang, Tao; Luo, Ping · 2025 · 2025 IEEE International Conference on Robotics and Automation (ICRA)

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — The Perceptive Internal Model (PIM) gives a humanoid stable perceptive locomotion by feeding an onboard, continuously updated robot-centric elevation map into an internal-model RL policy, enabling reliable stair climbing across robots and terrains with minimal added compute.
**Problem** — Unlike quadrupeds, which can traverse terrain with a "blind" policy, humanoids' high DoF and unstable morphology demand accurate perception for stable locomotion; but naively adding perceptual signals injects disturbances that hurt robustness, generalization, and efficiency.
**Method** — Rather than encoding raw depth maps or point clouds, PIM samples terrain heights from a constructed local elevation map. The policy is trained on ground-truth surrounding obstacle heights in simulation and optimized under the Hybrid Internal Model (HIM), then run at inference on elevation-map-sampled heights. Skipping depth rendering keeps sim cheap — policy training in ~3 hours on one RTX 4090.
**Key results** — Enables continuous stair climbing; validated across multiple humanoid robots, indoor/outdoor terrains, stairs, and sensor configurations.

## Takeaways
- Elevation-map heights (vs. raw depth/point clouds) let the robot see the terrain under its feet cleanly and stay robust to camera motion/noise — a representation choice, not just more sensing.
- Coupling perception to a Hybrid Internal Model formulation is the mechanism that keeps added perception from degrading robustness.
- Cheap to train (no depth rendering in sim; ~3 h on one GPU), positioning it as a foundational perceptive-locomotion recipe.

## Relevance to your work
A perceptive-locomotion reference for [[@terrain2026consistent]]: PIM's robot-centric elevation-map representation is a concrete design point for how terrain perception should be encoded for stable humanoid locomotion, directly informing consistent terrain-aware control.

## Concepts


## Source
- Cited by [[@terrain2026consistent]]
- bibkeys: `long2025learning`
