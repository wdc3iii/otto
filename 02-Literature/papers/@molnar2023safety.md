---
type: paper
citekey: molnar2023safety
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- T. G. Molnar
- A. D. Ames
year: 2023
venue: ACC
doi: 10.48550/arXiv.2303.03247
arxiv: 2303.03247
url: https://arxiv.org/abs/2303.03247
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@molnar2023safety.pdf
bibkeys:
- TamasACC23
---

# Safety-Critical Control with Bounded Inputs via Reduced Order Models

> [!info] T. G. Molnar; A. D. Ames · 2023 · ACC
> [!info]- otto authors: [[aaron-ames]]

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — A safety-critical control framework that uses a reduced-order model with a backup-set formulation to guarantee safety of the full-order system under bounded inputs and disturbances.
**Problem** — Enforcing safety on high-dimensional autonomous systems is hard because full-order models are complex and hard to identify, and actuation limits (bounded inputs) break naive CBF guarantees.
**Method** — The backup-set method is reformulated in terms of a reduced-order model, and conditions are derived under which safety of the reduced model provably implies safety of the full-order system despite input constraints. An input-to-state-safe variant of the backup-set method is then introduced to provide robustness to the mismatch between the reduced-order model and the true system.
**Key results** — Demonstrated in high-fidelity simulation, where a quadrupedal robot navigates around an obstacle via legged locomotion using a unicycle reduced-order model to enforce safety.

## Takeaways
- Reduced-order models make CBF safety tractable on complex robots, but the reduction gap must be handled explicitly — here via input-to-state safety.
- The backup-set method is what accommodates hard actuation limits, avoiding the unbounded control demands a plain CBF-QP can produce.
- The unicycle-model-for-a-quadruped case study is the template: plan/enforce safety on a simple model, certify transfer to the full legged system.

## Relevance to your work
Directly on the reduced-order-model-for-safety line that underpins layered locomotion safety; it is a natural companion to the layered safety framing in [[@cohen2025safety]] and to reduced-order planning models for legged robots.

## Concepts
[[reduced-order-model]] · [[control-barrier-function]]

## Source
- Cited by [[@cohen2025safety]]
- bibkeys: `TamasACC23`
