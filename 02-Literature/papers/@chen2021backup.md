---
type: paper
citekey: chen2021backup
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Chen, Yuxiao
- Jankovic, Mrdjan
- Santillo, Mario
- Ames, Aaron D
year: 2021
venue: 2021 60th IEEE Conference on Decision and Control (CDC)
doi: 10.1109/CDC45484.2021.9683111
arxiv: null
url: https://doi.org/10.1109/CDC45484.2021.9683111
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: missing
bibkeys:
- chen2021backup
---

# Backup control barrier functions: Formulation and comparative study

> [!info] Chen, Yuxiao; Jankovic, Mrdjan; Santillo, Mario; Ames, Aaron D · 2021 · 2021 60th IEEE Conference on Decision and Control (CDC)

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — A tutorial and comparative study of the *backup CBF*, a formulation that guarantees QP feasibility via an implicitly defined control invariant set from a fixed backup policy.
**Problem** — Standard CBF-QPs can lose feasibility because the safe set is not control invariant; constructing a valid control invariant set is hard in general.
**Method** — The backup CBF defines the invariant set implicitly by forward-integrating the dynamics under a fixed backup policy online, avoiding explicit set computation. The paper works the underlying math step by step and proves the backup CBF has relative degree 1 under mild assumptions.
**Key results** — Comparison against Hamilton-Jacobi PDE and Sum-of-Squares benchmarks shows the backup approach recovers a control invariant set close to the maximal one under a good backup policy for many practical problems.

## Takeaways
- Trades explicit invariant-set synthesis for online forward integration of a backup policy — feasibility of the CBF-QP is guaranteed by construction.
- Relative-degree-1 result makes the barrier constraint directly enforceable in a QP.
- Quality of the recovered invariant set hinges entirely on the choice of backup policy.

## Relevance to your work
A foundational feasibility-guaranteeing CBF construction that safety-focused controllers build on; relevant when pairing learned or planned references with hard safety filters as in [[@cohen2025safety]].

## Concepts
[[control-barrier-function]]

## Source
- Cited by [[@compton2025learning]]
- bibkeys: `chen2021backup`
