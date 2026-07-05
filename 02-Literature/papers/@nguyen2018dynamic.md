---
type: paper
citekey: nguyen2018dynamic
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Nguyen, Quan
- Agrawal, Ayush
- Martin, William
- Geyer, Hartmut
- Sreenath, Koushil
year: 2018
venue: The International Journal of Robotics Research
doi: 10.1177/0278364918791718
arxiv: null
url: https://doi.org/10.1177/0278364918791718
summary: ai-draft
pdf: missing
zotero: null
status: to-read
mine: false
bibkeys:
- nguyen_dynamic_2018
---

# Dynamic bipedal locomotion over stochastic discrete terrain

> [!info] Nguyen, Quan; Agrawal, Ayush; Martin, William; Geyer, Hartmut; Sreenath, Koushil · 2018 · The International Journal of Robotics Research

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — Achieves planar dynamic bipedal walking over stochastically generated stepping stones using a precomputed gait library indexed by step length/height plus real-time gait interpolation, with only one-step-ahead foothold knowledge.
**Problem** — Dynamic walking over discrete footholds with large, stochastic variation in step length and height is hard, especially when the robot knows the next foothold only one step ahead.
**Method** — A two-step periodic gait optimization builds a library of gaits parametrized by resulting step length/height and initial robot configuration, explicitly handling step-transition problems when switching between gaits. Real-time gait interpolation then selects the desired gait online.
**Key results** — Validated on ATRIAS (underactuated, human-scale): step lengths varied over [23, 78] cm with fixed height; with both varied, step length [30, 65] cm and step height [−22, 22] cm, at an average speed of ~0.6 m/s.

## Takeaways
- Gait-library + interpolation is a precomputation-heavy alternative to online MPC for discrete-terrain walking, trading offline optimization for cheap online lookup.
- Explicitly addresses gait-transition dynamics — the hard part when composing a library into a continuous walk.
- Only one-step foothold preview required, matching realistic perception limits on stepping-stone terrain.

## Abstract (from bib)
Owing to their morphology and mechanical design, bipedal robots have the ability to traverse over a wide range of terrain including those with discrete footholds such as stepping stones. This paper addresses the challenge of planar dynamic robotic walking over stochastically generated stepping stones with significant variations in step length and step height, and where the robot has knowledge about the location of the next discrete foothold only one step ahead. Specifically, our approach utilizes a two-step periodic gait optimization technique to build a library of gaits parametrized by their resulting step lengths and step heights, as well as the initial configuration of the robot. By doing so, we address the problems involved during step transition when switching between the different wa

## Relevance to your work
A benchmark for dynamic bipedal locomotion over stochastic discrete footholds with one-step preview, relevant to discrete-terrain humanoid walking as in [[@dai2025walk]].

## Concepts


## Source
- Cited by [[@dai2025walk]]
- bibkeys: `nguyen_dynamic_2018`
- DOI: https://doi.org/10.1177/0278364918791718
