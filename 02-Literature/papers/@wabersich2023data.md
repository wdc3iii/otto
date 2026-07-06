---
type: paper
citekey: wabersich2023data
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Wabersich, Kim P
- Taylor, Andrew J
- Choi, Jason J
- Sreenath, Koushil
- Tomlin, Claire J
- Ames, Aaron D
- Zeilinger, Melanie N
year: 2023
venue: IEEE Control Systems Magazine
doi: 10.1109/MCS.2023.3291885
arxiv: null
url: https://doi.org/10.1109/MCS.2023.3291885
zotero: null
summary: ai-draft
pdf: missing
status: to-read
mine: false
bibkeys:
- wabersich2023data
---

# Data-driven safety filters: Hamilton-jacobi reachability, control barrier functions, and predictive methods for uncertain systems

> [!info] Wabersich, Kim P; Taylor, Andrew J; Choi, Jason J; Sreenath, Koushil; Tomlin, Claire J; Ames, Aaron D · 2023 · IEEE Control Systems Magazine
> [!info]- otto authors: [[aaron-ames]]

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — A tutorial-style survey framing safety filters — modules that minimally modify a nominal controller to keep an uncertain system inside a safe set — across three lineages: Hamilton-Jacobi reachability, control barrier functions, and predictive (MPC-based) methods.
**Problem** — Modern control tasks (power grids, human-robot collaboration, medical devices) demand hard safety guarantees, yet classical stability-around-setpoints methods struggle with unstructured tasks and conflicting safety specs; missing safety certificates block deployment outside the lab.
**Method** — Presents the safety filter as a unifying abstraction: safety requirements encoded as static state constraints must hold under all physical limits of the system. Surveys HJ reachability, CBFs, and predictive safety filters, then layers on data-driven enhancements to handle model uncertainty.
**Key results** — A comparative framework relating the three approaches and their data-driven extensions; a reference for choosing and combining safety-filter designs under uncertainty (survey, no single benchmark).

## Takeaways
- Positions safety filters as controller-agnostic wrappers: any nominal/learned policy can be filtered to remain provably safe.
- Unifies HJ reachability, CBFs, and predictive methods — useful map of which certificate suits which uncertainty structure.
- Data-driven variants are the through-line: how to certify safety when the model is imperfect or learned.

## Relevance to your work
A standard reference for anyone using [[@cohen2025safety]]-style safety filters over learned or nominal policies; it situates CBF-QP filters alongside reachability and robust-MPC alternatives, which matters when arguing why a given certificate is the right one for an uncertain legged system.

## Concepts
[[control-barrier-function]] · [[tube-mpc]]

## Source
- Cited by [[@compton2025dynamic]], [[@compton2025learning]]
- bibkeys: `wabersich2023data`
