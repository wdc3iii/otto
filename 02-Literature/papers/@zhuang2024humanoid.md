---
type: paper
citekey: zhuang2024humanoid
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-06'
authors:
- Zhuang, Ziwen
- Yao, Shenzhe
- Zhao, Hang
year: 2024
venue: arXiv preprint arXiv:2406.10759
doi: null
arxiv: '2406.10759'
url: https://arxiv.org/abs/2406.10759
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@zhuang2024humanoid.pdf
bibkeys:
- zhuang2024humanoid
- zhuangHumanoidParkourLearning2024
---

# Humanoid parkour learning

> [!info] Zhuang, Ziwen; Yao, Shenzhe; Zhao, Hang · 2024 · arXiv preprint arXiv:2406.10759

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.

**TL;DR** — An end-to-end, vision-based whole-body-control policy that lets a humanoid perform multiple parkour skills with no motion prior.

**Problem** — Enabling humanoids to traverse challenging obstacles (platforms, hurdles, gaps) with agile, whole-body skills, without hand-designed reference motions or motion capture.

**Method** — Learns a single end-to-end vision-based whole-body-control parkour policy that acquires multiple skills without any motion prior, selecting the appropriate parkour behavior from joystick commands. The framework also adapts to mobile manipulation by overriding the arm motions.

**Key results** — On real hardware: jumping onto 0.42 m platforms, clearing hurdles and 0.8 m gaps, and running at 1.8 m/s outdoors, with robust traversal across varied terrain types.

## Takeaways
- Demonstrates motion-prior-free, purely learned humanoid parkour — no reference trajectories or mocap needed.
- Single policy multiplexes several agile skills, gated by joystick command; arm overriding gives a manipulation extension for free.
- Vision-in-the-loop whole-body control shown to transfer to outdoor real-world settings.

## Relevance to your work
A landmark demonstration of agile perceptive humanoid locomotion via end-to-end RL, useful as a baseline/contrast for perception-conditioned terrain traversal work like [[@terrain2026consistent]].

## Concepts
[[massively-parallel-simulation]]


## Source
- Cited by [[@terrain2026consistent]]
- bibkeys: `zhuang2024humanoid`
- arXiv: https://arxiv.org/abs/2406.10759
