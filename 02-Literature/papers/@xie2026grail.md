---
type: paper
citekey: xie2026grail
tags: [generative, imitation, foundation-model]
aliases: [GRAIL]
created: 2026-07-29
modified: 2026-07-29
authors:
- Xie, Tianyi
- Zhang, Haotian
- Park, Jinhyung
- Wang, Zi
- Wen, Bowen
- Li, Jiefeng
- Li, Xueting
- Ben, Qingwei
- Weng, Haoyang
- Ye, Yufei
- Minor, David
- Wang, Tingwu
- Jiang, Chenfanfu
- Fidler, Sanja
- Kautz, Jan
- Fan, Linxi
- Zhu, Yuke
- Luo, Zhengyi
- Iqbal, Umar
- Yuan, Ye
year: 2026
venue: arXiv preprint
doi: 10.48550/arXiv.2606.05160
arxiv: '2606.05160'
url: https://arxiv.org/abs/2606.05160
pdf: attachments/@xie2026grail.pdf
zotero: null
status: to-read
mine: false
---

# GRAIL: Generating Humanoid Loco-Manipulation from 3D Assets and Video Priors

> [!info] Xie, Tianyi; Zhang, Haotian; Park, Jinhyung; Wang, Zi; Wen, Bowen; Li, Jiefeng; Li, Xueting; Ben, Qingwei; Weng, Haoyang; Ye, Yufei; Minor, David; Wang, Tingwu; Jiang, Chenfanfu; Fidler, Sanja; Kautz, Jan; Fan, Linxi; Zhu, Yuke; Luo, Zhengyi; Iqbal, Umar; Yuan, Ye · 2026 · arXiv preprint (NVIDIA + UCLA)
> Co-first: Xie, Zhang, Park, Wang · Project leads: Luo, Iqbal, Yuan · [Project page](https://research.nvidia.com/labs/dair/grail/)

> [!note] AI-drafted reading note from the full PDF — refine into your own words. `## My notes` left for you.

## TL;DR
A **fully digital data-generation pipeline** for humanoid loco-manipulation: instead of reconstructing
in-the-wild video, GRAIL *first* builds a fully specified 3D scene (known object geometry, camera, metric
scale, environment depth, and a **character prefitted to the target robot's proportions**), *then* uses a
video foundation model as an interaction prior, and reconstructs metric 4D human–object interaction in that
known frame. >20,000 generated sequences → retargeted to a Unitree G1 → task-general trackers → egocentric
RGB policies deployed on real hardware at **84% pick-up** and **90% stair-climbing** success. The physical
robot and environment appear only at deployment.

## Problem
Scaling humanoid loco-manipulation needs demonstrations that are simultaneously (a) diverse over objects,
whole-body motions, and scene geometry, and (b) *physically executable by the target robot*. The two
existing data sources each break on one axis:
- **Teleoperation / motion capture** give high-quality, robot-compatible data but don't scale — every new
  object or terrain layout needs physical scene reconfiguration, instrumented actors, and a human driving
  the robot.
- **In-the-wild video reconstruction** gives broad visual coverage but is underconstrained — camera, metric
  scale, object geometry, human shape, contacts, and world-space motion must all be inferred from ambiguous
  monocular observations, and the recovered human morphology doesn't match the robot.

GRAIL's framing question: rather than recovering an entire 3D interaction from an uncontrolled video, can we
**specify the 3D scene first** and use video generative priors only for the *behavior*?

## Method
Three stages, all in simulation, plus a sim-to-real distillation.

### 1. Robot-centric human video generation (§3.1)
Given a 3D object asset $\mathcal{M}_\mathcal{O}$:
- Candidate environments from **Infinigen**; object settled into a stable, collision-free initial pose
  $\Theta^\mathcal{O}_1$ by rigid-body simulation (XPBD).
- A **human character asset prefitted to the target humanoid's proportions** placed in a rest pose — this is
  the morphology-mismatch fix, applied *before* generation rather than after.
- First frame rendered in Blender with **known intrinsics $C_K$ and extrinsics $C_E$**.
- A VLM (ChatGPT) writes an interaction prompt from the rendered frame; a VFM (**Kling 2.1**, image-to-video)
  synthesizes the reference HOI video under a **static camera**, so $(C_K, C_E)$ stay valid for reconstruction.
- The generated environment does double duty: visual context for the VFM *and* a ground-truth point cloud for
  metric-scale depth alignment later.

### 2. Interaction-aware 4D HOI reconstruction (§3.2)
Independent initial estimates, then joint refinement — the point being that every quantity normally *inferred*
is instead *known by construction*.
- **Body:** GENMO gives per-frame SMPL-X pose in camera space; **body shape is held fixed** at the prefitted
  morphology (GENMO contributes pose only), then mapped to world via known $C_E$.
- **Hands:** WiLoR refines per-frame MANO parameters per hand; missing detections filled by temporal linear
  interpolation, Savitzky–Golay smoothing, integrated into SMPL-X by wrist IK preserving predicted fingers.
- **Object:** FoundationPose fine-tuned 5 epochs with **depth channels zeroed** (RGB-only setup), initialized
  from the known $\Theta^\mathcal{O}_1$ and propagated. SAM2 masks validate tracking; inconsistent sequences
  are discarded.
- **Joint optimization** over *residual* motion parameters (6D rotation parameterization), hands frozen:
  $L = \lambda_{kp}L_{kp} + \lambda_{proj}L_{proj} + \lambda_{depth}L_{depth} + \lambda_{cont}L_{cont} + \lambda_{reg}L_{reg}$
  - $L_{kp}$ 2D body/hand keypoint reprojection · $L_{proj}$ keeps object image-aligned with FoundationPose
  - $L_{depth}$ — MoGe-2 depth **aligned to the GT rendered background depth** to recover metric scale, then
    SAM2-segmented human/object point clouds matched by bidirectional Chamfer distance
  - $L_{cont}$ — VLM-predicted per-frame contact labels (e.g. which hand), propagated over intervals;
    **depth-only** Chamfer on contact vertices, since image-space losses already handle projection. Disabled
    for terrain-only sequences.
  - $L_{reg} = L_{foot} + L_{vel} + L_{smooth}$ — foot-contact anti-skating (GENMO labels), pelvis velocity
    matched to GENMO's global estimate (suppresses depth-direction oscillation), 1st/2nd-order smoothness.

### 3. Task-general loco-manipulation tracking (§3.3)
**GMR** retargets the SMPL-X motion to the G1 (low mismatch *because* the character was robot-proportioned).
Tracking policies are built on **SONIC**, a pretrained whole-body controller with an FSQ-quantized latent
token $z_t = \mathcal{E}(\tilde q_t)$ and action decoder $\mathcal{G}$. Crucially, policies are trained
**per task family over pooled trajectories**, not per sequence or per object:
- **Object-aware latent adaptor $\pi_\varphi$** — controller (encoder/quantizer/decoder) **frozen**. Observes
  proprioception $s_t$ + object reference $o_t$ (object pose in body frame, hand-to-object transforms, finger
  contact forces, BPS shape encoding, and *critically* **delta observations** of reference-future vs. current
  object pose). Emits a 64-dim latent residual $\Delta z_t$ and a 2-dim binary hand primitive →
  $a^{body}_t = \mathcal{G}(z_t + \lambda\Delta z_t)$, $\lambda = 0.1$, with an $\ell_2$ penalty on
  $\Delta z_t$ to stay near pretrained behavior. Each hand primitive maps to 7 finger joints via predefined
  grasp configurations. BPS encoding is what lets one $\pi_\varphi$ span diverse object geometries.
- **Scene-aware tracker** — fine-tunes the controller *together with* a 2D-conv height-map encoder
  $\epsilon_h$, on a **mixture** of scene-interaction trajectories and the original flat-ground data (to
  preserve the base locomotion distribution). A parallel kinematic decoder $\mathcal{G}_{rec}$ reconstructs
  the motion targets as an auxiliary MSE regularizer on the latent.
- **Rewards** — shared exponential motion-tracking term + regularization; object-aware adds an object pose
  term and a **contact-gated** grasp reward (sustained finger contact saturating at $N_{min}$, thumb/index
  approaching from opposing sides for a stable pinch, fingertips drawn to the contact centroid).
- **Training** — PPO in Isaac Lab, **64 NVIDIA L40 GPUs**, 30,000 iterations, 1,024 envs/GPU, reference state
  initialization at every reset, motions sampled from a shared 4D HOI pool.

### 4. Sim-to-real (§3.4)
Trackers distilled into **separate egocentric visual policies** (one for pick-up, one for stair-climbing) that
consume head-camera RGB and output SONIC latent tokens, trained with visual domain randomization and camera
alignment. Deployment is **tethered**: G1 streams to a desktop with an RTX 5090, Luxonis OAK-D W camera,
inference at **10 Hz**.

## Key results
**Dataset.** 1,000 object assets (Robocasa, ComAsset, OMOMO, Hunyuan3D) × 1,000 procedurally generated terrain
configurations → **>20,000 sequences** in four families: pick-up (tabletop + ground, varying heights), whole-body
manipulation (carry/push/reposition boxes and carts while walking), sitting (diverse chair styles), and terrain
traversal (curbs, slopes, stairs — noted as underrepresented in existing datasets).

**HOI generation quality** (20 ComAsset objects; physical executability via InterMimic replay in simulation):

| | Contact ↓ | Pen. ↓ | Inter. Score ↑ | SR ↑ | Body Dev ↓ | Obj Dev ↓ |
|---|---|---|---|---|---|---|
| HOIDiff | 0.012 | 2.07% | 1.79 | 15.8% | 0.2120 | 0.3352 |
| CHOIS | 0.034 | 3.74% | 2.47 | 10.5% | 0.2564 | 0.3642 |
| DAViD | 0.246 | 1.46% | 2.74 | 24.0% | 0.4723 | 0.5826 |
| **GRAIL** | **0.008** | **0.90%** | **3.58** | **88.9%** | **0.0913** | **0.0851** |

The executability gap (88.9% vs. 24.0%) is the headline — an order of magnitude more of the generated motion is
physically trackable.

**Task-general tracking** (124 motions / 43 objects): GRAIL **81.4%** SR, ObjPos **0.135**, MPJPE-L **41.8** vs.
ResMimic 49.2% / 0.393 / 80.9 and HDMI 48.5% / 0.283 / 122.3. *Caveat the authors state:* neither baseline
actuates per-finger DoFs (their interactions rely on whole-arm/whole-body contact) and both train one policy
per task, so this compares different problem settings as much as different methods.

**Ablations** — the informative one: removing $\pi_\varphi$ (vanilla SONIC) gives the **best body tracking**
(MPJPE-L 37.1) but the **worst manipulation success** (39.7%). Accurate body imitation alone is insufficient for
object interaction. Removing SONIC entirely (train from scratch) → 45.0% SR and MPJPE-L blows up to 243.5;
absolute instead of relative object observations → 57.9%.

**Real G1.** Pick-up 84% on 5 seen objects (cube 100%, apple 60%, tea box 100%, carrot 70%, wet wipes 90%; 10
trials each) and **80% on 5 unseen objects** (spray can 100%, lint roller 50%, peach 90%, flashlight 80%,
medicine bottle 80%). Stair-climbing 90%. Trained on **only GRAIL-generated data** — 200 approach-and-pick-up
sequences per object.

## Limitations / open questions
Stated by the authors (§6):
- Requires 3D object assets, simulator-ready scene setup, and a VFM that actually follows the requested
  interaction.
- Reconstruction degrades under severe occlusion, fast motion, or inconsistent object appearance from the VFM,
  and the **failure-filtering step discards a non-trivial fraction of sequences** (fraction not quantified).
- Task-general trackers amortize over related pools but **still need training/fine-tuning when the motion
  family changes substantially** — so "task-general" means within-family, not open-ended.

> [!question] My reading — inferred, not claimed by the paper
> - The grasp action space is a **2-dim binary open/close primitive** mapped to predefined finger
>   configurations. This is loco-manipulation with a gripper abstraction, not dexterous manipulation; the
>   84%/80% pick-up numbers should be read in that light.
> - Deployment is **tethered at 10 Hz** off an RTX 5090 — the visual policy is not yet an onboard-compute
>   result. Relevant if comparing against onboard perceptive-locomotion baselines.
> - The whole pipeline inherits a **VFM as an unmodelled prior**: physical plausibility is enforced *post hoc*
>   by the optimization losses and the filtering step, never guaranteed. This is the same structure-vs-scale
>   bet flagged in [[motion-imitation]] §Tension — GRAIL scales data with no certificate, and pays for it with
>   a discard rate.
> - Terrain traversal here is **height-map conditioned tracking of reconstructed references**, which is a
>   different interface from command-driven perceptive locomotion — worth contrasting with the $SE(2)$
>   planner-compatible interface in your own line.

## Concepts
- [[motion-imitation]] — GRAIL's stage 3 is reference-motion tracking on a pretrained whole-body controller
  (SONIC), in the DeepMimic → PHC/PULSE/MaskedMimic lineage; the novelty is *where the references come from*.
- [[foundation-model]] — a video foundation model (Kling) used as an **interaction prior**, plus a VLM for
  prompt authoring and contact labelling. Foundation models supply behavior, not control.
- [[sim-to-real-transfer]] — visual domain randomization + camera alignment; RGB egocentric policies trained
  purely on generated data transfer to a real G1.
- [[massively-parallel-simulation]] — PPO in Isaac Lab, 64× L40, 1,024 envs/GPU, 30k iterations.
- [[loco-manipulation]] — the target capability (stub created 2026-07-29 with this note).

## My notes
<!-- Your own reactions; how it relates to your work. -->

## Source
- arXiv: https://arxiv.org/abs/2606.05160 (v1, submitted 3 Jun 2026, cs.RO)
- DOI: https://doi.org/10.48550/arXiv.2606.05160
- Project page: https://research.nvidia.com/labs/dair/grail/
- Full text read from `attachments/@xie2026grail.pdf` (main paper §1–6; appendices A–C not read).
