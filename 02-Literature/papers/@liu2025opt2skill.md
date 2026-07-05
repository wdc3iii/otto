---
type: paper
citekey: liu2025opt2skill
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Liu, Fukang
- Gu, Zhaoyuan
- Cai, Yilin
- Zhou, Ziyi
- Jung, Hyunyoung
- Jang, Jaehwi
- Zhao, Shijie
- Ha, Sehoon
- Chen, Yue
- Xu, Danfei
- others
year: 2025
venue: IEEE Robotics and Automation Letters
doi: null
arxiv: '2409.20514'
url: https://arxiv.org/abs/2409.20514
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@liu2025opt2skill.pdf
bibkeys:
- liu2025opt2skill
---

# Opt2skill: Imitating dynamically-feasible whole-body trajectories for versatile humanoid loco-manipulation

> [!info] Liu, Fukang; Gu, Zhaoyuan; Cai, Yilin; Zhou, Ziyi; Jung, Hyunyoung; Jang, Jaehwi · 2025 · IEEE Robotics and Automation Letters

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — Opt2Skill is an end-to-end pipeline that uses model-based trajectory optimization to generate dynamically feasible, contact-consistent whole-body reference motions and then trains RL policies to track them, yielding robust versatile humanoid loco-manipulation on the Digit robot.
**Problem** — Model-based optimal control gives precise, physically meaningful motion but is computationally heavy and needs accurate contact sensing; RL is robust in high-dimensional spaces but suffers inefficient learning, unnatural motion, and sim-to-real gaps. Neither alone handles contact-rich humanoid loco-manipulation well.
**Method** — Differential dynamic programming (DDP) produces dynamically feasible, contact-consistent reference trajectories for Digit; RL policies are trained to track these references. Including torque information in the references improves contact-force tracking on contact-heavy tasks (e.g., wiping a table).
**Key results** — Outperforms baselines that rely on human demonstrations and IK-based references in both motion-tracking accuracy and task success; torque-aware references improve contact-force tracking; transferred to real hardware.

## Takeaways
- Optimization-generated references beat human-demo / IK references precisely because they are dynamically feasible and contact-consistent — the RL policy tracks something the robot can actually do.
- Carrying torque (not just kinematics) into the reference is what unlocks contact-force tracking on manipulation tasks.
- A clean instance of the "plan with a model, track with RL" division of labor for whole-body humanoid control.

## Relevance to your work
Directly relevant to [[@dai2025walk]]: it exemplifies the model-based-plan / RL-track architecture for humanoid loco-manipulation, using trajectory optimization to supply dynamically feasible references that an RL policy learns to track on hardware.

## Concepts
[[hierarchical-control]]

## Source
- Cited by [[@dai2025walk]], [[@terrain2026consistent]]
- bibkeys: `liu2025opt2skill`
