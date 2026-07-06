---
type: paper
citekey: contract2025theory
tags: [control, planning]
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Mazo Jr., Manuel
- Compton, William D.
- Cohen, Max H.
- Ames, Aaron D.
authorship: contributing
year: 2025
venue: TAC (submitted)
doi: null
arxiv: null
url: null
zotero: null
status: read
mine: true
summary: ai-draft
pdf: attachments/@contract2025theory.pdf
---

# A Contract Theory for Layered Control Architectures

> [!info] Manuel Mazo Jr.; William D. Compton; Max H. Cohen; Aaron D. Ames · 2025 · TAC (submitted) — **my paper**

> [!note] De-anonymized 2026-07-06 (authors filled from the submission source). Citekey left
> as `contract2025theory` to preserve inbound links.

## Abstract
ion, e.g. chitectures. 1, 1 (July 2026), 13 pages. https://doi.org/10.1145/nnnnnnn. compare ODEs with difference equations or FSMs. After establish- nnnnnnn ing some basic properties of these relations, we introduce a version of system composition that captures both interconnections of sys-

## Summary
> [!note] AI-drafted from the abstract/intro — a base to refine or replace with your own framing.

**TL;DR** — A **contract theory for layered control architectures**: formalizes layers as a class of hybrid systems and defines *contracts* — interfaces between layers — such that composing per-layer contracts yields a contract for the whole system spec.
**Problem** — Layered systems mix discrete/continuous models across timescales; existing contract tools handle same-abstraction ("horizontal") composition but not heterogeneous, vertical (cross-layer) composition.
**Method** — Define relations between layers and vertical contracts via heterogeneous refinements (semantic maps between modeling domains); prove that contract composition at each layer captures the system-wide specification.
**Key results** — Enables **compositional, per-layer analysis** of layered architectures with system-level guarantees.

## Takeaways
- Gives the *formal* backbone for "design each layer independently, keep end-to-end guarantees."
- Vertical (cross-abstraction) contracts are the key new object.

## Where it sits in my work
The abstract/theoretical counterpart to [[@hierarchies2025motion|Hierarchies in Motion]] — one formalizes what the other builds and validates on hardware.

## Concepts
- [[hierarchical-control]] · _to add:_ assume-guarantee-contracts, hybrid-systems

## References (in otto)
- [[@alkhatib2020controller]]
- [[@baier2008principles]]
- [[@belta2017formal]]
- [[@benveniste2018contracts]]
- [[@borrelli2017predictive]]
- [[@girard2007approximation]]
- [[@incer2022algebra]]
- [[@kamermans2020primer]]
- [[@khalil2002nonlinear]]
- [[@kim2017small]]
- [[@krstic1995nonlinear]]
- [[@mazojr2024contract]]
- [[@nuzzo2018hierarchical]]
- [[@pinto2023leveraging]]
- [[@rosolia2022unified]]
- [[@saoud2021assume]]
- [[@shali2023composition]]
- [[@sharf2021assume]]
- [[@sontag1989universal]]
- [[@tabuada2009verification]]
