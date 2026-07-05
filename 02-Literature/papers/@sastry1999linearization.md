---
type: paper
citekey: sastry1999linearization
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Sastry, Shankar
year: 1999
venue: 'Nonlinear Systems: Analysis, Stability, and Control'
doi: 10.1007/978-1-4757-3108-8_9
arxiv: null
url: https://doi.org/10.1007/978-1-4757-3108-8_9
zotero: null
summary: ai-draft
pdf: missing
status: to-read
mine: false
bibkeys:
- sastry_linearization_1999
---

# Linearization by State Feedback

> [!info] Sastry, Shankar · 1999 · Nonlinear Systems: Analysis, Stability, and Control

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — Foundational textbook chapter developing the differential-geometric theory of feedback linearization for nonlinear control systems.
**Problem** — When and how a nonlinear system can be transformed, via state feedback and a change of coordinates, into an equivalent (fully or partially) linear system — extending linear geometric control theory to the nonlinear case.
**Method** — Surveys the geometric machinery (Lie derivatives and brackets, relative degree, involutive distributions, the Frobenius theorem) behind full-state and input-output linearization, tracing the lineage from Brockett, Hermann, Krener, Fliess, Sussmann and the seminal Isidori–Krener–Gori-Giorgi–Monaco results. Develops both exact static-feedback linearization conditions and the input-output normal form.
**Key results** — Establishes the conditions for exact linearization and characterizes the input-output normal form together with the residual internal (zero) dynamics left after input-output linearization. (Textbook chapter; no experiments.)

## Takeaways
- Input-output linearization always leaves internal dynamics; their stability (the minimum-phase property) is not guaranteed and must be checked separately.
- Relative degree and involutivity are the central structural invariants determining linearizability.
- Canonical reference for the geometric-control constructs (relative degree, zero dynamics, feedback linearization) that downstream tracking-control work assumes.

## Abstract (from bib)
In this chapter we begin with a study of the modern geometric theory of nonlinear control. The theory began with early attempts to extend results from linear control theory to the nonlinear case, such as results on controllability and observability. This work was pioneered by Brockett, Hermann, Krener, Fliess, Sussmann and others in the 1970s. Later, in the 1980s in a seminal paper by Isidori, Krener, Gori-Giorgi, and Monaco [150] it was shown that not only could the results on controllability and observability be extended but that large amounts of the linear geometric control theory, as represented, say, in Wonham [331] had a nonlinear counterpart. This paper, in turn, spurred a tremendous growth of results in nonlinear control in the 1980s. On a parallel course with this one, was a progr

## Relevance to your work
Feedback / input-output linearization and its zero-dynamics analysis are the classical backbone for the output-tracking controllers and reduced-order constructions in [[@compton2024constructive]].

## Concepts


## Source
- Cited by [[@compton2024constructive]], [[@csomayshanklin2024robust]], [[@hierarchies2025motion]]
- bibkeys: `sastry_linearization_1999`
- DOI: https://doi.org/10.1007/978-1-4757-3108-8_9
