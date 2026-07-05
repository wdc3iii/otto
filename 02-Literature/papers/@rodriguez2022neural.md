---
type: paper
citekey: rodriguez2022neural
tags: []
aliases: []
created: '2026-07-05'
modified: '2026-07-05'
authors:
- Rodriguez, Ivan Dario Jimenez
- Csomay-Shanklin, Noel
- Yue, Yisong
- Ames, Aaron D.
year: 2022
venue: Proceedings of The 4th Annual L4DC
doi: null
arxiv: 2204.08120
url: https://arxiv.org/abs/2204.08120
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@rodriguez2022neural.pdf
bibkeys:
- pmlr-v168-rodriguez22a
- rodriguez_neural_2022
---

# Neural Gaits: Learning Bipedal Locomotion via Control Barrier Functions and Zero Dynamics Policies

> [!info] Rodriguez, Ivan Dario Jimenez; Csomay-Shanklin, Noel; Yue, Yisong; Ames, Aaron D. · 2022 · Proceedings of The 4th Annual L4DC

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.
**TL;DR** — Learn a bipedal walking gait by enforcing set invariance with control barrier functions defined only on the low-dimensional zero dynamics, refining the model episodically from robot data while retaining full-order guarantees.
**Problem** — Learning dynamic walking directly on the full-order underactuated system is high-dimensional and model errors erode any stability/safety guarantees.
**Method** — Walking is framed as a set-invariance problem enforced via CBFs on the reduced-order zero dynamics (the underactuated component). Two learning modules cooperate: one learns a policy satisfying the CBF condition, the other learns a residual dynamics model correcting the nominal model's imperfections; learning only over the zero dynamics slashes dimensionality while the CBF still certifies the full-order system.
**Key results** — Demonstrated experimentally on an underactuated bipedal robot, achieving agile, dynamic locomotion even with partially unknown dynamics.

## Takeaways
- Restricting learning to the zero dynamics is the key move: dimensionality drops, yet CBF-based invariance lifts guarantees back to the full-order robot.
- A learned residual model closes the sim-to-real / nominal-model gap and is refined episodically from experimental data.
- Marries formal safety (CBFs) with learning — guarantees are only as good as the CBF certificate on the reduced model plus the residual's accuracy.

## Relevance to your work
Directly in your lineage of reduced-order + certificate-based locomotion: learning a policy on zero dynamics under CBF invariance is a close cousin of the constructive/robust reduced-order designs in [[@compton2024constructive]].

## Abstract (from bib)
This work presents Neural Gaits, a method for learning dynamic walking gaits through the enforcement of set invariance that can be refined episodically using experimental data from the robot. We first frame walking as a set invariance problem enforceable via control barrier functions (CBFs) defined on the reduced-order dynamics quantifying the underactuated component of the robot: the zero dynamics. Our approach contains two learning modules: one for learning a policy that satisfies the CBF condition, and another for learning a residual dynamics model to refine imperfections of the nominal model. Importantly, learning only over the zero dynamics significantly reduces the dimensionality of the learning problem while using CBFs allows us to still make guarantees for the full-order system. Fi

## Concepts
[[control-barrier-function]] · [[reduced-order-model]]

## Source
- Cited by [[@compton2024constructive]], [[@csomayshanklin2024robust]]
- bibkeys: `pmlr-v168-rodriguez22a`, `rodriguez_neural_2022`
