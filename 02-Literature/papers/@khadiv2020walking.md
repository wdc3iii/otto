---
type: paper
citekey: khadiv2020walking
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Khadiv, Majid
- Herzog, Alexander
- Moosavian, S. Ali. A.
- Righetti, Ludovic
year: 2020
venue: IEEE Transactions on Robotics
doi: 10.1109/TRO.2020.2982584
arxiv: 1704.01271
url: https://arxiv.org/abs/1704.01271
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@khadiv2020walking.pdf
bibkeys:
- khadiv_walking_2020
---

# Walking Control Based on Step Timing Adaptation

> [!info] Khadiv, Majid; Herzog, Alexander; Moosavian, S. Ali. A.; Righetti, Ludovic · 2020 · IEEE Transactions on Robotics

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — A walking pattern generator that selects both the next step location and its timing at every control cycle, guaranteeing that any viable state stays viable.
**Problem** — Step-timing adaptation is usually neglected because optimizing it over multiple footsteps is nonconvex, yet timing adaptation is key to robustness under disturbances.
**Method** — The authors argue that instead of optimizing over many steps, it suffices to select only the next step's timing and location; this yields a computationally simple per-cycle optimization with a viability guarantee. It adds a swing-foot adaptation strategy and pairs the generator with an inverse-dynamics controller that does not explicitly control the CoM or foot center of pressure.
**Key results** — Extensive humanoid simulations (robot with passive ankles) under external pushes and foot slippage show step-timing adaptation is important for stabilizing walking, especially for robots with limited CoP authority (point feet / passive ankles).

## Takeaways
- Reducing the horizon to the single next step sidesteps the nonconvexity of multi-step timing optimization while preserving gait viability.
- Adapting step timing (not just location) is essential for robots that cannot rely on ankle CoP modulation.
- Controller avoids explicit CoM/CoP tracking, which suits underactuated feet — a deliberate design choice worth noting.

## Relevance to your work
A reduced-order, viability-based step timing/location adaptation scheme directly relevant to dynamic footstep control; contrasts with learned walking policies such as [[@dai2025walk]] on how disturbance robustness is achieved.

## Abstract (from bib)
Step adjustment can improve the gait robustness of biped robots; however, the adaptation of step timing is often neglected as it gives rise to nonconvex problems when optimized over several footsteps. In this article, we argue that it is not necessary to optimize walking over several steps to ensure gait viability and show that it is sufficient to merely select the next step timing and location. Using this insight, we propose a novel walking pattern generator that optimally selects step location and timing at every control cycle. Our approach is computationally simple compared to standard approaches in the literature, yet guarantees that any viable state will remain viable in the future. We propose a swing foot adaptation strategy and integrate the pattern generator with an inverse dynamic

## Concepts
[[reduced-order-model]]

## Source
- Cited by [[@dai2025walk]]
- bibkeys: `khadiv_walking_2020`
- DOI: https://doi.org/10.1109/TRO.2020.2982584
