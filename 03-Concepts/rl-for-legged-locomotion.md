---
type: concept
tags: [rl, locomotion, to-revisit]
aliases: [RL for legged locomotion, learned locomotion, RL locomotion, reinforcement learning for locomotion]
created: 2026-07-06
modified: 2026-07-06
---

# Reinforcement learning for legged locomotion

> [!note] AI-drafted base — refine into your own words, then drop `to-revisit`.

## Definition
Training a feedback control policy (typically an MLP) with **model-free deep RL** (usually PPO) in **massively parallel simulation** to map observations — proprioception, and optionally exteroception / terrain — to actuator commands, then transferring to hardware via **domain randomization**. It trades the explicit models and constraints of model-based control for robustness learned from billions of simulated transitions.

## Intuition / why it matters
RL policies are strikingly robust to disturbance and model error where model-based pipelines are brittle or intractable ([[@hwangbo2019learning]]). But *pure reward-shaped, end-to-end* RL struggles with three things that matter for real autonomy: **precise foothold placement** on discontinuous terrain, **certifiable stability**, and a **clean interface** a planner can drive. The productive response is to **inject structure** rather than hand-tune rewards — which is exactly the [[reduced-order-model|ROM]]- and [[control-lyapunov-function|CLF]]-guided line below.

## Key design axes
- **Reward design:** heuristic shaping vs. *structured* rewards (e.g. a [[control-lyapunov-function|CLF]] reward that certifies convergence instead of being hand-tuned).
- **Guidance / references:** environment-agnostic vs. **reference-guided** (a ROM or motion prior supplies dynamically-consistent targets the policy tracks).
- **Perception:** blind (proprioceptive) vs. **perceptive** (terrain-conditioned) policies.
- **Interface:** raw velocity vs. an **$SE(2)$-controllable** policy that plugs into a standard navigation stack.

## The CLF-guided RL thread (my line)
Use a [[control-lyapunov-function]] to *shape the reward*, so the policy is guided toward provable stability rather than through reward tuning — and modulate the reference to the terrain so the resulting policy is both perceptive and planner-compatible.
- [[@dai2025walk|PLANC]] — ROM stepping planner + CLF rewards for constrained-foothold stepping.
- [[@olkin2026stability]] — *why* CLF-guided RL is stable (the theory).
- [[@olkin2026chasing]] — dynamic retargeting + control-guided RL for controllable running.
- [[@terrain2026consistent]] — terrain-consistent references + CLF-RL, exposing an $SE(2)$ interface for navigation autonomy.
- Related outside work: [[@li2025clf|CLF-RL]], [[@su2025lipm|LIPM-guided RL]].

## Grounding
- Foundations & infra: [[@hwangbo2019learning]] · [[@mittal2025isaac|Isaac Lab]] · [[@schwarke2025rsl|RSL-RL]] — see [[massively-parallel-simulation]].
- Perceptive/terrain-aware: [[@long2025learning]] · [[@he2025attention]] · [[@zhang2026rpl]] · [[@zhuang2024humanoid]] · [[@wangndbeamdojo]].
- Reference/imitation ([[motion-imitation]]): [[@liao2025beyondmimic]] · [[@lee2024integrating]] · [[@bang2024rl]].
- Navigation policies (RL over a locomotion controller): [[@wang2026guide]] — end-to-end goal-initialized nav; its 50 Hz low-level controller follows [[@long2025learning]]. See [[recurrent-navigation-policy]]: [[@yang2025spatially]] (SRU) · [[@lee2024learning]] (km-scale HRL) · [[@zhang2026focusnav]] (humanoid G1). The [[capability-aware-navigation]] project layers a nav policy over a *frozen* [[control-lyapunov-function|CLF-RL]] locomotion controller.
- Full literature map: [[learning-based-locomotion]].

## Related
- [[control-lyapunov-function]] · [[reduced-order-model]] · [[massively-parallel-simulation]] · [[control-barrier-function]] · [[hierarchical-control]] · [[motion-imitation]]

## Open questions
- **Certifiable stability** for learned policies — [[@olkin2026stability]] is a first answer; how far does it generalize?
- Closing the **sim-to-real** gap for contact-rich, discontinuous terrain.
- The right **abstraction/interface** between a learned low-level policy and a high-level planner (why $SE(2)$-controllability matters).
