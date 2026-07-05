---
type: paper
citekey: wu2026perceptive
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Wu, Zhen
- Huang, Xiaoyu
- Yang, Lujie
- Zhang, Yuanhang
- Sreenath, Koushil
- Chen, Xi
- Abbeel, Pieter
- Duan, Rocky
- Kanazawa, Angjoo
- Sferrazza, Carmelo
- others
year: 2026
venue: arXiv preprint arXiv:2602.15827
doi: null
arxiv: '2602.15827'
url: https://arxiv.org/abs/2602.15827
zotero: null
summary: ai-draft
pdf: attachments/@wu2026perceptive.pdf
status: to-read
mine: false
bibkeys:
- wu2026perceptive
---

# Perceptive humanoid parkour: Chaining dynamic human skills via motion matching

> [!info] Wu, Zhen; Huang, Xiaoyu; Yang, Lujie; Zhang, Yuanhang; Sreenath, Koushil; Chen, Xi · 2026 · arXiv preprint arXiv:2602.15827

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — PHP lets a humanoid perform vision-based parkour by chaining dynamic human skills via motion matching, then distilling into a single depth-sensing policy.
**Problem** — Enabling humanoids to autonomously select and execute diverse dynamic parkour skills (step over, climb, vault, roll off) from onboard perception alone, while preserving natural motion fluidity.
**Method** — Uses motion matching — nearest-neighbor search in a feature space — to compose human motion skills into extended kinematic trajectories; trains RL experts on the composed motions and distills them into a single depth-sensing policy via DAgger and RL, so the robot makes context-aware obstacle decisions from onboard depth plus velocity commands.
**Key results** — Real-world validation on a Unitree G1 demonstrates highly dynamic parkour, including climbing obstacles up to 1.25 m (~96% of robot height) and multi-obstacle traversal with real-time adaptation to obstacle changes.

## Takeaways
- Motion matching (a game-animation technique) as a skill-composition prior for RL is the notable methodological import.
- Perception is fused with skill selection so a single depth policy chooses among qualitatively different behaviors — not a fixed gait.
- Validated on the Unitree G1, the same hardware family in your own work; 1.25 m climbing is an aggressive real-world capability claim.

## Relevance to your work
Directly on-point for perceptive humanoid locomotion on the G1 (cited by [[@terrain2026consistent]]): shows a perception-to-skill pipeline where consistent onboard terrain/depth sensing drives context-dependent dynamic maneuvers.

## Concepts
<!-- [[03-Concepts]] links added when read -->

## Source
- Cited by [[@terrain2026consistent]]
- bibkeys: `wu2026perceptive`
- arXiv: https://arxiv.org/abs/2602.15827
