---
type: paper
citekey: tedrake2010lqr
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Tedrake, Russ
- Manchester, Ian R
- Tobenkin, Mark
- Roberts, John W
year: 2010
venue: The International Journal of Robotics Research
doi: 10.1177/0278364910369189
arxiv: null
url: https://journals.sagepub.com/doi/10.1177/0278364910369189
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@tedrake2010lqr.pdf
bibkeys:
- tedrake2010lqr
---

# LQR-trees: Feedback motion planning via sums-of-squares verification

> [!info] Tedrake, Russ; Manchester, Ian R; Tobenkin, Mark; Roberts, John W · 2010 · The International Journal of Robotics Research

## Summary
> [!note] AI-drafted from the abstract / technical report — a base to refine.
**TL;DR** — LQR-Trees stitch locally-valid LQR controllers into a nonlinear feedback policy whose sums-of-squares-certified regions of attraction probabilistically cover the controllable state space.
**Problem** — Feedback motion planning for underactuated nonlinear systems that offers *formal* stabilization guarantees over a region of state space, not just tracking of a single open-loop trajectory.
**Method** — Direct computation of Lyapunov functions via convex (sums-of-squares) optimization is used to certify the region of attraction ("funnel") of each locally-valid LQR controller about a trajectory. A randomized tree of such trajectories is grown backward from the goal, and their certified funnels are combined into one nonlinear feedback policy until they probabilistically cover the reachable, bounded state space.
**Key results** — Proves the probabilistic-coverage property (any initial condition able to reach the goal stabilizes to it) and demonstrates the design on underactuated benchmark systems.

## Takeaways
- Certified regions of attraction ("funnels") turn a sparse set of stabilized trajectories into a policy with a formal reachability/stability guarantee.
- SOS/convex optimization makes computing Lyapunov certificates for smooth nonlinear systems tractable — the enabling technical lever.
- Guarantee is *probabilistic* coverage of a *bounded* state space, and the SOS machinery assumes polynomial (or polynomial-approximable) dynamics.

## Relevance to your work
A foundational treatment of certified funnels around trajectories that motion-planning-with-guarantees layers build on; directly relevant to hierarchical planner/tracker schemes such as [[@hierarchies2025motion]] that need trajectory-level invariance certificates.

## Concepts
[[tracking-error-bound]]

## Source
- Cited by [[@hierarchies2025motion]]
- bibkeys: `tedrake2010lqr`
