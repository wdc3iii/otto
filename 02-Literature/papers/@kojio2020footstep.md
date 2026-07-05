---
type: paper
citekey: kojio2020footstep
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Kojio, Yuta
- Omori, Yuki
- Kojima, Kunio
- Sugai, Fumihito
- Kakiuchi, Yohei
- Okada, Kei
- Inaba, Masayuki
year: 2020
venue: IEEE Robotics and Automation Letters
doi: 10.1109/LRA.2020.3004796
arxiv: null
url: https://doi.org/10.1109/LRA.2020.3004796
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: missing
bibkeys:
- kojio_footstep_2020
---

# Footstep Modification Including Step Time and Angular Momentum Under Disturbances on Sparse Footholds

> [!info] Kojio, Yuta; Omori, Yuki; Kojima, Kunio; Sugai, Fumihito; Kakiuchi, Yohei; Okada, Kei · 2020 · IEEE Robotics and Automation Letters

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — A footstep-modification method that, given foothold constraints, adjusts step position, step timing, and angular momentum together so a biped can stay balanced under disturbances even on sparse footholds.
**Problem** — Few methods jointly respect foothold constraints and balance; on sparse footholds (e.g., stepping stones) a robot may be unable to recover because admissible landing positions are strictly limited.
**Method** — The steppable region is represented as convex hulls, and the walking parameters — step position, step timing, and angular momentum — are computed analytically by applying the authors' prior modification method within that constrained region.
**Key results** — Validated on a life-sized humanoid walking on stepping stones made of unsteady blocks, recovering from pushes despite tightly limited steppable regions.

## Takeaways
- When landing position alone is insufficient (sparse footholds), also modulating step timing and angular momentum recovers balance.
- Convex-hull representation of steppable regions yields an analytic (not heavy-optimization) modification rule.
- Demonstrated on real hardware over stepping stones, a genuinely constrained-foothold scenario.

## Relevance to your work
Complements step-timing viability work by adding angular-momentum and steppable-region constraints; relevant to any dynamic footstep controller that must handle sparse, constrained footholds like [[@dai2025walk]].

## Abstract (from bib)
Maintaining dynamic balance is an important requirement for bipedal robots. To deal with large disturbances, the footsteps need to be modiﬁed depending on the disturbance. Currently, there are few methods that determine footsteps by considering foothold constraints and the balance of the robot. In this paper, we propose a footstep modiﬁcation method that considers the steppable region. In certain situations, robots cannot maintain balance due to the limitations of the landing position on sparse footholds, such as stepping stones. Therefore, our proposed method modiﬁes not only the step position, but also the step timing and the angular momentum, and balance can be maintained even on the footholds where the steppable region is strictly limited. These walking parameters are analytically calc

## Concepts
[[reduced-order-model]]

## Source
- Cited by [[@dai2025walk]]
- bibkeys: `kojio_footstep_2020`
- DOI: https://doi.org/10.1109/LRA.2020.3004796
