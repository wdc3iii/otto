---
type: paper
citekey: bjorck2025gr00t
tags: [foundation-model, generative]
aliases: [GR00T N1, GR00T, GR00T N1.5]
created: 2026-07-29
modified: 2026-07-29
authors:
- Bjorck, Johan
- Castañeda, Fernando
- Cherniadev, Nikita
- Da, Xingye
- Ding, Runyu
- Fan, Linxi
- Fang, Yu
- Fox, Dieter
- Hu, Fengyuan
- Huang, Spencer
- Jang, Joel
- Jiang, Zhenyu
- Kautz, Jan
- Kundalia, Kaushil
- Lao, Lawrence
- Li, Zhiqi
- Lin, Zongyu
- Lin, Kevin
- Liu, Guilin
- Llontop, Edith
- Magne, Loic
- Mandlekar, Ajay
- Narayan, Avnish
- Nasiriany, Soroush
- Reed, Scott
- Tan, You Liang
- Wang, Guanzhi
- Wang, Zu
- Wang, Jing
- Wang, Qi
- Xiang, Jiannan
- Xie, Yuqi
- Xu, Yinzhen
- Xu, Zhenjia
- Ye, Seonghyeon
- Yu, Zhiding
- Zhang, Ao
- Zhang, Hao
- Zhao, Yizhou
- Zheng, Ruijie
- Zhu, Yuke
year: 2025
venue: arXiv preprint
doi: 10.48550/arXiv.2503.14734
arxiv: '2503.14734'
url: https://arxiv.org/abs/2503.14734
pdf: attachments/@bjorck2025gr00t.pdf
zotero: null
status: to-read
mine: false
---

# GR00T N1: An Open Foundation Model for Generalist Humanoid Robots

> [!info] NVIDIA (authors listed alphabetically; project leads Linxi "Jim" Fan and Yuke Zhu) · 2025 · arXiv preprint
> [Isaac GR00T](https://developer.nvidia.com/isaac/gr00t) · The VLA layer SONIC plugs into

> [!todo] metadata + abstract stub — full text not read (36 pp). The *role* section is grounded in [[@luo2025sonic]], which I did read. Flesh out when read.

> [!warning] Version note: [[@luo2025sonic|SONIC]] uses **GR00T N1.5**, which is a **blog post**, not a paper (`research.nvidia.com/labs/gear/gr00t-n1_5/`, June 2025). This note covers **GR00T N1**, the arXiv paper, which is the citable architecture. Don't attribute N1.5's numbers to N1.

## TL;DR
An **open VLA foundation model for humanoids** with a dual-system architecture: a vision-language module
(**System 2**) interprets scene and instruction; a **diffusion transformer** (**System 1**) generates
fluid motor actions in real time. Both tightly coupled and trained **end-to-end**, on a heterogeneous
mix of real-robot trajectories, human video, and synthetic data.

## Abstract (from arXiv)
> General-purpose robots need a versatile body and an intelligent mind. Recent advancements in humanoid
> robots have shown great promise as a hardware platform for building generalist autonomy in the human
> world. A robot foundation model, trained on massive and diverse data sources, is essential for enabling
> the robots to reason about novel situations, robustly handle real-world variability, and rapidly learn
> new tasks. To this end, we introduce GR00T N1, an open foundation model for humanoid robots. GR00T N1
> is a Vision-Language-Action (VLA) model with a dual-system architecture. The vision-language module
> (System 2) interprets the environment through vision and language instructions. The subsequent
> diffusion transformer module (System 1) generates fluid motor actions in real time. Both modules are
> tightly coupled and jointly trained end-to-end. We train GR00T N1 with a heterogeneous mixture of
> real-robot trajectories, human videos, and synthetically generated datasets. We show that our
> generalist robot model GR00T N1 outperforms the state-of-the-art imitation learning baselines on
> standard simulation benchmarks across multiple robot embodiments. Furthermore, we deploy our model on
> the Fourier GR-1 humanoid robot for language-conditioned bimanual manipulation tasks, achieving strong
> performance with high data efficiency.

## Role in the SONIC/GRAIL cluster
This is the **semantic layer** that sits on top of [[@luo2025sonic|SONIC]]'s controller. SONIC fine-tunes
GR00T N1.5 on VR-teleoperated data and has it emit **78-dim actions = 64-dim universal motion token +
14-dim hand joints** — so the VLA never predicts joint targets, only tokens that SONIC's frozen decoder
turns into motion. Five real G1 loco-manipulation tasks at **75% average** success, including using a
**foot** as a manipulator.

SONIC also ablates the alternative: having the VLA predict explicit SMPL poses instead of tokens gives
**jerky motion and poor directional control**. That ablation is the concrete argument for a quantized
interface between a slow semantic model and a fast controller.

> [!question] My reading — inferred, not claimed by the paper
> Note the embodiment mismatch in the citation chain: GR00T N1's own hardware result is on a **Fourier
> GR-1** doing **bimanual manipulation** — a stationary upper-body task. SONIC's contribution is
> arguably making the same model class drive a *whole body including legs* on a G1, via the token
> interface. So "GR00T does whole-body loco-manipulation" is a SONIC result, not a GR00T N1 result.
> - The dual-system framing (slow VLM + fast diffusion transformer) is the same **rate-separation**
>   problem your [[vision-language-action]] note flags. GR00T solves it *inside* one model with a
>   diffusion action head; SONIC solves it *between* models with a quantized token. Two distinct answers
>   to one question, and worth comparing deliberately.

## Concepts
- [[vision-language-action]] — canonical humanoid VLA; the dual-system architecture is the reference design.
- [[foundation-model]] · [[diffusion-model]] — System 1 is a diffusion transformer over actions.
- [[transformer]] — both modules.
- [[loco-manipulation]] — via SONIC's token interface, not in GR00T N1 itself.

## My notes
<!-- Your own reactions; how it relates to your work. -->

## Source
- arXiv: https://arxiv.org/abs/2503.14734 (v2, Mar 2025) · DOI: https://doi.org/10.48550/arXiv.2503.14734
- GR00T N1.5 (used by SONIC) is a blog post: https://research.nvidia.com/labs/gear/gr00t-n1_5/
- Abstract quoted verbatim from arXiv. Role section grounded in [[@luo2025sonic]] §2.5, §3.6.
