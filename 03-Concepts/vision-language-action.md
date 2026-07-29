---
type: concept
tags: [foundation-model, to-revisit]
aliases: [Vision-Language-Action model, VLA, robot foundation model]
created: 2026-07-26
modified: 2026-07-29
---

# Vision-Language-Action model

> [!note] AI-drafted base — refine into your own words, then drop `to-revisit`.

## Definition
A robot policy built by **fine-tuning an internet-pretrained vision-language model to output actions**, so that web-scale semantic knowledge (objects, instructions, affordances) transfers into control ([[@brohan2023rt2]], [[@kim2024openvla]]). Observations and actions are tokenized and produced by the same [[transformer]] backbone.

## Intuition / why it matters
VLAs are the **semantic / task layer** — generalization to novel objects and language instructions — that would sit *above* a low-level locomotion + control stack like mine on the Unitree G1. The literature is overwhelmingly **manipulation**; the humanoid-locomotion analogue is largely open.

## Grounding
- [[@brohan2022rt1]] (RT-1) → [[@brohan2023rt2]] (RT-2, web knowledge → action).
- Data/scale: [[@oneill2024open]] (Open X-Embodiment / RT-X, cross-embodiment).
- Open + efficient: [[@kim2024openvla]] (OpenVLA, 7B). Flow-based: [[@black2024pi0]] (π0).
- **Navigation instance (in otto):** [[@cheng2024navila|NaVILA]] — a legged-robot VLA that emits *language* waypoints to a locomotion RL policy; plus the topological-nav foundation models [[@shah2023vint|ViNT]] / [[@sridhar2024nomad|NoMaD]]. Ties this concept into [[navigation-autonomy]].
- **Whole-body instance (in otto):** [[@luo2025sonic]] — GR00T N1.5 drives a G1's *entire kinematic chain* by predicting 78-dim actions (64-dim quantized motion token + 14-dim hands), including using **feet as manipulators** (stepping on a trash-can pedal while balancing on the other leg). 75% average over five real tasks. Also [[@xie2026grail]] for the data side.

## Related
- [[foundation-model]] · [[transformer]]

## Open questions
- **Control-rate mismatch**: VLAs run at ~Hz; locomotion runs at ~kHz. What is the right interface between a VLA task layer and a fast low-level controller?
- What is the locomotion/whole-body analogue of a manipulation VLA?

> [!tip] Both open questions above now have a concrete candidate answer (added 2026-07-29 with [[@luo2025sonic]], ai-draft)
> SONIC's answer to the **interface** question is a **quantized latent motion token** as the VLA's action
> space, plus an explicit multi-rate stack: VLA/kinematic planning at ~10 Hz → token → tracking policy at
> 50 Hz → command streaming at 500 Hz. The token is what decouples the rates: the VLA specifies *what
> motion*, the tracker owns *how to stay up*.
>
> They ablate the obvious alternative — having the VLA predict explicit SMPL poses — and report jerky
> motion and poor directional control. So the claim is that the *quantization*, not just the hierarchy,
> is doing work: a discrete token is a smaller, better-conditioned thing for a slow semantic model to emit.
>
> Worth interrogating against your own line: this is exactly the layered-interface question, but the
> interface is a **learned latent** rather than an $SE(2)$ command or a ROM state with a
> [[tracking-error-bound]]. Nothing certifies that an arbitrary token is trackable — compare how
> [[@terrain2026consistent]] chooses a planner-compatible interface *by construction*.
