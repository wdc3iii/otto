---
type: paper
citekey: nilsson1969mobile
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Nilsson, Nils J.
year: 1969
venue: null
doi: 10.21236/ADA459660
arxiv: null
url: http://www.dtic.mil/docs/citations/ADA459660
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: missing
bibkeys:
- nilsson_mobile_1969
---

# A Mobile Automaton: An Application of Artificial Intelligence Techniques:

> [!info] Nilsson, Nils J. · 1969 · —

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — The SRI "Shakey"-era report on an integrated mobile robot that senses, models its world, and plans sequences of actions to accomplish tasks, using formal theorem-proving for high-level planning.
**Problem** — How to build a complete robot system that ties together sensing, world modeling, and action planning into an efficient whole capable of performing a range of tasks in a real environment, rather than solving any single perception or planning subproblem in isolation.
**Method** — An experimental facility of an SDS-940 computer controlling a wheeled vehicle carrying a TV camera and other sensors. The software processes sensory data, stores relevant information about the environment, and plans the sequence of motor actions needed for a task; a novel feature is using a formal theorem-proving system to plan execution of high-level functions as sequences of lower-level ones, recursively requiring further planning at lower levels.
**Key results** — A working system in which the robot rearranges simple objects by pushing them, demonstrating the integration of planning, world models, and sensory processing on a physical platform.

## Takeaways
- Foundational statement of the perceive-model-plan-act architecture that grounds classical robot autonomy; motion planning is one layer inside a hierarchy of planning at multiple abstraction levels.
- The recursive decomposition of high-level goals into lower-level plans (via theorem proving) is an early articulation of hierarchical / layered planning.
- Historical baseline: capabilities are modest by modern standards, but the systems framing is what endures.

## Relevance to your work
A canonical origin point for autonomous mobile robot navigation, cited to situate modern learning- or planning-based navigation pipelines against the classical sense-plan-act lineage that [[@csomayshanklin2025dynamically]] builds on.

## Concepts


## Source
- Cited by [[@csomayshanklin2025dynamically]]
- bibkeys: `nilsson_mobile_1969`
- DOI: https://doi.org/10.21236/ADA459660
- URL: http://www.dtic.mil/docs/citations/ADA459660
