---
type: paper
citekey: brohan2023rt2
tags: [rl]
aliases: []
created: '2026-07-26'
modified: '2026-07-26'
authors:
- Brohan, Anthony
- Brown, Noah
- Carbajal, Justice
- Chebotar, Yevgen
- Chen, Xi
- Choromanski, Krzysztof
- Ding, Tianli
- Driess, Danny
- Dubey, Avinava
- Finn, Chelsea
- Florence, Pete
- Fu, Chuyuan
- Gonzalez Arenas, Montse
- Gopalakrishnan, Keerthana
- Han, Kehang
- Hausman, Karol
- Herzog, Alexander
- Hsu, Jasmine
- Ichter, Brian
- Irpan, Alex
- Joshi, Nikhil
- Julian, Ryan
- Kalashnikov, Dmitry
- Kuang, Yuheng
- Leal, Isabel
- Lee, Lisa
- Lee, Tsang-Wei Edward
- Levine, Sergey
- Lu, Yao
- Michalewski, Henryk
- Mordatch, Igor
- Pertsch, Karl
- Rao, Kanishka
- Reymann, Krista
- Ryoo, Michael
- Salazar, Grecia
- Sanketi, Pannag
- Sermanet, Pierre
- Singh, Jaspiar
- Singh, Anikait
- Soricut, Radu
- Tran, Huong
- Vanhoucke, Vincent
- Vuong, Quan
- Wahid, Ayzaan
- Welker, Stefan
- Wohlhart, Paul
- Wu, Jialin
- Xia, Fei
- Xiao, Ted
- Xu, Peng
- Xu, Sichun
- Yu, Tianhe
- Zitkovich, Brianna
year: 2023
venue: CoRL
doi: 10.48550/arXiv.2307.15818
arxiv: '2307.15818'
url: https://arxiv.org/abs/2307.15818
zotero: null
status: to-read
mine: false
summary: ai-draft
pdf: attachments/@brohan2023rt2.pdf
---

# RT-2: Vision-Language-Action Models Transfer Web Knowledge to Robotic Control

> [!info] Brohan, Brown, Carbajal et al. · 2023 · CoRL

## Summary
> [!note] AI-drafted from the arXiv abstract — a base to refine.

**TL;DR** — Co-fine-tune a state-of-the-art vision-language model on both web-scale vision-language tasks and robot trajectory data by encoding actions as text tokens, yielding a single end-to-end vision-language-action (VLA) model that inherits internet knowledge and shows emergent semantic reasoning in robotic control.

**Problem** — How can the internet-scale knowledge baked into vision-language models be brought *directly* into end-to-end robotic control, so a single model both maps observations to actions and enjoys the generalization benefits of large-scale web pretraining?

**Method** — Co-fine-tune a pretrained VLM on a mixture of robot trajectories and internet vision-language tasks (e.g. visual question answering). The key trick for a "simple, general recipe": express robot actions as text tokens and fold them into the training set exactly like natural-language tokens, so language responses and actions share one output format. This class of models is dubbed VLA; RT-2 is the instantiated example. Chain-of-thought reasoning is additionally incorporated to enable multi-stage semantic reasoning.

**Key results** — Across an extensive evaluation (6k evaluation trials, per abstract), the approach produces performant policies and a range of emergent capabilities from internet-scale training: significantly improved generalization to novel objects; the ability to interpret commands absent from the robot training data (e.g. place an object onto a particular number or icon); and rudimentary reasoning (pick the smallest/largest object, or the one closest to another). With chain-of-thought, RT-2 performs multi-stage semantic reasoning — e.g. selecting a rock as an improvised hammer, or an energy drink for someone tired.

**Limitations / open questions** — The abstract does not enumerate limitations. (inferred) RT-2 acquires *semantic* generalization but does not add new low-level motor skills beyond what the robot demonstration data covers; (inferred) running large VLM backbones as real-time policies carries substantial compute/latency cost; (inferred) evaluation is on manipulation platforms, leaving transfer to other embodiments (e.g. legged/whole-body control) open.

## Concepts
[[vision-language-action]]
[[foundation-model]]
[[transformer]]

> proposed links — concept notes to be created centrally.

## Relevance to your work
RT-2 is the canonical VLA result showing internet-scale VLM knowledge transferring into robot action — the semantic/task layer that would sit *above* a low-level locomotion + control stack like the one on the Unitree G1. It frames how a high-level "what to do and why" policy could interface with certified low-level controllers, rather than replacing them.

## Abstract (from arXiv)
We study how vision-language models trained on Internet-scale data can be incorporated directly into end-to-end robotic control to boost generalization and enable emergent semantic reasoning. Our goal is to enable a single end-to-end trained model to both learn to map robot observations to actions and enjoy the benefits of large-scale pretraining on language and vision-language data from the web. To this end, we propose to co-fine-tune state-of-the-art vision-language models on both robotic trajectory data and Internet-scale vision-language tasks, such as visual question answering. In contrast to other approaches, we propose a simple, general recipe to achieve this goal: in order to fit both natural language responses and robotic actions into the same format, we express the actions as text tokens and incorporate them directly into the training set of the model in the same way as natural language tokens. We refer to such category of models as vision-language-action models (VLA) and instantiate an example of such a model, which we call RT-2. Our extensive evaluation (6k evaluation trials) shows that our approach leads to performant robotic policies and enables RT-2 to obtain a range of emergent capabilities from Internet-scale training. This includes significantly improved generalization to novel objects, the ability to interpret commands not present in the robot training data (such as placing an object onto a particular number or icon), and the ability to perform rudimentary reasoning in response to user commands (such as picking up the smallest or largest object, or the one closest to another object). We further show that incorporating chain of thought reasoning allows RT-2 to perform multi-stage semantic reasoning, for example figuring out which object to pick up for use as an improvised hammer (a rock), or which type of drink is best suited for someone who is tired (an energy drink).

## Source
- arXiv: https://arxiv.org/abs/2307.15818
- PDF: https://arxiv.org/pdf/2307.15818
- DOI: https://doi.org/10.48550/arXiv.2307.15818
