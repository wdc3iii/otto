---
type: paper
citekey: pokhrel2024cahsor
tags: [navigation, method]
aliases: []
created: '2026-07-06'
modified: '2026-07-06'
authors:
- Pokhrel, Anuj
- Datar, Aniket
- Nazeri, Mohammad
- Xiao, Xuesu
year: 2024
venue: IEEE Robotics and Automation Letters
doi: 10.1109/LRA.2024.3457369
arxiv: '2402.07065'
url: http://arxiv.org/abs/2402.07065
zotero: null
summary: ai-draft
pdf: attachments/@pokhrel2024cahsor.pdf
status: to-read
mine: false
bibkeys:
- pokhrelCAHSORCompetenceAwareHighSpeed2024
---

# CAHSOR: Competence-Aware High-Speed Off-Road Ground Navigation in SE(3)

> [!info] Anuj Pokhrel; Aniket Datar; Mohammad Nazeri; Xuesu Xiao · 2024 · IEEE Robotics and Automation Letters

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — Gives high-speed off-road vehicles competence awareness in SE(3) via a learned 6-DoF kinodynamic model, letting them reason about roll/slide/vibration consequences of aggressive maneuvers and cut instability with little speed loss.
**Problem** — Assuming an SE(2) workspace breaks down at high speed off-road: sharp turns on high-friction surfaces cause rollover, aggressive turns on gravel/grass violate non-holonomic constraints and cause lateral sliding, and rugged terrain produces vertical vibration — forcing most off-road vehicles to drive slowly for safety.
**Method** — CAHSOR: reason about maneuver consequences in SE(3) using a 6-DoF forward kinodynamic model, learned from visual + inertial Terrain Representation for Off-road Navigation (TRON) via multimodal self-supervised vehicle-terrain interactions; applied in both autonomous and human shared-control setups.
**Key results** — Reduces vehicle instability by 62% while compromising only 8.6% average speed on a physical ground robot.

## Takeaways
- Reframes competence/safety in full SE(3) rather than SE(2) — captures rollover, lateral slide, and vertical vibration.
- Learned 6-DoF kinodynamic model from self-supervised visual+inertial terrain interactions (TRON).
- Works both autonomously and as a shared-control safety filter; big stability gain at small speed cost.

## Relevance to your work
Strongly relevant to capability-aware navigation: CAHSOR is a concrete competence/capability-aware controller that predicts the dynamic consequences of maneuvers on terrain and constrains them — exactly the capability-awareness idea, ported to a wheeled SE(3) setting but conceptually transferable to legged capability limits.

## Abstract (from bib)
While the workspace of traditional ground vehicles is usually assumed to be in a 2D plane, i.e., SE(2), such an assumption may not hold when they drive at high speeds on unstructured off-road terrain: High-speed sharp turns on high-friction surfaces may lead to vehicle rollover; Turning aggressively on loose gravel or grass may violate the non-holonomic constraint and cause significant lateral sliding; Driving quickly on rugged terrain will produce extensive vibration along the vertical axis. Therefore, most offroad vehicles are currently limited to drive only at low speeds to assure vehicle stability and safety. In this work, we aim at empowering high-speed off-road vehicles with competence awareness in SE(3) so that they can reason about the consequences of taking aggressive maneuvers on different terrain with a 6-DoF forward kinodynamic model. The model is learned from visual and inertial Terrain Representation for Off-road Navigation (TRON) using multimodal, self-supervised vehicle-terrain interactions. We demonstrate the efficacy of our Competence-Aware High-Speed Off-Road (CAHSOR) navigation approach on a physical ground robot in both an autonomous navigation and a human shared-control setup and show that CAHSOR can efficiently reduce vehicle instability by 62% while only compromising 8.6% average speed with the help of TRON.

## Concepts
- [[capability-awareness]]
- [[traversability-estimation]]

## Source
- bibkeys: `pokhrelCAHSORCompetenceAwareHighSpeed2024`
- arXiv: http://arxiv.org/abs/2402.07065
- DOI: https://doi.org/10.1109/LRA.2024.3457369
- URL: http://arxiv.org/abs/2402.07065
