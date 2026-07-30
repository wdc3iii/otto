---
type: paper
citekey: li2025genmo
tags: [generative, imitation]
aliases: [GENMO, GEM]
created: 2026-07-29
modified: 2026-07-29
authors:
- Li, Jiefeng
- Cao, Jinkun
- Zhang, Haotian
- Rempe, Davis
- Kautz, Jan
- Iqbal, Umar
- Yuan, Ye
year: 2025
venue: ICCV 2025
doi: 10.48550/arXiv.2505.01425
arxiv: '2505.01425'
url: https://arxiv.org/abs/2505.01425
pdf: attachments/@li2025genmo.pdf
zotero: null
status: to-read
mine: false
---

# GENMO: A GENeralist Model for Human MOtion

> [!info] Li, Jiefeng; Cao, Jinkun; Zhang, Haotian; Rempe, Davis; Kautz, Jan; Iqbal, Umar; Yuan, Ye · 2025 · ICCV 2025 (NVIDIA)
> [Project page](https://research.nvidia.com/labs/dair/genmo/)

> [!todo] metadata + abstract stub — full text not read. The *role* section is grounded in [[@xie2026grail]] and [[@luo2025sonic]], which I did read. Flesh out when read.

> [!warning] Naming: this paper is cited as **GENMO** by [[@xie2026grail|GRAIL]] and as **GEM** by [[@luo2025sonic|SONIC]] — same authors, same venue (ICCV 2025), same work. arXiv title is GENMO; SONIC's bibliography renames it "GEM: A generalist model for human motion." One paper, two names. Don't double-file it.

## TL;DR
Unifies human motion **estimation** (recover motion from video) and **generation** (synthesize motion
from text/audio/keyframes) in one model, by reformulating estimation as **constrained generation** —
the output must precisely satisfy the observed conditioning signal. Combines regression and diffusion,
handles variable-length motion and mixed multimodal conditions at different time intervals.

## Abstract (from arXiv)
> Human motion modeling traditionally separates motion generation and estimation into distinct tasks
> with specialized models. Motion generation models focus on creating diverse, realistic motions from
> inputs like text, audio, or keyframes, while motion estimation models aim to reconstruct accurate
> motion trajectories from observations like videos. Despite sharing underlying representations of
> temporal dynamics and kinematics, this separation limits knowledge transfer between tasks and requires
> maintaining separate models. We present GENMO, a unified Generalist Model for Human Motion that
> bridges motion estimation and generation in a single framework. Our key insight is to reformulate
> motion estimation as constrained motion generation, where the output motion must precisely satisfy
> observed conditioning signals. Leveraging the synergy between regression and diffusion, GENMO
> achieves accurate global motion estimation while enabling diverse motion generation. We also
> introduce an estimation-guided training objective that exploits in-the-wild videos with 2D
> annotations and text descriptions to enhance generative diversity. Furthermore, our novel
> architecture handles variable-length motions and mixed multimodal conditions (text, audio, video) at
> different time intervals, offering flexible control. This unified approach creates synergistic
> benefits: generative priors improve estimated motions under challenging conditions like occlusions,
> while diverse video data enhances generation capabilities. Extensive experiments demonstrate GENMO's
> effectiveness as a generalist framework that successfully handles multiple human motion tasks within
> a single model.

## Role in the SONIC/GRAIL cluster
This is the **human-motion workhorse both anchor papers depend on**, used at opposite ends:
- In [[@xie2026grail|GRAIL]] it is the **estimator** — per-frame SMPL-X pose from the generated video
  (with body shape held fixed at the robot-proportioned morphology, so GENMO contributes pose only). Its
  foot-contact labels drive GRAIL's anti-skating regularizer, and its global-space pelvis velocity
  estimate is used to suppress depth-direction oscillation.
- In [[@luo2025sonic|SONIC]] it is the **generator** — the multi-modal front end that turns video, text,
  and music into human motion, fed to SONIC's human motion encoder $\mathcal{E}^h$ via sliding windows
  with inpainting-based transitions.

That the *same* model serves both directions is the whole point of the paper, and it's why this cluster
can treat "video in" and "text in" as the same interface.

> [!question] My reading — inferred, not claimed by the paper
> Reformulating estimation as **constrained generation** is the conceptual move worth extracting, and it
> generalizes past motion: a generative prior plus hard consistency constraints is the same shape as
> using a learned model with a feasibility projection. The interesting question for your line is what
> "precisely satisfy observed conditioning signals" means operationally — a soft loss, or an enforced
> constraint? The abstract doesn't say, and it's the difference between a prior and a guarantee.

## Concepts
- [[diffusion-model]] — regression + diffusion synergy is the stated mechanism.
- [[motion-imitation]] — supplies the reference motion that the imitation stack consumes.
- [[foundation-model]] — "generalist model" across estimation and generation tasks in one set of weights.

## My notes
<!-- Your own reactions; how it relates to your work. -->

## Source
- arXiv: https://arxiv.org/abs/2505.01425 (v1, 2 May 2025) · DOI: https://doi.org/10.48550/arXiv.2505.01425
- Project page: https://research.nvidia.com/labs/dair/genmo/
- Abstract quoted verbatim from arXiv. Role section grounded in [[@xie2026grail]] §3.2 and [[@luo2025sonic]] §3.4.
