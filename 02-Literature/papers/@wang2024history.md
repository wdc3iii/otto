---
type: paper
citekey: wang2024history
tags: [navigation, planning]
aliases: []
created: '2026-07-06'
modified: '2026-07-06'
authors:
- Wang, Yinchuan
- Du, Nianfei
- Qin, Yongsen
- Zhang, Xiang
- Song, Rui
- Wang, Chaoqun
year: 2024
venue: '2024 IEEE International Conference on Robotics and Automation (ICRA)'
doi: 10.1109/ICRA57147.2024.10610488
arxiv: '2406.01928'
url: http://arxiv.org/abs/2406.01928
zotero: null
summary: ai-draft
pdf: attachments/@wang2024history.pdf
status: to-read
mine: false
bibkeys:
- wangHistoryAwarePlanningRiskfree2024
---

# History-Aware Planning for Risk-free Autonomous Navigation on Unknown Uneven Terrain

> [!info] Yinchuan Wang; Nianfei Du; Yongsen Qin; Xiang Zhang; Rui Song; Chaoqun Wang · 2024 · 2024 IEEE International Conference on Robotics and Automation (ICRA)

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — A layered mapless navigation pipeline that grows a local tree unifying planning with terrain identification and keeps selected nodes as a sparse global graph recording exploration history, using subgoals to guide safe traversal of unknown uneven terrain.
**Problem** — Autonomous, mapless navigation of a mobile robot through unknown environments with uneven terrain is challenging and safety-critical.
**Method** — A layered pipeline: at the local level, a tree structure is dynamically extended during navigation, unifying planning with terrain identification and explicitly flagging hazardous areas on uneven terrain. At the global level, certain tree nodes are retained to form a sparse graph recording the exploration history. Subgoals drawn from the tree and graph lead the navigation, selected via an evaluation method whose input elements are efficiently obtained from the layered structure.
**Key results** — Simulation and real-world experiments show the robot travels safely through unknown uneven regions and reaches targets rapidly without a preconstructed map (no numeric figures read).

## Takeaways
- Local tree unifies motion planning with terrain identification and explicit hazard flagging in one structure.
- Retaining select nodes into a sparse global graph gives history-aware exploration without a full map.
- Subgoal selection uses features cheaply computed from the layered tree/graph.

## Relevance to your work
On-target for mapless, terrain-aware navigation autonomy: the history-aware tree/graph structure and explicit hazard/traversability flagging are relevant to capability-aware navigation on uneven terrain, though demonstrated on a wheeled/mobile robot rather than a legged platform.

## Abstract (from bib)
It is challenging for the mobile robot to achieve autonomous and mapless navigation in the unknown environment with uneven terrain. In this study, we present a layered and systematic pipeline. At the local level, we maintain a tree structure that is dynamically extended with the navigation. This structure unifies the planning with the terrain identification. Besides, it contributes to explicitly identifying the hazardous areas on uneven terrain. In particular, certain nodes of the tree are consistently kept to form a sparse graph at the global level, which records the history of the exploration. A series of subgoals that can be obtained in the tree and the graph are utilized for leading the navigation. To determine a subgoal, we develop an evaluation method whose input elements can be efficiently obtained on the layered structure. We conduct both simulation and real-world experiments to evaluate the developed method and its key modules. The experimental results demonstrate the effectiveness and efficiency of our method. The robot can travel through the unknown uneven region safely and reach the target rapidly without a preconstructed map.

## Concepts
- [[mapless-navigation]]
- [[traversability-estimation]]
- [[topological-navigation]]

## Source
- bibkeys: `wangHistoryAwarePlanningRiskfree2024`
- arXiv: http://arxiv.org/abs/2406.01928
- DOI: https://doi.org/10.1109/ICRA57147.2024.10610488
- URL: http://arxiv.org/abs/2406.01928
