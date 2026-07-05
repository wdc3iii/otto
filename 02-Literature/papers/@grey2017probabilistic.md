---
type: paper
citekey: grey2017probabilistic
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Grey, Michael X.
- Ames, Aaron D.
- Liu, C. Karen
year: 2017
venue: arXiv
doi: 10.48550/arXiv.1702.00425
arxiv: '1702.00425'
url: https://arxiv.org/abs/1702.00425
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@grey2017probabilistic.pdf
bibkeys:
- grey_ames_liu_2017
---

# Probabilistic Completeness of Randomized Possibility Graphs Applied to Bipedal Walking in Semi-unstructured Environments

> [!info] Grey, Michael X.; Ames, Aaron D.; Liu, C. Karen · 2017 · arXiv

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — A theoretical analysis proving that the Randomized Possibility Graph — a whole-body motion planner that decomposes the feasibility manifold into high- and low-level layers — is probabilistically complete for quasi-static bipedal walking in semi-unstructured environments, and converges faster than a flat planner.
**Problem** — Whole-body bipedal motion planning is expensive because feasibility constraints carve a complicated manifold; a hierarchical decomposition can speed search, but its completeness guarantees were unproven.
**Method** — The Randomized Possibility Graph uses a high-level decomposition of the feasibility constraint manifold to rapidly propose candidate routes, which lower-level planners then check for feasibility. The paper analyzes this two-level scheme theoretically for quasi-static walking in semi-unstructured environments.
**Key results** — Proves probabilistic completeness for quasi-static bipedal walking and shows the high/low-level split yields a considerably higher convergence rate in the probability of finding a solution when one exists, illustrated on simulated scenarios.

## Takeaways
- Provides a completeness guarantee for a hierarchical (possibility-graph) bipedal planner — a formal justification for layered planning.
- The speedup comes from cheap high-level route proposals filtered by expensive low-level feasibility checks.
- Scope is quasi-static walking in semi-unstructured environments; not a dynamic-walking result.

## Relevance to your work
A formal completeness/convergence argument for hierarchical bipedal motion planning, directly relevant to the layered planning-and-control decompositions in [[@hierarchies2025motion]].

## Concepts
[[hierarchical-control]]

## Source
- Cited by [[@hierarchies2025motion]]
- bibkeys: `grey_ames_liu_2017`
- DOI: https://doi.org/10.48550/arXiv.1702.00425
