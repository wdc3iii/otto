---
type: paper
citekey: sarma2022internal
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Sarma, Anish A.
- Li, Jing Shuang Lisa
- Stenberg, Josefin
- Card, Gwyneth
- Heckscher, Elizabeth S.
- Kasthuri, Narayanan
- Sejnowski, Terrence
- Doyle, John C.
year: 2022
venue: 2022 American Control Conference (ACC)
doi: 10.23919/ACC53348.2022.9867859
arxiv: '2110.05029'
url: https://arxiv.org/abs/2110.05029
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@sarma2022internal.pdf
bibkeys:
- sarma_internal_2022
---

# Internal feedback in biological control: Architectures and examples

> [!info] Sarma, Anish A.; Li, Jing Shuang Lisa; Stenberg, Josefin; Card, Gwyneth; Heckscher, Elizabeth S.; Kasthuri, Narayanan · 2022 · 2022 American Control Conference (ACC)

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — Argues that biological control systems are pervaded by complex *internal feedback pathways* (IFPs) and that severe hardware speed-accuracy tradeoffs, mitigated by diversity-enabled sweet spots (DESS), explain why they exist.
**Problem** — Beyond ordinary plant-controller feedback, biology shows intricate feedback *within* the controller (neural systems, bacterial signaling, immune system) that standard control accounts leave cryptic.
**Method** — Motivating examples from neuroscience and biology are used to introduce the concepts needed to explain IFPs, centered on hardware speed-accuracy tradeoffs. Minimal toy models illustrate how diversity-enabled sweet spots (DESS) mitigate those tradeoffs; standard modern/robust control and System Level Synthesis (SLS) are invoked for more realistic models.
**Key results** — A conceptual framework (this is a survey/position paper with toy models) tying IFPs to DESS and layered architectures; detailed theory deferred to companion papers.

## Takeaways
- Internal feedback pathways are a first-class architectural feature, not noise — driven by physical hardware tradeoffs.
- Diversity-enabled sweet spots (DESS): combining heterogeneous components beats any single one under speed-accuracy limits.
- Bridges biological control intuition to SLS / robust layered-control theory; mostly conceptual, with formal results elsewhere.

## Relevance to your work
Provides the layered-architecture / DESS lens on why robust control systems distribute feedback across heterogeneous, multi-rate layers; cited by [[@hierarchies2025motion]] as biological motivation for hierarchical locomotion control.

## Concepts
[[hierarchical-control]]

## Source
- Cited by [[@hierarchies2025motion]]
- bibkeys: `sarma_internal_2022`
