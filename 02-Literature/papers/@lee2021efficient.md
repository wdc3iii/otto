---
type: paper
citekey: lee2021efficient
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Lee, Jaemin
- Bakolas, Efstathios
- Sentis, Luis
year: 2021
venue: Autonomous Robots
doi: 10.1007/s10514-020-09952-7
arxiv: null
url: https://doi.org/10.1007/s10514-020-09952-7
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: missing
bibkeys:
- lee2021efficient
---

# An efficient and direct method for trajectory optimization of robots constrained by contact kinematics and forces

> [!info] Lee, Jaemin; Bakolas, Efstathios; Sentis, Luis · 2021 · Autonomous Robots

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — A direct trajectory-optimization method for contact-constrained robots that avoids linearizing the nonlinear coupled dynamics and contact constraints, decomposing the problem into cheaper subproblems for efficiency.
**Problem** — For robots subject to contact kinematics and contact-force constraints, the dynamics and constraints are nonlinear and mutually coupled; conventional approaches linearize the model and constraints, sacrificing fidelity or robustness.
**Method** — Rather than linearizing, the method directly solves the optimal control problem for feasible state trajectories and control inputs, and subdivides trajectory generation into tractable subproblems: a sampling problem, a convex optimization problem, and a nonlinear program. This structure reduces computational cost while respecting reachability and contact-force feasibility.
**Key results** — Reports significant reduction in computational cost versus solving the coupled nonlinear problem directly, yielding feasible contact-constrained trajectories (validated on robotic systems in the paper).

## Takeaways
- Central idea: exploit reachability/convex structure to split a hard contact-constrained OCP into a sampling + convex + NLP pipeline rather than one monolithic nonlinear solve.
- Keeps the true nonlinear contact model instead of linearizing, trading a bespoke decomposition for accuracy.
- Contact-force constraints (friction cones, complementarity-type conditions) are treated as first-class, targeting legged/manipulation systems.

## Relevance to your work
Directly relevant to whole-body/contact-rich trajectory optimization for legged robots; a candidate low-level generator whose feasible motions a hierarchical or reduced-order planner such as [[@csomayshanklin2025dynamically]] would coordinate at the template level.

## Concepts

## Source
- Cited by [[@csomayshanklin2025dynamically]], [[@hierarchies2025motion]]
- bibkeys: `lee2021efficient`
