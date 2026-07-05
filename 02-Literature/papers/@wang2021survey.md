---
type: paper
citekey: wang2021survey
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Wang, Jiankun
- Zhang, Tianyi
- Ma, Nachuan
- Li, Zhaoting
- Ma, Han
- Meng, Fei
- Meng, Max Q.-H.
year: 2021
venue: IET Cyber-Systems and Robotics
doi: 10.1049/csy2.12020
arxiv: null
url: https://onlinelibrary.wiley.com/doi/abs/10.1049/csy2.12020
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: missing
bibkeys:
- wang_survey_2021
---

# A survey of learning-based robot motion planning

> [!info] Wang, Jiankun; Zhang, Tianyi; Ma, Nachuan; Li, Zhaoting; Ma, Han; Meng, Fei · 2021 · IET Cyber-Systems and Robotics

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — A survey of learning-based approaches to robot motion planning, organizing supervised, unsupervised, and reinforcement-learning methods and their integration with classical planners.
**Problem** — Classical collision-free motion planning struggles in high-dimensional spaces and complex environments; learning-based methods have recently shown advantages there, but the landscape needed organizing.
**Method** — Reviews learning-based motion-planning methods across supervised, unsupervised, and RL paradigms, distinguishing those that rely on human-crafted task reward functions from those that learn from successful planning experience. Provides both the classical and learning-oriented formulations of the motion-planning problem.
**Key results** — A taxonomy of learning-based planners and a discussion of how classical motion planning and learning techniques can be combined.

## Takeaways
- Survey/reference, not a new method — useful as an entry point and for its classical-vs-learning problem framing.
- Splits the field along reward-driven (RL) vs experience-driven (imitation/supervised) axes.
- Emphasizes hybrid classical+learning planners as the promising direction.

## Relevance to your work
A convenient citation for positioning learning-based planning against classical planning in the navigation/autonomy stack that sits above a legged robot's locomotion controller.

## Abstract (from bib)
A fundamental task in robotics is to plan collision-free motions among a set of obstacles. Recently, learning-based motion-planning methods have shown significant advantages in solving different planning problems in high-dimensional spaces and complex environments. This article serves as a survey of various different learning-based methods that have been applied to robot motion-planning problems, including supervised, unsupervised learning, and reinforcement learning. These learning-based methods either rely on a human-crafted reward function for specific tasks or learn from successful planning experiences. The classical definition and learning-related definition of motion-planning problem are provided in this article. Different learning-based motion-planning algorithms are introduced, and

## Concepts


## Source
- Cited by [[@csomayshanklin2025dynamically]]
- bibkeys: `wang_survey_2021`
- DOI: https://doi.org/10.1049/csy2.12020
- URL: https://onlinelibrary.wiley.com/doi/abs/10.1049/csy2.12020
