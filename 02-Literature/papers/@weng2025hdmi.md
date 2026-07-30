---
type: paper
citekey: weng2025hdmi
tags: [imitation, rl, locomotion]
aliases: [HDMI, HumanoiD iMitation for Interaction]
created: 2026-07-29
modified: 2026-07-29
authors:
- Weng, Haoyang
- Li, Yitang
- Sobanbabu, Nikhil
- Wang, Zihan
- Luo, Zhengyi
- He, Tairan
- Ramanan, Deva
- Shi, Guanya
year: 2025
venue: arXiv preprint
doi: 10.48550/arXiv.2509.16757
arxiv: '2509.16757'
url: https://arxiv.org/abs/2509.16757
pdf: attachments/@weng2025hdmi.pdf
zotero: null
status: to-read
mine: false
---

# HDMI: Learning Interactive Humanoid Whole-Body Control from Human Videos

> [!info] Weng, Haoyang; Li, Yitang; Sobanbabu, Nikhil; Wang, Zihan; Luo, Zhengyi; He, Tairan; Ramanan, Deva; Shi, Guanya · 2025 · arXiv preprint (CMU)
> [Website](https://hdmi-humanoid.github.io) · One of GRAIL's two loco-manipulation baselines

> [!note] AI-drafted note — **partial read**: abstract, introduction, method design (§III), and headline real-world results. Method details and full ablations not read. Refine into your own words.

## TL;DR
Learn whole-body humanoid–object interaction **directly from monocular RGB video** — no mocap, no
teleoperation, no 3D asset pipeline. Extract and retarget human *and object* trajectories from
unconstrained video, train an RL policy to **co-track robot and object state**, deploy zero-shot on a
Unitree G1. Headline durability result: **67 consecutive door traversals (~34 min)** before failure,
plus 6 distinct real loco-manipulation tasks and 14 in simulation.

Read as the **video-native counterpoint** to [[@xie2026grail|GRAIL]]: same goal (robot-ready interaction
data at scale), opposite premise about whether you should control the scene beforehand.

## Problem
Whole-body humanoid–object interaction is hard for two compounding reasons: **motion data scarcity** and
the **contact-rich** nature of the task. Mocap of human–object interaction is expensive and
category-limited; teleoperation doesn't scale. Human video is abundant but gives you neither metric
object state nor a robot-executable trajectory.

## Method
Three stages:
1. **Data** — extract and retarget human *and object* trajectories from unconstrained monocular video
   into structured motion datasets.
2. **Policy** — RL that **co-tracks robot and object states**, with three stated design choices:
   - a **unified object representation** so one framework spans diverse objects (incl. articulated ones
     like doors and folding chairs)
   - a **residual action space** for stable exploration of challenging poses
   - a **general interaction reward** promoting robust, precise contact
3. **Deployment** — zero-shot sim-to-real onto a real humanoid.

## Key results
- **67 consecutive door traversals**, ~34 minutes of continuous operation, robust across different
  initial poses and terrain variations (with/without a wooden board). The door task is genuinely
  sequential: push the door open with a hand, walk through, turn around, kick it closed.
- **6 real-world** loco-manipulation tasks, **14 in simulation**.
- **The interaction reward is load-bearing**; the contact reward and contact-based termination are
  mostly not. Their own ablation (Fig. 6) reports that for most of 8 tasks, removing the contact reward
  and contact-based termination **does not affect final success rate** — a useful negative result, since
  contact rewards are near-universal in this literature.
- As GRAIL's baseline (124 motions / 43 objects): **48.5% SR**, ObjPos 0.283, MPJPE-L 122.3.

## Limitations / open questions
- GRAIL's stated caveats about it: HDMI **does not actuate per-finger DoFs** (interactions rely on
  whole-arm or whole-body contact), and it trains **one specialist policy per task**. Both are real
  scope limits, but they also mean GRAIL's headline comparison is across different problem settings.
- Full-text limitations section not read — **flagged, verify before citing.**

> [!question] My reading — inferred, not claimed by the paper
> The durability metric (67 consecutive trials, 34 min) is a different and arguably more useful claim
> than the single-trial success rates everything else in this cluster reports. Sustained closed-loop
> operation is what actually breaks on hardware, and nobody else here measures it.
> - The contact-reward negative result is worth taking seriously as evidence about **reward shaping**
>   generally: a term everyone includes turns out not to matter for most tasks. Cf. how
>   [[@araujo2025retargeting|GMR]] found reward engineering was hiding *data* problems.

## Concepts
- [[loco-manipulation]] · [[motion-imitation]] · [[sim-to-real-transfer]]

## My notes
<!-- Your own reactions; how it relates to your work. -->

## Source
- arXiv: https://arxiv.org/abs/2509.16757 (v3, Sep 2025) · DOI: https://doi.org/10.48550/arXiv.2509.16757
- Website: https://hdmi-humanoid.github.io
- Partial read from `attachments/@weng2025hdmi.pdf`. Baseline numbers cross-read from [[@xie2026grail]] Tab. 2.
