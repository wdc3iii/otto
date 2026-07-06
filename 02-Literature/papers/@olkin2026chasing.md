---
type: paper
citekey: olkin2026chasing
tags: [rl, locomotion]
aliases: []
created: '2026-07-05'
modified: '2026-07-06'
authors:
- Olkin, Zachary
- Compton, William D.
- Bena, Ryan M.
- Ames, Aaron D.
year: 2026
venue: IROS 2026
doi: null
arxiv: null
url: null
zotero: null
status: read
mine: true
summary: ai-draft
pdf: attachments/@olkin2026chasing.pdf
---

# Chasing Autonomy: Dynamic Retargeting and Control Guided RL for Performant and Controllable Humanoid Running

> [!info] Olkin, Zachary; Compton, William D.; Bena, Ryan M.; Ames, Aaron D. · 2026 · IROS 2026 — **my paper**
> [!info]- otto authors: [[aaron-ames]] · [[ryan-bena]] · [[zachary-olkin]]

## Abstract
Humanoid robots have the promise of locomoting like humans, including fast and dynamic running. Recently, reinforcement learning (RL) controllers that can mimic human motions have become popular as they can generate very dynamic behaviors, but they are often restricted to single motion play-back which hinders their deployment in long duration and autonomous locomotion. In this paper, we present a pipeline to dynamically retarget human motions through an optimization routine with hard constraints to generate improved periodic reference libraries from a single human demonstration. We then study the effect of both the reference motion and the reward structure on the reference and commanded velocity tracking, concluding that a goal-conditioned and control-guided reward which tracks dynamically optimized human data results in the best performance. We deploy the policy on hardware, demonstrating its speed and endurance by achieving running speeds of up to 3.3 m/s on a Unitree G1 robot and traversing hundreds of meters in real-world environments. Additionally, to demonstrate the controllability of the locomotion, we use the controller in a full perception and planning autonomy stack for obstacle avoidance while running outdoors.

## Summary
> [!note] AI-drafted from the abstract/intro — a base to refine or replace with your own framing.

**TL;DR** — A pipeline for **performant, controllable humanoid running**: dynamically retarget a single human demo into optimized periodic reference libraries, then train a goal-conditioned, control-guided RL policy that tracks them.
**Problem** — RL motion-mimicking gives dynamic behaviors but is often locked to single-clip playback, hindering long-duration, controllable, autonomous locomotion.
**Method** — Optimization with hard constraints retargets human motion into improved periodic references; ablates reference vs. reward structure, finding a goal-conditioned + control-guided reward on dynamically-optimized human data works best.
**Key results** — On a **Unitree G1**: running up to **3.3 m/s**, hundreds of meters outdoors; integrated into a full perception+planning autonomy stack for obstacle avoidance while running.

## Autonomy stack — CBF-constrained MPC safety filter
*(verified from §V-C, not just the abstract)* On top of the frozen running controller sits an
**MPC layer that generates its velocity commands** for real-time collision avoidance:
- Real-time **LiDAR** scans build/update a local occupancy map, from which a smooth
  **[[poisson-safety-function|Poisson safety function]]** is synthesized ([[@bena2025geometry]]).
- That PSF becomes a **[[control-barrier-function|CBF]] collision-avoidance constraint along the MPC
  horizon**; the loop (1) characterizes the environment, (2) re-plans, (3) updates the running
  command. Odometry from FastLIO at 10 Hz — all computation onboard.
- Sustains **~2 m/s** forward running while dodging detected obstacles outdoors.

This is what makes the running *autonomous* (vs. remote velocity feedforward), and it is the **same
PSF → CBF-MPC safety-filter-over-a-frozen-LLC pattern** as the safety tier of my
[[capability-aware-navigation]] project.

## Takeaways
- Retargeting-in-the-loop + control-guided rewards beat raw motion playback for controllable speed tracking.
- Exposes a clean command interface, making the runner usable inside a navigation stack.

## Where it sits in my work
Applies the CLF-guided-RL stability ideas of [[@olkin2026stability]]; the controllable-locomotion-for-autonomy goal is shared with [[@terrain2026consistent]]. **Distinct from [[@olkin2025chasing|Chasing Stability]]** (the CLF-RL *running* paper): Chasing Autonomy adds the dynamic human-motion **retargeting** front-end *and* the **CBF-MPC safety-filter autonomy stack** on top of the runner. Part of [[navigation-autonomy]].

## Concepts
- [[rl-for-legged-locomotion]] · [[control-lyapunov-function]] · [[poisson-safety-function]] · [[control-barrier-function]] · [[massively-parallel-simulation]] · _to add:_ reference-guided-rl, motion-retargeting
- Maps: [[learning-based-locomotion]] · [[navigation-autonomy]]

## References (in otto)
—
