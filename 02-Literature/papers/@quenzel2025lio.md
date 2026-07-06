---
type: paper
citekey: quenzel2025lio
tags: [navigation, method]
aliases: []
created: '2026-07-06'
modified: '2026-07-06'
authors:
- Quenzel, Jan
- Behnke, Sven
year: 2025
venue: arXiv
doi: 10.48550/arXiv.2511.13985
arxiv: '2511.13985'
url: http://arxiv.org/abs/2511.13985
zotero: null
summary: ai-draft
pdf: attachments/@quenzel2025lio.pdf
status: to-read
mine: false
bibkeys:
- quenzelLIOMARSNonuniformContinuoustime2025
---

# LIO-MARS: Non-uniform Continuous-time Trajectories for Real-time LiDAR-Inertial-Odometry

> [!info] Jan Quenzel; Sven Behnke · 2025 · arXiv

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — A LiDAR-inertial odometry system that jointly aligns multi-resolution surfel maps with a GMM over a non-uniform continuous-time B-spline trajectory for robust real-time state estimation.
**Problem** — Autonomous robots (here, flying search-and-rescue platforms) need robust real-time perception fusing IMU (acceleration/rotation constraints) and LiDAR (accurate range) for safe navigation.
**Method** — Builds on the MARS LiDAR odometry: aligns multi-resolution surfel maps against a Gaussian mixture model using a continuous-time B-spline trajectory; a new scan window uses non-uniform temporal knot placement for trajectory continuity without added scan delay; an unscented transform de-skews surfels and intra-scan segmentation enables motion compensation during spline optimization; soft constraints on relative poses and preintegrated IMU pseudo-measurements add robustness. Covariance/GMM computation accelerated via Kronecker sums/products.
**Key results** — Reports a 3.3x speedup on essential covariance and GMM computations, and state-of-the-art quality vs. recent LIO systems on handheld, ground, and aerial datasets (no other numeric figures read).

## Takeaways
- Non-uniform knot placement on a continuous-time B-spline gives whole-trajectory continuity without incurring extra scan latency.
- Kronecker-structured math yields a concrete 3.3x speedup on the covariance/GMM bottleneck.
- Surfel de-skewing (unscented transform) + intra-scan motion compensation folded directly into spline optimization.

## Relevance to your work
State estimation / odometry is upstream infrastructure for navigation autonomy; a robust real-time LIO could feed the perception stack for terrain-aware or mapless navigation on legged platforms, though this paper targets aerial/ground vehicles rather than humanoid locomotion specifically.

## Abstract (from bib)
Autonomous robotic systems heavily rely on environment knowledge to safely navigate. For search & rescue, a flying robot requires robust real-time perception, enabled by complementary sensors. IMU data constrains acceleration and rotation, whereas LiDAR measures accurate distances around the robot. Building upon the LiDAR odometry MARS, our LiDAR-inertial odometry (LIO) jointly aligns multi-resolution surfel maps with a Gaussian mixture model (GMM) using a continuous-time B-spline trajectory. Our new scan window uses non-uniform temporal knot placement to ensure continuity over the whole trajectory without additional scan delay. Moreover, we accelerate essential covariance and GMM computations with Kronecker sums and products by a factor of 3.3. An unscented transform de-skews surfels, while a splitting into intra-scan segments facilitates motion compensation during spline optimization. Complementary soft constraints on relative poses and preintegrated IMU pseudo-measurements further improve robustness and accuracy. Extensive evaluation showcases the state-of-the-art quality of our LIO-MARS w.r.t. recent LIO systems on various handheld, ground and aerial vehicle-based datasets.

## Concepts
<!-- [[03-Concepts]] links added when read -->

## Source
- bibkeys: `quenzelLIOMARSNonuniformContinuoustime2025`
- arXiv: http://arxiv.org/abs/2511.13985
- DOI: https://doi.org/10.48550/arXiv.2511.13985
- URL: http://arxiv.org/abs/2511.13985
