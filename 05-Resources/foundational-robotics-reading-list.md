---
type: resource
tags: [to-revisit]
aliases: [Foundational Robotics Reading List, Modern Robotics Canon, Foundational Papers]
created: 2026-07-26
modified: 2026-07-29
---

# Foundational Robotics Reading List

> [!note] AI-drafted, agent-maintained working list — not an authentic synthesis note. Refine
> the ordering/annotations to taste; when a cluster is read and digested, promote it into a
> proper MOC in [[04-Maps/index|04 · Maps]].

A prioritized to-read queue of **foundational papers for the modern (foundation-model era) of
robotics** — the generative / learning spine that complements otto's already-deep
[[learning-based-locomotion|control + humanoid-RL]] coverage.

**Ordering = dependency / canon order** (chosen 2026-07-26): read the *enablers* before the
systems built on them. Within each layer, the root comes first.

**Legend.** `[ ]` unread · ✅ full reading note in otto · 🟨 metadata+abstract stub (flesh out
when read) · PDF saved at `attachments/@citekey.pdf` for every entry below unless noted.
Concept notes drafted for this list: [[transformer]] · [[diffusion-model]] · [[diffusion-policy]]
· [[world-model]] · [[motion-imitation]] · [[vision-language-action]] · [[foundation-model]]
· [[loco-manipulation]].

---

## Layer 1 — Sequence & generative primitives (the enablers)
- [ ] ✅ [[@vaswani2017attention]] — **Transformer / self-attention.** The architecture under every LLM/VLM and, through them, every VLA below. → [[transformer]]
- [ ] ✅ [[@ho2020denoising]] — **DDPM.** The denoising-diffusion generative process. → [[diffusion-model]]

## Layer 2 — World models (learned dynamics)
- [ ] ✅ [[@ha2018world]] — **World Models.** Learn a latent simulator; train/plan "in imagination." → [[world-model]]
- [ ] 🟨 [[@hafner2023mastering]] — **DreamerV3.** One config solves 150+ tasks incl. Minecraft-diamond from scratch.
- [ ] 🟨 [[@bruce2024genie]] — **Genie.** Foundation *world* model — action-controllable environments from unlabelled video.

## Layer 3 — Generative primitives → learned control
- [ ] ✅ [[@chi2023diffusion]] — **Diffusion Policy.** Diffusion over action chunks for multimodal visuomotor imitation. → [[diffusion-policy]]

## Layer 4 — Vision-Language-Action / robot foundation models
- [ ] 🟨 [[@brohan2022rt1]] — **RT-1.** Robotics Transformer; task-agnostic pretraining at scale. → [[vision-language-action]]
- [ ] ✅ [[@brohan2023rt2]] — **RT-2.** Web VLM knowledge transfers to robot actions (the canonical VLA). → [[vision-language-action]], [[foundation-model]]
- [ ] 🟨 [[@oneill2024open]] — **Open X-Embodiment / RT-X.** Cross-embodiment dataset + models; the data play. → [[foundation-model]]
- [ ] 🟨 [[@kim2024openvla]] — **OpenVLA.** Open 7B VLA; beats RT-2-X with 7× fewer params; fine-tunes on consumer GPUs.
- [ ] 🟨 [[@black2024pi0]] — **π0.** VLA *flow* model for general robot control (Physical Intelligence).

## Layer 5 — Generative motion imitation (character → humanoid)
- [ ] ✅ [[@peng2018deepmimic]] — **DeepMimic.** Example-guided RL, single-clip tracking — the ancestor of the whole line. → [[motion-imitation]]
- [ ] 🟨 [[@peng2021amp]] — **AMP.** Adversarial motion prior; style from unstructured clips, no clip selection.
- [ ] 🟨 [[@peng2022ase]] — **ASE.** Large-scale reusable adversarial skill embeddings.
- [ ] 🟨 [[@luo2023perpetual]] — **PHC.** Perpetual humanoid control; 10k clips, fail-state recovery.
- [ ] 🟨 [[@luo2024universal]] — **PULSE.** Universal humanoid motion latent for downstream RL.
- [ ] 🟨 [[@tessler2024maskedmimic]] — **MaskedMimic** (NVIDIA). Unified control as masked motion inpainting.
- [ ] 🟨 [[@wang2026motionbricks]] — **MotionBricks.** Modular latent generative model + "smart primitives"; **deploys on the Unitree G1** (your hardware).

## Layer 6 — Composing the stack: generated data → loco-manipulation on hardware
> [!abstract] Added 2026-07-29 (ai-draft). This layer is a **tight cluster, not a list** — 8 papers,
> mostly NVIDIA + Stanford/CMU, 2025–2026, all deploying on the **Unitree G1**. They cite each other
> densely and share components (GMR retargeting, GENMO motion estimation, SONIC as the base controller).
> Read the two anchors first; the rest exist to explain *why the anchors' pieces are the way they are*.
> Suggested order is 6a → 6b → 6c → 6d, but 6b/6c/6d are independent of each other.

### 6a. The two anchors — read these first, in this order
- [ ] ✅ [[@luo2025sonic]] — **SONIC** (NVIDIA). **Read before GRAIL — GRAIL is built on it.** The scaling-laws paper for humanoid whole-body control: motion tracking as *the* scalable foundational task (dense mocap supervision, no reward engineering), scaled to 42M params / 100M+ frames / 21k GPU hours → 99.6% success on unseen motion, **onboard on a Jetson Orin at 50 Hz**, with a quantized universal token space that VR teleop, video/text/music, and a GR00T N1.5 VLA all drive through one policy. → [[motion-imitation]], [[foundation-model]], [[vision-language-action]], [[loco-manipulation]]
  - *Why it matters most to you:* it answers the **control-rate interface** open question in [[vision-language-action]] with a learned latent token; it claims to beat a hand-tuned velocity-tracking specialist **on velocity tracking** (98.5% vs. 43.0% survival — but see [[@ben2025homie]] in 6c before accepting that framing); and its one stated limitation is "no formal treatment of safety." That's the scale-side bet in [[motion-imitation]] §Tension stated as plainly as it gets. Public G1-format mocap (**BONES-SEED**, 288 h) + code (`NVlabs/GR00T-WholeBodyControl`).
- [ ] ✅ [[@xie2026grail]] — **GRAIL** (NVIDIA/UCLA). Uses a *video* foundation model as an interaction prior inside a fully specified 3D scene, reconstructs metric 4D human-object interaction, retargets to the **Unitree G1**, and trains task-general trackers on a frozen pretrained whole-body controller (SONIC). 20k+ generated sequences → 84% real pick-up, 90% stair-climbing, trained on **generated data only**. → [[loco-manipulation]], [[motion-imitation]], [[foundation-model]], [[sim-to-real-transfer]]
  - *Why here:* it's the payoff case for this whole list — Layer 4's foundation models supply the behavior prior, Layer 5's imitation machinery converts it to robot actions, and it lands on your hardware. Read after Layer 5's roots (DeepMimic → PHC) so the tracking stack reads as familiar.
  - *The seam between the two:* SONIC's dataset **filters out** stair climbing and seated activities as G1-infeasible; GRAIL's scene-aware tracker adds exactly those back. Read consecutively and the pair reads as one program, not two papers.

### 6b. Upstream plumbing — how human motion becomes robot motion
*Both anchors depend on these two. Neither anchor examines them, which is why they're worth reading separately.*
- [ ] ✅ [[@araujo2025retargeting]] — **GMR** (Stanford). The retargeter **both anchors use**, plus the data-quality ablation this literature was missing: hold the tracker fixed ([[@liao2025beyondmimic|BeyondMimic]], which needs no reward tuning) and vary only the retargeter. Retargeting artifacts — ground penetration (60 cm!), self-intersection, joint-value jumps — measurably reduce policy robustness once you stop papering over them with reward engineering. → [[motion-imitation]], [[sim-to-real-transfer]]
  - **Read this one closely.** It's the most methodologically careful paper in the cluster, it partly undercuts SONIC's "no reward engineering" claim (the engineering moved upstream into the retargeter), and its start-frame result (same policy: 14% → 100% success depending on the reference's first frame) is a **reachability condition on the reference** — the closest thing in this cluster to a statement your CLF/[[tracking-error-bound]] work could formalize.
- [ ] 🟨 [[@li2025genmo]] — **GENMO / "GEM"** (NVIDIA, ICCV 2025). Unifies motion *estimation* and *generation* by treating estimation as **constrained generation**. GRAIL uses it as the estimator (SMPL-X pose from generated video, foot-contact labels, pelvis velocity); SONIC uses it as the generator (video/text/music → motion). Same model, both directions. → [[diffusion-model]], [[motion-imitation]]
  - *Naming trap:* GRAIL cites it as **GENMO**, SONIC as **GEM**. Same authors, same venue, one paper.

### 6c. Rival whole-body loco-manipulation systems — the baselines the anchors beat
*Read at least one to calibrate how much the anchors' headline numbers mean.*
- [ ] 🟨 [[@zhao2025resmimic]] — **ResMimic** (Berkeley/Stanford/CMU). General motion tracking base + a **task-specific residual** that adds object awareness. Architecturally the closest rival to GRAIL's stage 3 — the fork is *where the residual enters*: action space (ResMimic) vs. the controller's quantized latent (GRAIL). GRAIL's baseline at 49.2% SR. → [[loco-manipulation]]
- [ ] 🟨 [[@weng2025hdmi]] — **HDMI** (CMU). Whole-body interaction learned **directly from monocular RGB video** — the video-native counterpoint to GRAIL's "specify the 3D scene first" premise. Reports **67 consecutive door traversals (~34 min)**, a durability metric nobody else here measures. Also a useful negative result: removing the contact reward doesn't hurt most tasks. GRAIL's baseline at 48.5% SR. → [[loco-manipulation]]
- [ ] 🟨 [[@ben2025homie]] — **HOMIE / "OpenHomie"** (Shanghai AI Lab). A **$500 open-source teleoperation cockpit** (pedal-driven RL body policy + isomorphic exoskeleton arm + Hall-sensor gloves). → [[loco-manipulation]]
  - **Read the abstract before citing SONIC's specialist comparison.** HOMIE's policy is built for walking/squatting *while an operator poses the upper body* — not high-speed velocity tracking. SONIC benchmarks it to 5 m/s and reports 43% survival. That's outside HOMIE's design envelope, so "generalist beats specialist" is weaker than SONIC's framing suggests.

### 6d. The semantic layer on top
- [ ] 🟨 [[@bjorck2025gr00t]] — **GR00T N1** (NVIDIA). Open humanoid VLA, dual-system: vision-language module (System 2) + **diffusion transformer** action head (System 1), jointly trained end-to-end. SONIC fine-tunes N1.5 to emit its universal motion tokens. → [[vision-language-action]], [[foundation-model]], [[diffusion-model]]
  - *Two nuances:* (1) SONIC uses **N1.5**, which is only a **blog post** — N1 is the citable paper. (2) GR00T N1's own hardware result is bimanual manipulation on a **Fourier GR-1**, i.e. a stationary upper-body task; whole-body loco-manipulation is a *SONIC* result, not a GR00T one.
  - *Worth comparing deliberately:* GR00T solves the slow-semantics/fast-control rate split **inside** one model (diffusion action head); SONIC solves it **between** models (quantized token). Two answers to the open question in [[vision-language-action]].

---

## Already in otto — the humanoid-RL systems these foundations feed into
The systems layer is well-covered; these ground the list's payoff and live under
[[learning-based-locomotion]]:
- [x] [[@liao2025beyondmimic]] — BeyondMimic (guided diffusion → versatile humanoid control; the bridge from Layer 1/5 to hardware).
- [x] [[@radosavovic2024real]] · [[@radosavovic2024humanoid]] — real-world humanoid RL / challenging terrain.
- [x] [[@zhang2026rpl]] · [[@zhuang2024humanoid]] · [[@wu2026perceptive]] — perceptive humanoid locomotion & parkour.

## Notes / open decisions
- **Tagging:** new notes carry `tags: []` (foundation-model papers don't fit otto's
  robotics-control taxonomy). Proposed additions to `.claude/taxonomy.md`: `generative`,
  `foundation-model`, `imitation` — awaiting your call before applying.
- **Promotion candidates:** once read, Layers 4–5 are the natural seed for a
  `modern-robotics-foundations` or `learned-whole-body-control` MOC.
