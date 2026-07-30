---
type: paper
citekey: ben2025homie
tags: [hardware, rl, locomotion]
aliases: [HOMIE, OpenHomie]
created: 2026-07-29
modified: 2026-07-29
authors:
- Ben, Qingwei
- Jia, Feiyu
- Zeng, Jia
- Dong, Junting
- Lin, Dahua
- Pang, Jiangmiao
year: 2025
venue: arXiv preprint
doi: 10.48550/arXiv.2502.13013
arxiv: '2502.13013'
url: https://arxiv.org/abs/2502.13013
pdf: attachments/@ben2025homie.pdf
zotero: null
status: to-read
mine: false
---

# HOMIE: Humanoid Loco-Manipulation with Isomorphic Exoskeleton Cockpit

> [!info] Ben, Qingwei; Jia, Feiyu; Zeng, Jia; Dong, Junting; Lin, Dahua; Pang, Jiangmiao · 2025 · arXiv preprint (Shanghai AI Lab)
> [Website / open-source](https://homietele.github.io/) · **SONIC's specialist baseline** ("OpenHomie")

> [!todo] metadata + abstract stub — full text not read. The *role* section below is grounded in [[@luo2025sonic]], which I did read. Flesh out when read.

## TL;DR
A **$500, fully open-source semi-autonomous teleoperation cockpit** for humanoid loco-manipulation:
an RL body-control policy driven by a **foot pedal**, an **isomorphic exoskeleton arm** for arm control,
and Hall-sensor **motion-sensing gloves** for the hands. The point is a data flywheel — make humanoid
teleoperation cheap and fast enough to collect demonstrations at volume.

Matters to otto mainly as the **specialist baseline [[@luo2025sonic|SONIC]] beats**, and reading it
changes how much that comparison is worth (see below).

## Abstract (from arXiv)
> Generalizable humanoid loco-manipulation poses significant challenges, requiring coordinated
> whole-body control and precise, contact-rich object manipulation. To address this, this paper
> introduces HOMIE, a semi-autonomous teleoperation system that combines a reinforcement learning
> policy for body control mapped to a pedal, an isomorphic exoskeleton arm for arm control, and
> motion-sensing gloves for hand control, forming a unified cockpit to freely operate humanoids and
> establish a data flywheel. The policy incorporates novel designs, including an upper-body pose
> curriculum, a height-tracking reward, and symmetry utilization. These features enable the system to
> perform walking and squatting to specific heights while seamlessly adapting to arbitrary upper-body
> poses. The exoskeleton, by eliminating the reliance on inverse dynamics, delivers faster and more
> precise arm control. The gloves utilize Hall sensors instead of servos, allowing even compact devices
> to achieve 15 or more degrees of freedom and freely adapt to any model of dexterous hands. Compared
> to previous teleoperation systems, HOMIE stands out for its exceptional efficiency, completing tasks
> in half the time; its expanded working range, allowing users to freely reach high and low areas as
> well as interact with any objects; and its affordability, with a price of just $500. The system is
> fully open-source, demos and code can be found in our https://homietele.github.io/.

## Role in the SONIC/GRAIL cluster
[[@luo2025sonic|SONIC]] uses HOMIE's locomotion policy ("OpenHomie") as its **specialist baseline**, and
this is the comparison carrying SONIC's strongest rhetorical claim: a generalist tracker beating a
hand-tuned specialist *on the specialist's own task*. SONIC reports **98.5% vs. 43.0% survival** on
sim-to-sim velocity tracking over 0–5 m/s, with HOMIE collapsing below 20% past ~1.5 m/s, and notes
HOMIE's velocity tracking **plateaus past 8 GPUs** while SONIC keeps improving with compute.

> [!warning] Read the abstract before accepting SONIC's framing — inferred, ai-draft 2026-07-29
> HOMIE's policy is described here as **body control mapped to a pedal**, designed so an operator can
> walk and squat to specific heights *while the exoskeleton poses the upper body arbitrarily*. Its stated
> design goals are an upper-body pose curriculum, height tracking, and symmetry — **not high-speed
> velocity tracking**. SONIC characterizes it as "a state-of-the-art single-task locomotion controller
> optimized for upper body inverse kinematics control and lower-body velocity tracking" and then
> benchmarks it at up to 5 m/s.
>
> So the honest reading is narrower than SONIC's framing: SONIC beats a **teleoperation cockpit's
> pedal-driven walking policy** outside that policy's design envelope. That's still a result — HOMIE is
> open-source and widely used — but it is *not* evidence that specialization loses to scale on a task
> the specialist was built for. Worth checking the full HOMIE paper for its actual claimed velocity range
> before citing SONIC's 98.5%-vs-43.0% comparison anywhere.

## Concepts
- [[loco-manipulation]] — the cockpit's target capability, via teleoperation rather than autonomy.
- Proposed once read: [[sim-to-real-transfer]], and possibly a hardware/teleoperation note otto lacks.

## My notes
<!-- Your own reactions; how it relates to your work. -->

## Source
- arXiv: https://arxiv.org/abs/2502.13013 (v2, Apr 2025) · DOI: https://doi.org/10.48550/arXiv.2502.13013
- Open-source: https://homietele.github.io/
- Abstract quoted verbatim from arXiv. Role/critique section grounded in [[@luo2025sonic]] §2.1, §2.6.
