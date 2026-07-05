---
type: paper
citekey: chen2021fastrack
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Mo Chen
- Sylvia L. Herbert
- Haimin Hu
- Ye Pu
- Jaime Fernandez Fisac
- Somil Bansal
- Soojean Han
- Claire J. Tomlin
year: 2021
venue: IEEE Transactions on Automatic Control
doi: 10.1109/TAC.2021.3059838
arxiv: null
url: null
zotero: null
status: to-read
mine: false
bibkeys:
- Chen2021
- TomlinTAC21
- chen2021fastrack
---

# FaSTrack:A Modular Framework for Real-Time Motion Planning and Guaranteed Safe Tracking

> [!info] Mo Chen; Sylvia L. Herbert; Haimin Hu; Ye Pu; Jaime Fernandez Fisac; Somil Bansal · 2021 · IEEE Transactions on Automatic Control

<!-- SUMMARY-PENDING: ingest-paper will fill a structured summary here -->

## Abstract (from bib)
Real-time, guaranteed safe trajectory planning is vital for navigation in unknown environments. However, real-time navigation algorithms typically sacrifice robustness for computation speed. Alternatively, provably safe trajectory planning tends to be too computationally intensive for real-time replanning. We propose FaSTrack, Fast and Safe Tracking, a framework that achieves both real-time replanning and guaranteed safety. In this framework, real-time computation is achieved by allowing any trajectory planner to use a simplified planning model of the system. The plan is tracked by the system, represented by a more realistic, higher dimensional tracking model. We precompute the tracking error bound (TEB) due to mismatch between the two models and due to external disturbances. We also obtai

## Concepts
<!-- [[03-Concepts]] links added when read -->

## Source
- Cited by [[@cohen2025safety]], [[@compton2025dynamic]], [[@compton2025learning]]
- bibkeys: `Chen2021`, `TomlinTAC21`, `chen2021fastrack`
- DOI: https://doi.org/10.1109/TAC.2021.3059838
