---
type: paper
citekey: qureshi2020motion
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Qureshi, Ahmed H.
- Miao, Yinglong
- Simeonov, Anthony
- Yip, Michael C.
year: 2020
venue: arXiv:1907.06013 [cs]
doi: null
arxiv: '1907.06013'
url: http://arxiv.org/abs/1907.06013
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@qureshi2020motion.pdf
doi: 10.1109/TRO.2020.3006716
bibkeys:
- qureshi_motion_2020
---

# Motion Planning Networks: Bridging the Gap Between Learning-based and Classical Motion Planners

> [!info] Qureshi, Ahmed H.; Miao, Yinglong; Simeonov, Anthony; Yip, Michael C. · 2020 · arXiv:1907.06013 [cs]

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — MPNet is a learning-based neural motion planner that learns near-optimal path-planning heuristics and, hybridized with a classical sampling-based planner, retains worst-case completeness guarantees while being far faster.
**Problem** — Classical sampling-based planners are general and come with guarantees but are computationally expensive; purely learned planners are fast but lack guarantees. The paper bridges the two.
**Method** — Neural networks encode the environment (e.g. raw point cloud from depth sensors) and, given start and goal configurations, recursively and bidirectionally generate connectable paths in a single pass. Merging this neural strategy with classical sample-based planners yields a hybrid with provable worst-case guarantees; an active continual-learning scheme lets MPNet learn from streaming data and query expert demonstrations only when needed, cutting training data.
**Key results** — Validated against gold-standard and state-of-the-art planners across 2D to 7D configuration spaces in cluttered environments, showing consistently stronger performance metrics (computation and optimality) than the baselines.

## Takeaways
- The core idea is a learned heuristic that biases search, with a classical planner as a fallback to preserve completeness/optimality guarantees — a template for "learning + guarantees" planning.
- Scales across dimensionality (2D–7D), including robot-arm configuration spaces, not just planar navigation.
- Active continual learning materially reduces the demonstration data needed, addressing a key practicality of learned planners.

## Relevance to your work
A key exemplar of hybrid learned/classical motion planning, cited by [[@csomayshanklin2025dynamically]] as the neural-planner reference against which structured, dynamically feasible planning is positioned.

## Abstract (from bib)
This paper describes Motion Planning Networks (MPNet)1, a computationally efﬁcient, learning-based neural planner for solving motion planning problems. MPNet uses neural networks to learn general near-optimal heuristics for path planning in seen and unseen environments. It takes environment information such as raw point-cloud from depth sensors, as well as a robot’s initial and desired goal conﬁgurations and recursively calls itself to bidirectionally generate connectable paths. In addition to ﬁnding directly connectable and near-optimal paths in a single pass, we show that worst-case theoretical guarantees can be proven if we merge this neural network strategy with classical sample-based planners in a hybrid approach while still retaining signiﬁcant computational and optimality improvemen

## Concepts


## Source
- Cited by [[@csomayshanklin2025dynamically]]
- bibkeys: `qureshi_motion_2020`
- arXiv: https://arxiv.org/abs/1907.06013
- URL: http://arxiv.org/abs/1907.06013
