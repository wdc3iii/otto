---
type: concept
tags: [navigation, control, to-revisit]
aliases: [social navigation, socially-compliant navigation, semantic safety]
created: 2026-07-06
modified: 2026-07-06
---

# Social navigation

> [!note] Stub — expand when revisited.

## Definition
Navigation that is **socially compliant**, not merely collision-free: appropriate interpersonal spacing, non-aggressive skirting of people, and consistent passing conventions (e.g. pass-on-the-right). Closely tied to **semantic safety** — making the safety margin *class-dependent* (a human gets a wider berth than a chair of equal volume) rather than purely geometric.

## Why it matters
Geometric CBFs are "semantically blind." Encoding social/semantic structure requires either class-aware modulation of the safety function ([[@yang2026safesage|Safe-SAGE]]'s Laplace-modulated [[poisson-safety-function|PSF]], with tangential passing bias) or perceptual prioritization of dynamic agents ([[@zhang2026focusnav]] tracking humans outside FOV). One of the two higher-order requirements of the [[capability-aware-navigation]] project ("sidewalk-vs-grass" semantics + human-spacing).

## Grounding
- [[@yang2026safesage]] — semantic/social modulation of the PSF (b_human vs b_object). · [[@zhang2026focusnav]] — dynamic-human handling in humanoid local nav.

## See also
[[poisson-safety-function]] · [[control-barrier-function]] · [[capability-aware-navigation]]
