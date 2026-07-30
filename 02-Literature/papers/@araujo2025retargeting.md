---
type: paper
citekey: araujo2025retargeting
tags: [imitation, locomotion, method]
aliases: [GMR, General Motion Retargeting, Retargeting Matters]
created: 2026-07-29
modified: 2026-07-29
authors:
- Araújo, João Pedro
- Ze, Yanjie
- Xu, Pei
- Wu, Jiajun
- Liu, C. Karen
year: 2025
venue: arXiv preprint (ICRA 2026)
doi: 10.48550/arXiv.2510.02252
arxiv: '2510.02252'
url: https://arxiv.org/abs/2510.02252
pdf: attachments/@araujo2025retargeting.pdf
zotero: null
status: to-read
mine: false
---

# Retargeting Matters: General Motion Retargeting for Humanoid Motion Tracking

> [!info] Araújo, João Pedro; Ze, Yanjie; Xu, Pei; Wu, Jiajun; Liu, C. Karen · 2025 · arXiv preprint, ICRA 2026
> [Website](https://jaraujo98.github.io/retargeting_matters) · **Code: [YanjieZe/GMR](https://github.com/YanjieZe/GMR)**

> [!note] AI-drafted reading note — read the full main text (§I–VI); tables read selectively. Refine into your own words. `## My notes` left for you.

## TL;DR
The **data-quality ablation** the humanoid motion-tracking literature was missing. Everyone retargets
human mocap to a robot and then trains RL to imitate it — but retargeting injects artifacts (foot
sliding, ground penetration, self-intersection), and the standard practice is to let reward
engineering and domain randomization paper over them. This paper *suppresses* the reward tuning and
asks what retargeting quality is actually worth. Answer: it matters, sometimes decisively. Plus a new
open-source retargeter, **GMR**, that closes most of the gap to Unitree's closed-source pipeline.

This is the retargeter **both [[@luo2025sonic|SONIC]] and [[@xie2026grail|GRAIL]] use**.

## Problem
The embodiment gap: 3D human motion data is the fuel for humanoid learning, but a human skeleton isn't
a G1. Kinematic retargeting bridges it, and the artifacts it introduces get pushed downstream — the RL
policy is asked to imitate physically infeasible motion *while* satisfying physical constraints. Prior
work shows this is trainable in sim but that real-world transfer then "demands extensive trial-and-error,
reward shaping, and parameter tuning."

The authors' hypothesis, stated plainly: **with enough reward engineering and domain randomization,
retargeting artifacts can be mostly hidden — so the question is what happens without them.**

## Method
### The evaluation design (the actually clever part)
Train tracking policies with **[[@liao2025beyondmimic|BeyondMimic]]**, chosen precisely because it
needs *no reward tuning* and was developed independently of every retargeter under test. That isolates
retargeting quality as the only variable. Four retargeters compared:
- **PHC** (via H2O/[[@luo2023perpetual|PHC]] codebase) — fits SMPL shape params to the robot skeleton,
  then gradient-descent IK (Adam + Adadelta) on joint position error. Doesn't model **contact state**
  during retargeting → floating, foot sliding, floor penetration. Slow, so not real-time viable.
- **ProtoMotions** — global axis-aligned scaling + differential IK (Mink) on weighted position/orientation error.
- **GMR** (theirs) — **non-uniform local scaling**, then a two-stage optimization. Scaling is identified
  as the root cause of most artifacts in the other two.
- **Unitree** — closed-source, proprietary; included as the quality ceiling.

21 LAFAN1 sequences (5 s to 2 min), walking through martial arts, kicks, dancing; motions with non-foot
contact excluded. Strict success = complete the reference *in its entirety*. Evaluated 100× without
domain randomization, **4096× with**, plus sim2sim in MuJoCo, plus a 20-participant user study on
perceptual faithfulness to the source motion.

## Key results
**Q1 — does retargeting choice matter? Yes.** Policies trained on PHC/ProtoMotions data show
considerably higher global and local tracking error, and for long dance sequences retargeted with PHC
the motion became effectively **impossible to learn**. Most motions track under any retargeter, but
robustness degrades — "particularly for dynamic or long sequences."

**Q2 — which artifacts are fatal?** Three, named explicitly:
- **physically inconsistent height / ground penetration** (PHC on "Dance 1": up to **60 cm**)
- **self-intersection** (ProtoMotions on "Run (stop & go)": legs intersecting)
- **sudden jumps in joint values** (GMR's own failure on "Dance 5": waist-roll jumps — they report their
  own artifact, from the optimization phase, on <2% of the dataset)

**Q3 — faithfulness.** Users (N=20) rate GMR more faithful than PHC and ProtoMotions; Unitree is rated
more faithful than GMR, but users **struggle to tell the two apart**. Combined with the success rates,
that's the paper's claim that GMR is a viable open substitute for proprietary retargeting.

**The finding that's easy to miss:** the **starting frame** of the reference motion can dominate
everything else. Same policy, same motion, different start frame: "Turn 1" goes from **14% → 100%**
(PHC) and **47% → 100%** (Unitree) in sim2sim. Recommendation: ensure the start pose is one the robot
can safely reach at inference onset, and end on a stable pose for safe deactivation.

## Limitations / open questions
- Scope is deliberately narrow: **no object or complex scene interaction** (crawling and floor get-ups
  excluded; one cartwheel admitted because hands and feet are never both down).
- GMR uses **one set of optimization weights for all motions**; they acknowledge some motions would need
  per-motion weight tuning — i.e. the tuning burden is reduced, not eliminated.
- Conclusions are entangled with BeyondMimic as the training pipeline; a different tracker might mask or
  amplify different artifacts.

> [!question] My reading — inferred, not claimed by the paper
> This is the most **methodologically careful** paper in the SONIC/GRAIL cluster, and it's the only one
> that treats "how much of our result is reward engineering?" as an empirical question rather than an
> embarrassment. Worth reading for the experimental design alone.
> - It quietly undercuts a premise the scaling papers depend on. [[@luo2025sonic|SONIC]]'s pitch is
>   "dense supervision, **no reward engineering**" — but SONIC's supervision is GMR output, and this
>   paper shows tracking success is *sensitive to retargeting artifacts* when reward tuning is
>   suppressed. So the reward engineering didn't disappear; some of it moved upstream into the
>   retargeter's objective and scaling heuristics.
> - The start-frame result (14% → 100% on the same policy) is a **reachability** condition on the
>   reference, which is very close to something you could state properly: the reference trajectory must
>   begin in the policy's region of attraction. That's a [[control-lyapunov-function]]-shaped statement
>   sitting unnoticed in an empirical robotics paper — plausibly the cleanest bridge in this whole
>   cluster to your line. Flagged as *my* framing, not theirs.

## Concepts
- [[motion-imitation]] — the data-preparation stage the entire lineage depends on and rarely examines.
- [[sim-to-real-transfer]] — 4096-rollout domain-randomized evaluation + MuJoCo sim2sim; artifacts
  surface as transfer failures, not sim failures.
- Related notes worth linking once read: [[tracking-error-bound]] (the start-frame/reachability point).

## My notes
<!-- Your own reactions; how it relates to your work. -->

## Source
- arXiv: https://arxiv.org/abs/2510.02252 (v1, 2 Oct 2025, ICRA 2026)
- DOI: https://doi.org/10.48550/arXiv.2510.02252
- Code: https://github.com/YanjieZe/GMR · Website: https://jaraujo98.github.io/retargeting_matters
- Full text read from `attachments/@araujo2025retargeting.pdf` (§I–VI; Tables I–III read selectively).
