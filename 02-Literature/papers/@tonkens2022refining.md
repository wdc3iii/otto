---
type: paper
citekey: tonkens2022refining
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Tonkens, Sander
- Herbert, Sylvia
year: 2022
venue: 2022 IEEE/RSJ International Conference on Intelligent Robots and Systems (IROS)
doi: 10.1109/IROS47612.2022.9981814
arxiv: 2204.12507
url: https://arxiv.org/abs/2204.12507
summary: ai-draft
pdf: attachments/@tonkens2022refining.pdf
zotero: null
status: to-read
mine: false
bibkeys:
- tonkens2022refining
---

# Refining control barrier functions through Hamilton-Jacobi reachability

> [!info] Tonkens, Sander; Herbert, Sylvia · 2022 · 2022 IEEE/RSJ International Conference on Intelligent Robots and Systems (IROS)

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — refineCBF uses Hamilton-Jacobi reachability (dynamic programming) to iteratively repair an invalid or overly-conservative candidate CBF into a provably valid one under input constraints.

**Problem** — Synthesizing a valid CBF that is not overly conservative in the presence of input constraints is notoriously hard; expert-designed or backup CBFs are often invalid or too cautious.

**Method** — The framework refines a candidate (expert-synthesized or backup) CBF via DP-based reachability analysis. Each DP iteration is guaranteed to produce a CBF at least as safe as the previous one, and the sequence converges to a valid CBF, uniting formal verification with reachability.

**Key results** — Guarantees monotone safety improvement per iteration and convergence to a valid CBF, bridging HJ reachability value functions and CBF-based safety filtering.

## Takeaways
- Treats CBF synthesis as refinement, not design-from-scratch: start from any candidate and let reachability certify/repair it.
- Monotone-safety-per-iteration is the key property — you can stop early and still hold a valid (if conservative) barrier.
- Inherits the curse of dimensionality of grid-based HJ reachability, limiting it to low-dimensional systems.

## Relevance to your work
Connects reachability-based safety value functions with CBF safety filters, relevant to constructing valid barriers for constrained locomotion/navigation systems as explored in [[@compton2025learning]].

## Concepts
[[control-barrier-function]]

## Source
- Cited by [[@compton2025learning]]
- bibkeys: `tonkens2022refining`
