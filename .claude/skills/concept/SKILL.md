---
name: concept
description: Help turn a messy or fleeting note into an atomic evergreen concept note in 03-Concepts/ — a single idea, in the user's own words, linked to the papers that ground it. Use when the user wants to distill or crystallize an idea, "make this a concept note", or refine their understanding of a topic.
---

# concept

Crystallize one idea into a durable, reusable note. On concept notes you **refine the
user's words; you do not ghost-write** — the writing is where the learning happens.

## Procedure
1. **Atomic check.** Identify the single idea. If the material holds two ideas, split into
   two notes and link them.
2. **Draft in the user's voice.** Work from what the user wrote/said; sharpen phrasing and
   structure. If their understanding is unclear or has a gap, **ask** — don't invent an
   explanation to paper over it.
3. **Fill `Templates/concept.md`:** Definition · Intuition/why-it-matters · Grounding · Open
   questions. Grounding cites real `[@citekey]` notes and links `[[related-concepts]]` only
   where A genuinely changes how the user sees B.
4. **Filename** kebab-case; frontmatter per schema; ≤3 tags from `.claude/taxonomy.md`.
5. **Back-link.** Add this concept to the **Concepts/Grounding** section of the papers that
   support it, so the paper↔concept links go both ways.
6. Update `03-Concepts/index.md` if warranted; run `link-check`; report.

## Rules
- One idea per note. Own words. No ghost-writing. No invented citations or links.
