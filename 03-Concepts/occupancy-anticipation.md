---
type: concept
tags: [navigation, method, to-revisit]
aliases: [Occupancy anticipation, map anticipation, occupancy prediction, visibility masking]
created: 2026-07-29
modified: 2026-07-29
---

# Occupancy anticipation

> [!note] AI-drafted base, created 2026-07-29 alongside the ingest of [[auxiliary-prediction-heads]].
> Refine or reject.

## Definition
Predicting occupancy (or terrain class, or height) **beyond the currently visible region** — behind the
robot, around a corner, under an occluding tread — rather than reconstructing what the sensor can
already see. Operationally: a per-cell **visibility mask** on the loss, so only the unseen part is
supervised.

## Intuition / why it matters
The masking is the whole idea, and it's what converts a perception task into a memory task:

> Predicting the visible part is encoder reconstruction; predicting the occluded/behind part is memory.
> — [[auxiliary-prediction-heads]] §0

That distinction is why this is a first-class option rather than an implementation detail. A head
predicting the *visible* occupancy can be satisfied by the current frame and shapes only the encoder; a
head predicting the *invisible* occupancy can only succeed by storing something, which puts pressure
exactly where the reward gradient is weakest ([[belief-state]]).

[[@ramakrishnan2020occupancy]] is the evidence that the unseen region is learnable at useful accuracy
at all — and that an anticipated map improves downstream exploration and navigation, not just
reconstruction metrics.

A second, sharper variant: anticipate not occupancy but a **potential field** over the map.
[[@ramakrishnan2022poni|PONI]] predicts an explicitly **geodesic-distance-based** object potential by
supervised learning on a passive dataset — which is the closest published precedent for treating a
wavefront/geodesic field as a supervised prediction target rather than a privileged critic input.

## Grounding
- **The masking design + learnability evidence:** [[@ramakrishnan2020occupancy]] (Occupancy
  Anticipation, ECCV 2020 — occupancy beyond the visible region from egocentric RGB-D).
- **Geodesic potential as a supervised target:** [[@ramakrishnan2022poni]] (PONI, CVPR 2022).
- **The maximal version — supervise the whole map module:** [[@chaplot2020learning]] (Active Neural
  SLAM: map + pose trained with explicit supervised losses, RL reserved for the policies).
- **As a standalone perception problem on legged platforms:** [[@shi2026oneocc]] (OneOcc — semantic
  occupancy for legged robots from one panoramic camera; useful as an upper bound on what an aux head
  could be expected to represent).
- **As an RL aux target, ranked highest by ablation:** [[@ye2021auxiliary]] (coverage prediction).
- **Output parameterisation, polar/range-view:** [[@kong2023rethinking]] (RangeFormer — bearing-indexed
  2D output is workable, with seam/discontinuity failure modes) · [[@xue2024pvp]] (polar occupancy).
  Note neither uses these as an RL auxiliary — the radial variant has no direct RL precedent.

## Related
- [[auxiliary-task-learning]] — the mechanism this is usually deployed through.
- [[belief-state]] — what the visibility mask is trying to shape.
- [[traversability-estimation]] · [[mapless-navigation]] · [[privileged-information]]

## Open questions
- **How far beyond the visible is learnable?** [[@ramakrishnan2020occupancy]] establishes "useful
  accuracy" for indoor RGB-D; unclear how that transfers to outdoor/campus geometry and a lidar-derived
  occupancy lattice.
- **Is anticipating the field redundant with a reward already shaped by it?** If dense geodesic
  progress shaping is already in the reward, an aux head predicting a wavefront-derived quantity is
  partly predicting its own reward signal — the occupancy and visitation targets are less entangled.
  (Your §6 risk #4.)
