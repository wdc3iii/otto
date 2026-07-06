---
type: paper
citekey: jr2024contract
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Manuel Mazo Jr.
- Will Compton
- Max H. Cohen
- Aaron D. Ames
year: 2024
venue: null
doi: null
arxiv: '2409.14902'
url: https://arxiv.org/abs/2409.14902
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@jr2024contract.pdf
bibkeys:
- mazo2024contracttheorylayeredcontrol
---

# A Contract Theory for Layered Control Architectures

> [!info] Manuel Mazo Jr.; Will Compton; Max H. Cohen; Aaron D. Ames · 2024 · —
> [!info]- otto authors: [[aaron-ames]]

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — Formalizes layered (hierarchical) control architectures as relations between layers and introduces contracts — interfaces between layers — so that each layer can be designed in isolation and their composition provably meets a system-wide specification.

**Problem** — Autonomous systems combine discrete and continuous models running at different timescales, forming a hybrid system over heterogeneous signals; there was no compositional theory guaranteeing that independently designed layers combine into a correct whole.

**Method** — The paper defines a layered control architecture through a theory of relations between layers, then formulates contracts that specify each inter-layer interface. Composing the per-layer contracts yields a contract that captures the desired system-wide specification, enabling a compositional (isolate-and-compose) design and analysis workflow.

**Key results** — A formal, compositional framework: it shows that satisfying local contracts at each layer certifies the global specification, decoupling the design of layers in an otherwise entangled hybrid system.

## Takeaways
- Contracts turn layer interfaces into first-class objects: satisfy local contracts and correct composition is guaranteed, so layers decouple.
- Frames a multi-rate hybrid stack (discrete + continuous, different timescales) as a single analyzable object.
- Assumes the desired system spec can be decomposed into composable per-layer contracts — the framework's power depends on finding those interfaces.

## Relevance to your work
This is the compositional-guarantee backbone for layered locomotion architectures; it is closely tied to your own contract-theory line of work [[@contract2025theory]] and grounds the hierarchical planning of [[@hierarchies2025motion]].

## Concepts
[[hierarchical-control]]

## Source
- Cited by [[@hierarchies2025motion]]
- bibkeys: `mazo2024contracttheorylayeredcontrol`
- arXiv: https://arxiv.org/abs/2409.14902
- URL: https://arxiv.org/abs/2409.14902
