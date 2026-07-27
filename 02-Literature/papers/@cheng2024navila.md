---
type: paper
citekey: cheng2024navila
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Cheng, An-Chieh
- Ji, Yandong
- Yang, Zhaojing
- Gongye, Zaitian
- Zou, Xueyan
- Kautz, Jan
- B\iy\ik, Erdem
- Yin, Hongxu
- Liu, Sifei
- Wang, Xiaolong
year: 2024
venue: arXiv preprint arXiv:2412.04453
doi: null
arxiv: '2412.04453'
url: https://arxiv.org/abs/2412.04453
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@cheng2024navila.pdf
bibkeys:
- cheng2024navila
---

# Navila: Legged robot vision-language-action model for navigation

> [!info] Cheng, An-Chieh; Ji, Yandong; Yang, Zhaojing; Gongye, Zaitian; Zou, Xueyan; Kautz, Jan · 2024 · arXiv preprint arXiv:2412.04453

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — NaVILA is a two-level framework for vision-and-language navigation on legged robots: a vision-language-action model emits mid-level, language-form waypoints (e.g. "move forward 75cm") that a visual locomotion RL policy then executes.
**Problem** — Translating free-form human language instructions all the way down to low-level leg joint actions is hard; legged robots must also navigate cluttered, challenging scenes that wheeled VLN setups avoid.
**Method** — Rather than predicting joint actions directly from the VLA, NaVILA has the VLA generate mid-level actions with spatial information expressed in language, which serve as commands to a downstream visual locomotion RL policy. This decoupling separates high-level instruction grounding from low-level dynamic control.
**Key results** — Reports substantial improvement over prior approaches on existing VLN benchmarks, plus new IsaacLab benchmarks with realistic scenes and low-level control, and real-world robot experiments (relative gains stated qualitatively here).

## Takeaways
- A language-as-interface between the VLA and the locomotion policy is the key design choice — mid-level spatial commands decouple semantics from control.
- The two-level split lets a general VLA reuse a robust visual locomotion RL policy instead of learning joint-level control end-to-end.
- Validated in sim (IsaacLab) and on real hardware, not just static VLN benchmarks.

## Relevance to your work
A concrete instance of hierarchical high-level (language/planning) over low-level (RL locomotion) control for legged robots — relevant to layered navigation autonomy as in [[@terrain2026consistent]].

## Concepts
[[hierarchical-control]] · [[vision-language-action]] · [[foundation-model]]

## Source
- Cited by [[@terrain2026consistent]]
- bibkeys: `cheng2024navila`
- arXiv: https://arxiv.org/abs/2412.04453
