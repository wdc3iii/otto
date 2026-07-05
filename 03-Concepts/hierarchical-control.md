---
type: concept
tags: [control, planning, to-revisit]
aliases: [hierarchical control, layered control, planning and tracking]
created: 2026-07-05
modified: 2026-07-05
---

# Hierarchical control

> [!note] AI-drafted base — refine into your own words, then drop `to-revisit`.

## Definition
Decomposing control into layers operating at different timescales / levels of abstraction — e.g. a planning layer on a [[reduced-order-model]] feeding references to a tracking layer on the full-order dynamics — coordinated so that guarantees compose across layers.

## Intuition / why it matters
Divide-and-conquer for control: each layer is designed against a simpler model, and the architecture (layer interfaces + [[tracking-error-bound|tracking bounds]]) preserves end-to-end guarantees. The failure mode is a lower layer violating its assumed interface, which breaks the higher layer's plan — motivating explicit cross-layer contracts.

## Grounding
- [[@hierarchies2025motion]] · [[@contract2025theory]] — your layered-architecture synthesis and its contract-theoretic formalization.
- [[@girard2009hierarchical]] · [[@kurtz2020robust]] · [[@csomayshanklin2022multi]] — approximate-simulation / multi-rate foundations.

## Related
- [[reduced-order-model]] · [[tracking-error-bound]]

## Open questions
- Formalizing vertical (cross-abstraction) composition with preserved guarantees — see [[@contract2025theory]].
