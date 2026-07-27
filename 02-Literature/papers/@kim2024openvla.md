---
type: paper
citekey: kim2024openvla
tags: [foundation-model]
aliases: []
created: '2026-07-26'
modified: '2026-07-26'
authors:
- Kim, Moo Jin
- Pertsch, Karl
- Karamcheti, Siddharth
- Xiao, Ted
- Balakrishna, Ashwin
- Nair, Suraj
- Rafailov, Rafael
- Foster, Ethan
- Lam, Grace
- Sanketi, Pannag
- Vuong, Quan
- Kollar, Thomas
- Burchfiel, Benjamin
- Tedrake, Russ
- Sadigh, Dorsa
- Levine, Sergey
- Liang, Percy
- Finn, Chelsea
year: 2024
venue: CoRL
doi: 10.48550/arXiv.2406.09246
arxiv: '2406.09246'
url: https://arxiv.org/abs/2406.09246
zotero: null
status: to-read
mine: false
pdf: attachments/@kim2024openvla.pdf
---

# OpenVLA: An Open-Source Vision-Language-Action Model

> [!info] Kim, Moo Jin; Pertsch, Karl; Karamcheti, Siddharth; Xiao, Ted; et al. · 2024 · CoRL

> [!todo] metadata-only stub — flesh out from full text when read.

## Concepts
- [[vision-language-action]]
- [[foundation-model]]

*proposed links — concept notes to be created centrally.*

## Abstract (from arXiv)
Large policies pretrained on a combination of Internet-scale vision-language data and diverse robot demonstrations have the potential to change how we teach robots new skills: rather than training new behaviors from scratch, we can fine-tune such vision-language-action (VLA) models to obtain robust, generalizable policies for visuomotor control. Yet, widespread adoption of VLAs for robotics has been challenging as 1) existing VLAs are largely closed and inaccessible to the public, and 2) prior work fails to explore methods for efficiently fine-tuning VLAs for new tasks, a key component for adoption. Addressing these challenges, we introduce OpenVLA, a 7B-parameter open-source VLA trained on a diverse collection of 970k real-world robot demonstrations. OpenVLA builds on a Llama 2 language model combined with a visual encoder that fuses pretrained features from DINOv2 and SigLIP. As a product of the added data diversity and new model components, OpenVLA demonstrates strong results for generalist manipulation, outperforming closed models such as RT-2-X (55B) by 16.5% in absolute task success rate across 29 tasks and multiple robot embodiments, with 7x fewer parameters. We further show that we can effectively fine-tune OpenVLA for new settings, with especially strong generalization results in multi-task environments involving multiple objects and strong language grounding abilities, and outperform expressive from-scratch imitation learning methods such as Diffusion Policy by 20.4%. We also explore compute efficiency; as a separate contribution, we show that OpenVLA can be fine-tuned on consumer GPUs via modern low-rank adaptation methods and served efficiently via quantization without a hit to downstream success rate. Finally, we release model checkpoints, fine-tuning notebooks, and our PyTorch codebase with built-in support for training VLAs at scale on Open X-Embodiment datasets.

## Source
- https://arxiv.org/abs/2406.09246
- DOI: https://doi.org/10.48550/arXiv.2406.09246
