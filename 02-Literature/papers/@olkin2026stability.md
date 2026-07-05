---
type: paper
citekey: olkin2026stability
tags: [control, rl, locomotion]
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Olkin, Zachary
- Compton, William D.
- Ames, Aaron D.
year: 2026
venue: CDC 2026
doi: null
arxiv: null
url: null
zotero: null
status: read
mine: true
summary: ai-draft
pdf: attachments/@olkin2026stability.pdf
---

# Stability of Control Lyapunov Function Guided Reinforcement Learning

> [!info] Olkin, Zachary; Compton, William D.; Ames, Aaron D. · 2026 · CDC 2026 — **my paper**

## Abstract
Reinforcement learning (RL) has become the de facto method for achieving locomotion on humanoid robots in practice, yet stability analysis of the corresponding control policies is lacking. Recent work has attempted to merge control theoretic ideas with reinforcement learning through control guided learning. A notable example of this is the use of a control Lyapunov function (CLF) to synthesize the reinforcement learn- ing rewards, a technique known as CLF-RL, which has shown practical success. This paper investigates the stability properties of optimal controllers using CLF-RL with the goal of bridging experimentally observed stability with theoretical guarantees. The RL problem is viewed as an optimal control problem and exponential stability is proven in both continuous and discrete time using both core CLF reward terms and the additional Fig. 1. The main ideas behind CLF guided RL. A CLF is designed offline terms used in practice. The theoretical bounds are numerically and used in an RL/optimal control problem as the reward/cost. Then the verified on systems such as the double integrator and cart-pole. optimal policy, π ∗ is applied to the system resulting in provable exponential Finally, the CLF guided rewards are implemented for a walking stability and in stable humanoid locomotion. humanoid robot to generate stable periodic orbits.

## Summary
> [!note] AI-drafted from the abstract/intro — a base to refine or replace with your own framing.

**TL;DR** — Gives the **stability theory** behind CLF-RL (using a control Lyapunov function to shape RL rewards): views the RL problem as optimal control and proves exponential stability of the resulting policies.
**Problem** — RL is the de-facto method for humanoid locomotion but ships with little stability analysis; CLF-RL works in practice with no theoretical backing.
**Method** — Cast CLF-RL as an optimal control problem; prove exponential stability in both continuous and discrete time, for the core CLF reward term *and* the extra terms used in practice.
**Key results** — Bounds numerically verified on the double integrator and cart-pole; CLF-guided rewards produce stable periodic orbits on a walking humanoid.

## Takeaways
- Bridges "RL that works experimentally" with certifiable exponential stability.
- The practical reward terms (not just the idealized CLF term) are covered by the analysis.

## Where it sits in my work
The theory for your CLF-guided-RL line — the reward-shaping used in [[@olkin2026chasing|Chasing Autonomy]] and related to CLF rewards in [[@dai2025walk|Walk the PLANC]].

## Concepts
- _to add:_ control-lyapunov-function, clf-guided-rl, exponential-stability

## References (in otto)
- [[@ames2014rapidly]]
- [[@dong2020principled]]
- [[@galloway2015torque]]
- [[@gu2025evolution]]
- [[@kajita20013d]]
- [[@li2026clf]]
- [[@liao2025beyondmimic]]
- [[@olkin2025chasing]]
- [[@olkin2026chasing]]
- [[@pratt2006capture]]
- [[@sleiman2026zest]]
- [[@sontag1989universal]]
- [[@wensing2024optimization]]
- [[@westenbroek2022lyapunov]]
- [[@westervelt2003hybrid]]
- [[@westervelt2018feedback]]
