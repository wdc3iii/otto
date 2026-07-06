---
type: paper
citekey: dai2023data
tags: [locomotion, control]
aliases: []
created: '2026-07-06'
modified: '2026-07-06'
authors:
- Dai, Min
- Xiong, Xiaobin
- Lee, Jaemin
- Ames, Aaron D.
year: 2023
venue: arXiv
doi: 10.48550/arXiv.2209.08458
arxiv: '2209.08458'
url: http://arxiv.org/abs/2209.08458
zotero: null
summary: ai-draft
pdf: attachments/@dai2023data.pdf
status: to-read
mine: false
bibkeys:
- daiDatadrivenAdaptationRobust2023
---

# Data-Driven Adaptation for Robust Bipedal Locomotion with Step-to-Step Dynamics

> [!info] Min Dai; Xiaobin Xiong; Jaemin Lee; Aaron D. Ames · 2023 · arXiv

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — An online, data-driven adaptive representation of step-to-step (S2S) dynamics synthesizes agile bipedal walking that adapts to unknown environments, model errors, and disturbances.
**Problem** — S2S dynamics enable dynamic walking on underactuated robots but assume known dynamics and environments; real deployment faces uncertain models, disturbances, and terrain.
**Method** — Learn a data-driven representation of the S2S dynamics via an adaptive-control approach that is data-efficient and easy to implement. The learned S2S controller outputs desired discrete foot placement, realized on the full-order robot by tracking outputs synthesized from that foot placement.
**Key results** — In high-fidelity Cassie simulation: improves velocity tracking versus a non-adaptive baseline and maintains stable, agile locomotion under unmodeled payload, large model errors, external disturbance forces, biased velocity estimation, and sloped terrain. (no numeric figures read)

## Takeaways
- Adaptive control learns the S2S (discrete step-to-step) dynamics online rather than assuming a fixed known model.
- Two-layer structure: learned S2S controller sets desired foot placement; full-order output tracking realizes it — a reduced-order-to-full-order pattern.
- Robustness demonstrated across a broad disturbance battery (payload, model error, force pushes, biased state estimate, slopes).

## Relevance to your work
Ames-group work directly on your reduced-order + adaptive-control line: learning the S2S map for robust foot-placement under model/environment uncertainty is a template for robust humanoid walking on the G1, complementary to tube-MPC / tracking-error-bound approaches.

## Abstract (from bib)
This paper presents an online framework for synthesizing agile locomotion for bipedal robots that adapts to unknown environments, modeling errors, and external disturbances. To this end, we leverage step-to-step (S2S) dynamics which has proven effective in realizing dynamic walking on underactuated robots -- assuming known dynamics and environments. This paper considers the case of uncertain models and environments and presents a data-driven representation of the S2S dynamics that can be learned via an adaptive control approach that is both data-efficient and easy to implement. The learned S2S controller generates desired discrete foot placement, which is then realized on the full-order dynamics of the bipedal robot by tracking desired outputs synthesized from the given foot placement. The benefits of the proposed approach are twofold. First, it improves the ability of the robot to walk at a given desired velocity when compared to the non-adaptive baseline controller. Second, the data-driven approach enables stable and agile locomotion under the effect of various unknown disturbances: additional unmodeled payload, large robot model errors, external disturbance forces, biased velocity estimation, and sloped terrains. This is demonstrated through in-depth evaluation with a high-fidelity simulation of the bipedal robot Cassie subject to the aforementioned disturbances.

## Concepts
- [[step-to-step-dynamics]]
- [[reduced-order-model]]

## Source
- bibkeys: `daiDatadrivenAdaptationRobust2023`
- arXiv: http://arxiv.org/abs/2209.08458
- DOI: https://doi.org/10.48550/arXiv.2209.08458
- URL: http://arxiv.org/abs/2209.08458
