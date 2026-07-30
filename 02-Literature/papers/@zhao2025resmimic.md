---
type: paper
citekey: zhao2025resmimic
tags: [imitation, rl, locomotion]
aliases: [ResMimic]
created: 2026-07-29
modified: 2026-07-29
authors:
- Zhao, Siheng
- Ze, Yanjie
- Wang, Yue
- Liu, C. Karen
- Abbeel, Pieter
- Shi, Guanya
- Duan, Rocky
year: 2025
venue: arXiv preprint
doi: 10.48550/arXiv.2510.05070
arxiv: '2510.05070'
url: https://arxiv.org/abs/2510.05070
pdf: attachments/@zhao2025resmimic.pdf
zotero: null
status: to-read
mine: false
---

# ResMimic: From General Motion Tracking to Humanoid Whole-Body Loco-Manipulation via Residual Learning

> [!info] Zhao, Siheng; Ze, Yanjie; Wang, Yue; Liu, C. Karen; Abbeel, Pieter; Shi, Guanya; Duan, Rocky · 2025 · arXiv preprint
> [Website](https://resmimic.github.io/) · GRAIL's other loco-manipulation baseline

> [!note] AI-drafted note — **partial read**: abstract, introduction, contributions, and framework overview. Full experiments and ablations not read. Refine into your own words.

## TL;DR
Take a **general motion tracking (GMT)** policy trained on human-only motion as a task-agnostic base,
then learn a **thin residual** on top that adds the precision and object-awareness that GMT lacks.
Two-stage residual learning, evaluated in sim and on a real Unitree G1.

Architecturally this is **the closest rival to [[@xie2026grail|GRAIL]]'s stage 3** — both keep a
pretrained whole-body controller and inject a learned correction rather than retraining. The difference
is *where* the correction enters: ResMimic adds a residual in **action** space; GRAIL adds a residual
in the controller's **quantized latent** space.

## Problem
Advances in general motion tracking let humanoids reproduce diverse human motion, but those policies
"lack the precision and object awareness required for loco-manipulation." The authors' framing: whole-body
movement generalizes across tasks, while only **fine-grained object interaction** needs adaptation —
which is exactly the structure residual learning is for.

## Method
Two stages:
1. **Base** — a GMT policy trained on large-scale human-only motion; task-agnostic, produces human-like
   whole-body movement.
2. **Residual** — an efficient, precise residual policy $\pi_{Res}$ (PPO) conditioned on object state,
   refining GMT's output to improve locomotion and incorporate object interaction.

Three training-efficiency devices, which are the paper's real contribution:
- a **point-cloud-based object tracking reward** for smoother optimization
- a **contact reward** encouraging accurate body–object contact
- a **curriculum-based virtual object controller** — a virtual force that warm-starts early training,
  then is annealed away

## Key results
- Reported substantial gains over strong baselines in **task success, training efficiency, and
  robustness**, in sim and on a real G1. Evaluated on human motion tracking, object motion tracking,
  task success, training efficiency, robustness, and generalization.
- As GRAIL's baseline (124 motions / 43 objects): **49.2% SR**, ObjPos 0.393, MPJPE-L 80.9.
- *Numbers from its own experiments not read* — **flagged.**

## Limitations / open questions
- GRAIL's stated caveats: **no per-finger DoF actuation**, and **one residual per task** — so it doesn't
  amortize across a motion family the way GRAIL's pooled trackers claim to.
- Full-text limitations not read — **verify before citing.**

> [!question] My reading — inferred, not claimed by the paper
> The action-space-vs-latent-space residual question is a real design fork worth resolving, and neither
> paper frames it as such. GRAIL's argument for the latent residual is implicit: it keeps the frozen
> decoder's learned motion prior intact (they add an $\ell_2$ penalty on the residual to enforce exactly
> that), whereas an action-space residual can in principle drive the robot anywhere the actuators allow.
> If that reasoning holds, the latent residual is the more *constrained* intervention — closer in spirit
> to a structured correction than an unconstrained one. Testable, and not tested by either paper.
> - "Virtual force curriculum then anneal" is the same shape as many reward-shaping schedules in
>   locomotion RL. Whether the annealed policy retains anything the virtual force taught it is not
>   something the abstract addresses.

## Concepts
- [[loco-manipulation]] · [[motion-imitation]] · [[sim-to-real-transfer]]

## My notes
<!-- Your own reactions; how it relates to your work. -->

## Source
- arXiv: https://arxiv.org/abs/2510.05070 (v2, Oct 2025) · DOI: https://doi.org/10.48550/arXiv.2510.05070
- Website: https://resmimic.github.io/
- Partial read from `attachments/@zhao2025resmimic.pdf`. Baseline numbers cross-read from [[@xie2026grail]] Tab. 2.
