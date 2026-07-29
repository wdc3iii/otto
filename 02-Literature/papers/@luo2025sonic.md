---
type: paper
citekey: luo2025sonic
tags: [imitation, foundation-model, rl]
aliases: [SONIC]
created: 2026-07-29
modified: 2026-07-29
authors:
- Luo, Zhengyi
- Yuan, Ye
- Wang, Tingwu
- Li, Chenran
- Castañeda, Fernando
- Chen, Sirui
- Cao, Zi-Ang
- Li, Jiefeng
- Minor, David
- Ben, Qingwei
- Park, Jinhyung
- Sami, David
- Wang, Zi
- Da, Xingye
- Ding, Runyu
- Hogg, Cyrus
- Song, Lina
- Lim, Edy
- Jeong, Eugene
- He, Tairan
- Xue, Haoru
- Xiao, Wenli
- Yuen, Simon
- Kautz, Jan
- Chang, Yan
- Iqbal, Umar
- Fan, Linxi
- Zhu, Yuke
year: 2025
venue: arXiv preprint
doi: 10.48550/arXiv.2511.07820
arxiv: '2511.07820'
url: https://arxiv.org/abs/2511.07820
pdf: attachments/@luo2025sonic.pdf
zotero: null
status: to-read
mine: false
---

# SONIC: Supersizing Motion Tracking for Natural Humanoid Whole-Body Control

> [!info] Luo, Zhengyi; Yuan, Ye; Wang, Tingwu; Li, Chenran; Castañeda, Fernando; Chen, Sirui; Cao, Zi-Ang; Li, Jiefeng; Minor, David; Ben, Qingwei; Park, Jinhyung; Sami, David; Wang, Zi; Da, Xingye; Ding, Runyu; Hogg, Cyrus; Song, Lina; Lim, Edy; Jeong, Eugene; He, Tairan; Xue, Haoru; Xiao, Wenli; Yuen, Simon; Kautz, Jan; Chang, Yan; Iqbal, Umar; Fan, Linxi; Zhu, Yuke · 2025 · arXiv preprint (NVIDIA) · 28 authors
> [Project page](https://nvlabs.github.io/SONIC/) · **Code: [NVlabs/GR00T-WholeBodyControl](https://github.com/NVlabs/GR00T-WholeBodyControl)** · v1 Nov 2025, v3 May 2026 · journal-style format (Results / Materials and Methods)

> [!note] AI-drafted reading note from the full PDF — refine into your own words. `## My notes` left for you.

## TL;DR
The **scaling-laws paper for humanoid whole-body control**. The claim: *motion tracking* is the
right foundational task because mocap gives dense per-frame supervision with **no reward
engineering**, so it scales where locomotion rewards and adversarial imitation don't. Scaled along
three axes — 1.2M→42M parameters, 4M→**100M+ frames** (611 h of mocap), 2K→**21K GPU hours** (128
GPUs, 7 days) — a single policy reaches 99.6% tracking success on out-of-distribution motion, runs
**fully onboard a Jetson Orin at 50 Hz**, and exposes a quantized **universal token space** that VR
teleop, video/text/music generators, and a GR00T N1.5 VLA all drive through one unchanged controller.

This is the pretrained controller [[@xie2026grail|GRAIL]] builds on.

## Problem
Humanoid control hasn't scaled while everything else in AI has. The authors diagnose **task
selection** as the root cause, not architecture:
- **Reward-engineered locomotion** — walking forward gives no signal for dancing, getting up, or
  teleoperation. Every capability needs a redesigned objective, so effort grows linearly with skills.
- **Adversarial imitation** (AMP, ASE, CALM) unifies the objective but the discriminator's job gets
  *harder* as the dataset diversifies → documented **mode collapse** at scale.
- **Prior motion trackers** mostly report tracking on training data and demonstrate little downstream
  beyond navigation.

Second, separate problem: even a scalable objective needs to *serve* heterogeneous task
specifications — teleop, goal-directed navigation, vision-language commands — without retraining.

## Method
### The scalable task: motion tracking with dense supervision
PPO in Isaac Lab, MDP formulation adapted from [[@liao2025beyondmimic|BeyondMimic]]'s environment
settings. State = 10-step history of proprioception $(q_t, \dot q_t, \omega_t, g_t, a_{t-1})$ + a
motion command, all in the robot's local frame, 6D rotation representation. Actions = target joint
positions tracked by PD control. Reward = tracking terms (root pose, link positions/orientations
relative to root, link velocities) + an explicit **end-effector** term (head, wrists, ankles) +
anti-shake and foot-acceleration penalties. Asymmetric actor-critic — the critic sees privileged sim
state, the actor only deployment-available observations.

### The universal token space (the systems contribution)
Three specialized MLP encoders map heterogeneous commands into one shared latent:
- $\mathcal{E}^r$ **robot motion** — joint positions/velocities over $F_r$ future frames
- $\mathcal{E}^h$ **human motion** — 3D SMPL joint positions over $F_h$ future frames
- $\mathcal{E}^m$ **hybrid** — sparse current-frame upper-body keypoints (head, hands) + future
  lower-body robot motion (this is what makes real-time 3-point teleop work)

The latent is quantized by **FSQ** (two tokens, $D_z$ dims, $L_z$ levels) — chosen over VQ-VAE
because it avoids codebook collapse, needs no commitment loss or EMA updates, and gives clean
straight-through gradients **compatible with joint PPO optimization**. Two decoders: a robot *control*
decoder $\mathcal{D}^c(z, s^p_t) \to a_t$, and an auxiliary robot *motion* decoder
$\mathcal{D}^r(z) \to \hat g_r$ that doubles as an **implicit human→robot retargeting module**.

Trained end-to-end with four jointly optimized losses:
$$\mathcal{L} = \mathcal{L}_{ppo} + \mathcal{L}_{recon} + \mathcal{L}_{token} + \mathcal{L}_{cycle}$$
- $\mathcal{L}_{recon}$ — each modality's token must reconstruct the *robot* command; when the input is
  human motion this **is** the retargeting loss, which is how the system learns from human data directly
- $\mathcal{L}_{token}$ — pairwise alignment across all three encoders (same motion → same token)
- $\mathcal{L}_{cycle}$ — $\|\mathcal{E}^r(\mathcal{D}^r(z_h)) - z_r\|^2$, human→robot→human coherence

PPO updates encoders/quantizer/control decoder; the auxiliary losses update encoders/quantizer/motion
decoder. The authors explicitly report **no instability** from coupling quantization with RL at any
model scale. Bin-based adaptive motion sampling weights by capped failure rate.

### Dataset
~700 h of commercial mocap → retargeted to the Unitree G1 via **GMR** + PyRoki → **611 h / 100M+
frames at 50 Hz**, 317,189 clips, 8,447 unique sub-categories across 33 categories (locomotion, dance,
gestures, combat, props/object manipulation, tool use, injured gait, stylistic variants, roleplay).
Held-out splits are the careful part: **test-content** (6,998 clips, 182 sub-categories *entirely
absent* from training) vs. **test-repetition** (6,306 clips, new takes of known types).

> [!important] Actionable for you — public data + code
> A large portion is released as **BONES-SEED** on Hugging Face: 142,220 sequences / 288 h / 522
> actors, **already in Unitree G1 format**, with language descriptions and temporal segmentation.
> Code at `NVlabs/GR00T-WholeBodyControl`. This is a G1-ready mocap corpus you could pull directly.

### Kinematic planner + deployment
A separate large latent generative model does autoregressive motion **in-betweening**: generates
0.8–2.4 s segments (duration chosen by the planner), replans every 100 ms or on command change,
**<5 ms on a laptop / 12 ms on a Jetson Orin**. Velocity commands 0–6 m/s and arbitrary heading,
filtered by a critically damped spring model.

Deployment on a G1 (29 actuated joints): **all inference onboard a Jetson Orin** via TensorRT + CUDA
graphs, 1–2 ms per policy forward pass. Multi-rate: policy 50 Hz, command streaming 500 Hz, operator
input 100 Hz, kinematic planning 10 Hz. Switching interface = switching the active encoder, no retraining.

## Key results
**Scaling holds on all three axes.** Largest model: **99.6% success / 23.8 mm MPJPE-L on test-content
(OOD)** vs. 98.0% / 27.7 mm for the 1.2M-parameter model. Gains are *most pronounced on OOD motions* —
the load-bearing claim, since it means scale buys generalization, not memorization. More GPUs give
better asymptotic performance at equal iteration count (larger batches → optimization stability).

**vs. other trackers** (all in MuJoCo, same termination criterion), success on
test-content / test-repetition / PHUMA:

| | test-content | test-rep. | PHUMA | MPJPE-L |
|---|---|---|---|---|
| Any2Track | 31.1% | 38.4% | 58.6% | — |
| [[@liao2025beyondmimic\|BeyondMimic]] | 81.6% | 85.8% | 73.4% | 39.1 mm |
| **SONIC** | **98.7%** | **99.6%** | **97.0%** | **23.2 mm** (−41%) |

The authors caveat this themselves: different source datasets and retargeting pipelines, so read it as
cross-dataset generalization evidence, not a data-matched benchmark. The 97.0% on PHUMA matters most —
that corpus comes from video-based pose estimation with a *different* retargeting pipeline.

**vs. a specialist** — against OpenHomie, a velocity-tracking locomotion controller, on its own task:
SONIC **98.5% survival vs. 43.0%**. OpenHomie collapses below 20% beyond ~1.5 m/s; SONIC holds near
100% to ~4 m/s. And OpenHomie's performance *plateaus past 8 GPUs* while SONIC keeps improving.

**Sim-to-real** — 123 real motion sequences: **99.2% success (vs. 100% sim)**, MPJPE-L 25.7 mm (vs.
22.3 mm). Gap is smallest at the upper body (22.2 vs. 21.8 mm) and **largest at the feet (53.7 vs.
29.0 mm)** — precise foot placement under real contact dynamics is where sim-to-real still bites.
Robust to an ~11 kg object dropped on the robot from above head height (Fig. S3).

**VLA-driven loco-manipulation** — GR00T N1.5 fine-tuned on teleop data, predicting 78-dim actions
(64-dim universal token + 14-dim hand joints). Five tasks, strict binary success over 10–20 trials:
apple→plate 90%, carrot pickup 75%, scrub pickup 95%, **open trash can by stepping on the pedal 70%**,
soda can→trash can (5 sequential skills) 60%, drill+box relocation 70%. **75% average.** Predicting
tokens beats predicting explicit SMPL poses (ablated, Tab. 3) — explicit poses give jerky motion and
poor directional control.

**Ablation:** FSQ beats VQ-VAE by **8.7 mm** MPJPE-L on test-content.

## Limitations / open questions
Stated by the authors (§2.6):
- **No formal treatment of safety** or energy efficiency for extended deployment. Stated plainly, in
  one sentence, as the paper's principal limitation.
- The tracker is robust to noisy planner output via motion-command domain randomization and the
  critically damped spring filter, but **under extreme conditions or very dynamic motions it may lose
  balance**.
- Motions that can't be executed on a G1 (**stair climbing, seated activities**) were *filtered out* of
  the training data — 700 h → 611 h.

> [!question] My reading — inferred, not claimed by the paper
> - The dataset filter is the seam. SONIC deliberately **discards stair climbing and sitting** as
>   G1-infeasible; [[@xie2026grail|GRAIL]] then adds *exactly those* (sitting, curbs, stairs) via a
>   height-map-conditioned scene-aware tracker fine-tuned on SONIC. GRAIL is best read as patching a
>   hole SONIC's own data curation opened, not as an independent contribution.
> - **Onboard vs. tethered:** SONIC runs entirely on a Jetson Orin at 50 Hz, but GRAIL's *visual*
>   policy on top of it needs a tethered RTX 5090 at 10 Hz. The perception layer, not the controller,
>   is what's off-board — worth knowing before citing either as an "onboard" result.
> - The OpenHomie comparison is the sharpest empirical claim against specialization in this literature:
>   a generalist beat a hand-tuned specialist **on the specialist's own metric**, and the specialist
>   stopped benefiting from compute at 8 GPUs. If that generalizes, it's an argument against
>   task-structured controllers on *capability* grounds — see the tension noted in [[motion-imitation]].
> - Not addressed: nothing here bounds tracking error or certifies stability. 99.6% success with a
>   0.25 m deviation threshold is an empirical success *rate*, not a guarantee — the gap
>   [[tracking-error-bound]] and [[control-lyapunov-function]] work is aimed at.

## Concepts
- [[motion-imitation]] — the paper's central thesis is that motion tracking is *the* scalable
  foundational task for humanoid control, and it supplies the scaling evidence the lineage lacked.
- [[foundation-model]] — explicitly "a foundation model for motion tracking"; the scaling-axes framing
  (parameters / data / compute) is imported wholesale from LLM practice.
- [[vision-language-action]] — the universal token space is a VLA *action space*; GR00T N1.5 drives the
  full kinematic chain including feet.
- [[loco-manipulation]] — five real VLA-driven whole-body tasks requiring coordinated hand *and* foot
  placement (feet used as manipulators).
- [[sim-to-real-transfer]] — 99.2% real vs. 100% sim over 123 sequences; feet are the residual gap.
- [[massively-parallel-simulation]] — Isaac Lab across 128 GPUs, 21k GPU hours, distributed multi-node.

## My notes
<!-- Your own reactions; how it relates to your work. -->

## Source
- arXiv: https://arxiv.org/abs/2511.07820 (v1 11 Nov 2025; **v3 21 May 2026**, the version read here)
- DOI: https://doi.org/10.48550/arXiv.2511.07820
- Project page: https://nvlabs.github.io/SONIC/ · Code: https://github.com/NVlabs/GR00T-WholeBodyControl
- Data: BONES-SEED on Hugging Face (Bones Studio, 2025)
- Full text read from `attachments/@luo2025sonic.pdf` (§1–3.6; supplementary S1–S8 skimmed for
  deployment/architecture details only).
