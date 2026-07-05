---
type: paper
citekey: pinto2023leveraging
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Pinto, Alessandro
- Corso, Anthony
- Schmerling, Edward
year: 2023
venue: International Conference on Assured Autonomy (ICAA)
doi: 10.1109/ICAA58325.2023.00013
arxiv: '2304.13517'
url: https://arxiv.org/abs/2304.13517
summary: ai-draft
pdf: attachments/@pinto2023leveraging.pdf
zotero: null
status: to-read
mine: false
bibkeys:
- pinto_icca_2023
---

# Leveraging Compositional Methods for Modeling and Verification of an Autonomous Taxi System

> [!info] Pinto, Alessandro; Corso, Anthony; Schmerling, Edward · 2023 · International Conference on Assured Autonomy (ICAA)

## Summary
> [!note] AI-drafted from the abstract — a base to refine.
**TL;DR** — A case study applying compositional formal modeling and verification to an autonomous aircraft taxi system, used to surface concrete gaps in the current formal-methods toolchain for autonomy.

**Problem** — Formal methods see limited adoption in the design of autonomous (including learning-enabled) systems; it is unclear what capabilities are missing to make compositional verification practical at system scale.

**Method** — The authors model and verify an autonomous aircraft taxi system with a compositional formal method, report insights from the modeling process, and from that experience enumerate the research gaps that block wider adoption.

**Key results** — Identifies six needs: (1) semantics for composing viewpoints in different specification languages plus tools for heterogeneous declarative models; (2) reusable libraries of formal models for autonomous systems; (3) methods to lift automated-reasoning results up to the specification level; (4) probabilistic contract frameworks for imperfect implementations; (5) standard high-level functional architectures for autonomy; (6) a theory of higher-order contracts.

## Takeaways
- A grounded case study, not a new theory — its value is the concrete gap list for compositional verification of autonomy.
- Explicitly calls for probabilistic and higher-order contract frameworks, signaling where contract theory needs to grow for learning-enabled systems.
- Heterogeneous specification languages and the lack of standard functional architectures are named as practical blockers.

## Relevance to your work
Motivates contract-based design of layered autonomy stacks by cataloging what compositional verification still lacks — particularly probabilistic and higher-order contracts relevant to a control-theoretic contract framework ([[@contract2025theory]]).

## Concepts
<!-- [[03-Concepts]] links added when read -->

## Source
- Cited by [[@contract2025theory]]
- bibkeys: `pinto_icca_2023`
