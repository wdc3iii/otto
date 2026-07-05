---
type: paper
citekey: lee2024asap
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Lee, Dong-Hyun
- Choi, Sunglok
- Na, Ki-In
year: 2024
venue: IEEe Access
doi: null
arxiv: null
url: https://ieeexplore.ieee.org/document/10600674/
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: missing
bibkeys:
- lee2024asap
---

# ASAP: Agile and safe pursuit for local planning of autonomous mobile robots

> [!info] Lee, Dong-Hyun; Choi, Sunglok; Na, Ki-In · 2024 · IEEe Access

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — ASAP (Agile and SAfe Pursuit) is a lightweight local planner for autonomous mobile robots that combines agile path following with safe obstacle avoidance while staying cheap enough for embedded real-time use.
**Problem** — Local planners must follow a path agilely and avoid collisions in cluttered environments, yet run in real time on embedded hardware with limited compute — objectives that usually trade off against each other.
**Method** — For agile following, it builds a local path from line segments, arcs, and in-place rotations, and generates a target velocity respecting the robot's kinematic constraints. For safe avoidance, it constructs "safety corners" — free-space points that route the robot around arbitrarily shaped obstacles — and picks the corner minimizing travel time.
**Key results** — Presented as computationally efficient for embedded, low-power platforms (IEEE Access, 2024); see paper for benchmark comparisons.

## Takeaways
- The "safety corner" construction is the distinctive element: obstacle avoidance via minimum-travel-time free-space waypoints rather than a full optimization or sampling loop.
- Explicitly targets embedded/low-compute deployment — the design is optimized for efficiency, not maximal optimality.
- Scoped to wheeled/ground mobile robots and geometric kinematic constraints, not legged whole-body dynamics.

## Relevance to your work
A lightweight local-planning / obstacle-avoidance baseline for the navigation-autonomy layer — cited in [[@terrain2026consistent]] as prior art on real-time agile-yet-safe local motion for mobile robots.

## Concepts


## Source
- Cited by [[@terrain2026consistent]]
- bibkeys: `lee2024asap`
