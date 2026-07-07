---
type: paper
citekey: frey2025boxi
tags: [hardware, navigation]
aliases: []
created: '2026-07-06'
modified: '2026-07-07'
authors:
- Frey, Jonas
- Tuna, Turcan
- Fu, Lanke Frank Tarimo
- Weibel, Cedric
- Patterson, Katharine
- Krummenacher, Benjamin
- Müller, Matthias
- Nubert, Julian
- Fallon, Maurice
- Cadena, Cesar
- Hutter, Marco
year: 2025
venue: arXiv
doi: 10.48550/arXiv.2504.18500
arxiv: '2504.18500'
url: http://arxiv.org/abs/2504.18500
zotero: null
summary: ai-draft
pdf: attachments/@frey2025boxi.pdf
status: to-read
mine: false
bibkeys:
- freyBoxiDesignDecisions2025
---

# Boxi: Design Decisions in the Context of Algorithmic Performance for Robotics

> [!info] Jonas Frey; Turcan Tuna; Lanke Frank Tarimo Fu; Cedric Weibel; Katharine Patterson; Benjamin Krummenacher; Matthias Müller; Julian Nubert; Maurice Fallon; Cesar Cadena; Marco Hutter · 2025 · arXiv

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — Boxi is a tightly integrated multimodal sensor payload for mobile-robot autonomy in the wild, presented alongside an analysis of how payload design decisions (synchronization, calibration, sensor modality) impact state estimation and mapping.
**Problem** — Designing a robust multimodal sensor suite involves many critical, interacting design decisions (sensor selection, placement, thermal/power limits, compute, networking, synchronization, calibration) that are often overlooked in academia or kept proprietary.
**Method** — Present Boxi (2 LiDARs, 10 RGB cameras incl. HDR/global-shutter/rolling-shutter, an RGB-D camera, 7 IMUs of varying precision, dual-antenna RTK GNSS) and analyze design-decision impact on downstream state estimation and mapping, framed by cost and environment-specific challenges; also provide a mobile sensor-suite "cookbook" of generalizable design guidelines.
**Key results** — Analysis shows time synchronization, calibration, and sensor modality have crucial impact on state-estimation performance; Boxi demonstrated across varied real-world applications (no numeric figures read). Code: github.com/leggedrobotics/grand_tour_box.

## Takeaways
- A rare, explicit treatment of sensor-payload engineering as a first-class determinant of downstream algorithmic (state estimation / mapping) performance.
- Time synchronization and calibration are called out as the highest-leverage design factors — not just which sensors you pick.

## Relevance to your work
Tangential to the control/RL core, but a practical reference if building or spec'ing a perception payload for perceptive locomotion/navigation on the G1 — especially the synchronization/calibration lessons for reliable state estimation.

## Abstract (from bib)
Achieving robust autonomy in mobile robots operating in complex and unstructured environments requires a multimodal sensor suite capable of capturing diverse and complementary information. However, designing such a sensor suite involves multiple critical design decisions, such as sensor selection, component placement, thermal and power limitations, compute requirements, networking, synchronization, and calibration. While the importance of these key aspects is widely recognized, they are often overlooked in academia or retained as proprietary knowledge within large corporations. To improve this situation, we present Boxi, a tightly integrated sensor payload that enables robust autonomy of robots in the wild. This paper discusses the impact of payload design decisions made to optimize algorithmic performance for downstream tasks, specifically focusing on state estimation and mapping. Boxi is equipped with a variety of sensors: two LiDARs, 10 RGB cameras including high-dynamic range, global shutter, and rolling shutter models, an RGB-D camera, 7 inertial measurement units (IMUs) of varying precision, and a dual antenna RTK GNSS system. Our analysis shows that time synchronization, calibration, and sensor modality have a crucial impact on the state estimation performance. We frame this analysis in the context of cost considerations and environment-specific challenges. We also present a mobile sensor suite `cookbook` to serve as a comprehensive guideline, highlighting generalizable key design considerations and lessons learned during the development of Boxi. Finally, we demonstrate the versatility of Boxi being used in a variety of applications in real-world scenarios, contributing to robust autonomy. More details and code: https://github.com/leggedrobotics/grand_tour_box

## Concepts
- [[state-estimation]] — analyzes how sensor-payload design (synchronization, calibration, modality) determines downstream state-estimation and mapping performance.

## Source
- bibkeys: `freyBoxiDesignDecisions2025`
- arXiv: http://arxiv.org/abs/2504.18500
- DOI: https://doi.org/10.48550/arXiv.2504.18500
- URL: http://arxiv.org/abs/2504.18500
