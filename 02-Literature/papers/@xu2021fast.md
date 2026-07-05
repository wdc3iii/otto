---
type: paper
citekey: xu2021fast
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Xu, Wei
- Zhang, Fu
year: 2021
venue: IEEE Robotics and Automation Letters
doi: 10.1109/LRA.2021.3064227
arxiv: '2010.08196'
url: https://arxiv.org/abs/2010.08196
summary: ai-draft
pdf: attachments/@xu2021fast.pdf
zotero: null
status: to-read
mine: false
bibkeys:
- xu2021fast
---

# Fast-lio: A fast, robust lidar-inertial odometry package by tightly-coupled iterated kalman filter

> [!info] Xu, Wei; Zhang, Fu · 2021 · IEEE Robotics and Automation Letters

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.

**TL;DR** — FAST-LIO is a computationally efficient, robust LiDAR-inertial odometry package fusing LiDAR features and IMU with a tightly-coupled iterated extended Kalman filter (iEKF).

**Problem** — LiDAR-inertial odometry degrades under fast motion, noise, and clutter, and standard iEKF updates scale with the (large) number of LiDAR measurements, making real-time onboard operation costly.

**Method** — Tightly couples LiDAR feature points with IMU data in an iterated EKF for robust state estimation. A new formula computes the Kalman gain with cost that scales with the state dimension rather than the measurement dimension, sharply reducing computation when many points are used.

**Key results** — Runs in real time on a quadrotor onboard computer, fusing 1200+ effective feature points per scan with each iEKF step completing within 25 ms; validated across indoor and outdoor environments and open-sourced.

## Takeaways
- The state-dimension Kalman-gain formula is the core efficiency trick, decoupling cost from the number of LiDAR points.
- Tight LiDAR-IMU coupling in an iEKF buys robustness to fast, aggressive motion.
- A practical, open-source odometry backbone rather than a new estimation theory.

## Relevance to your work
State estimation and odometry are the perception substrate for terrain-aware legged navigation; FAST-LIO-class odometry supplies the pose/map a locomotion planner like [[@terrain2026consistent]] consumes.

## Concepts
<!-- [[03-Concepts]] links added when read -->

## Source
- Cited by [[@terrain2026consistent]]
- bibkeys: `xu2021fast`
