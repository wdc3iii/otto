---
type: paper
citekey: peng2022ase
tags: [rl, imitation]
aliases: []
created: '2026-07-26'
modified: '2026-07-26'
authors:
- Peng, Xue Bin
- Guo, Yunrong
- Halper, Lina
- Levine, Sergey
- Fidler, Sanja
year: 2022
venue: SIGGRAPH
doi: 10.48550/arXiv.2205.01906
arxiv: '2205.01906'
url: https://arxiv.org/abs/2205.01906
zotero: null
status: to-read
mine: false
pdf: attachments/@peng2022ase.pdf
---

# ASE: Large-Scale Reusable Adversarial Skill Embeddings for Physically Simulated Characters

> [!info] Peng, Xue Bin; Guo, Yunrong; Halper, Lina; Levine, Sergey; Fidler, Sanja · 2022 · SIGGRAPH

> [!todo] metadata-only stub — flesh out from full text when read.

## Concepts
- [[motion-imitation]]
- [[massively-parallel-simulation]]

*proposed links — motion-imitation to be created centrally; massively-parallel-simulation already exists.*

## Abstract (from arXiv)
The incredible feats of athleticism demonstrated by humans are made possible in part by a vast repertoire of general-purpose motor skills, acquired through years of practice and experience. These skills not only enable humans to perform complex tasks, but also provide powerful priors for guiding their behaviors when learning new tasks. This is in stark contrast to what is common practice in physics-based character animation, where control policies are most typically trained from scratch for each task. In this work, we present a large-scale data-driven framework for learning versatile and reusable skill embeddings for physically simulated characters. Our approach combines techniques from adversarial imitation learning and unsupervised reinforcement learning to develop skill embeddings that produce life-like behaviors, while also providing an easy to control representation for use on new downstream tasks. Our models can be trained using large datasets of unstructured motion clips, without requiring any task-specific annotation or segmentation of the motion data. By leveraging a massively parallel GPU-based simulator, we are able to train skill embeddings using over a decade of simulated experiences, enabling our model to learn a rich and versatile repertoire of skills. We show that a single pre-trained model can be effectively applied to perform a diverse set of new tasks. Our system also allows users to specify tasks through simple reward functions, and the skill embedding then enables the character to automatically synthesize complex and naturalistic strategies in order to achieve the task objectives.

## Source
- https://arxiv.org/abs/2205.01906
- DOI: https://doi.org/10.48550/arXiv.2205.01906
