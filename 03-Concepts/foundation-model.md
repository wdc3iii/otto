---
type: concept
tags: [method, to-revisit]
aliases: [Foundation model, pretrained model]
created: 2026-07-26
modified: 2026-07-26
---

# Foundation model

> [!note] AI-drafted base — refine into your own words, then drop `to-revisit`.

## Definition
A **large model pretrained on broad data at scale** that is then adapted (fine-tuned or prompted) to many downstream tasks. In robotics this means repurposing pretrained VLMs or world models as the backbone for control, rather than training a policy from scratch per task.

## Intuition / why it matters
The bet is that **broad priors transfer**: pretraining on internet-scale (or cross-embodiment) data yields generalization that per-task training cannot. Open X-Embodiment is the data play; RT-2 / OpenVLA are the policy play; Genie is a *foundation world model*. The unresolved question for me is whether such priors help **low-level legged control** or only high-level task selection.

## Grounding
- Robot policies: [[@brohan2023rt2]] (RT-2), [[@kim2024openvla]] (OpenVLA).
- Data substrate: [[@oneill2024open]] (Open X-Embodiment / RT-X).
- Foundation world model: [[@bruce2024genie]] (Genie).

## Related
- [[vision-language-action]] · [[world-model]] · [[transformer]]

## Open questions
- What data makes an *embodied* foundation model? (Cross-embodiment transfer is the Open X-Embodiment thesis.)
- Do foundation priors help the kHz control loop, or is their value confined to the semantic layer?
