---
name: concept
description: Draft or refine an atomic evergreen concept note in 03-Concepts/ — a single idea, grounded in the papers that support it, written as an editable base the user will refine. Use when the user wants to distill/crystallize an idea, "make this a concept note", draft concepts, or refine understanding of a topic.
---

# concept

Crystallize one idea into a durable, reusable note. **Draft a solid, correct base** the user
will edit into their own words — grounded in the linked papers and domain knowledge, marked
`ai-draft`, with inference flagged and nothing fabricated.

## Procedure
1. **Atomic check.** One idea per note. If the material holds two ideas, split and link them.
2. **Draft it.** Write a tight, correct explanation from the grounding papers + domain
   knowledge: what it is, the intuition, how it connects. If a claim isn't supported, mark it
   as inference or leave an open question — never fabricate specifics or citations.
3. **Fill `Templates/concept.md`:** Definition · Intuition/why-it-matters · Grounding · Open
   questions. Grounding cites real `[@citekey]` notes; link `[[related-concepts]]` only where
   A genuinely changes how you see B. Add an `ai-draft` callout so the user knows to review.
4. **Filename** kebab-case; frontmatter per schema; ≤3 tags from `.claude/taxonomy.md`.
5. **Back-link.** Add this concept to the **Concepts/Grounding** section of the papers that
   support it, so the paper↔concept links go both ways.
6. Update `03-Concepts/index.md` if warranted; run `link-check`; report.

## Rules
- One idea per note. Draft as an editable base (`ai-draft`); ground every claim; no invented
  citations or links; no fabricated specifics — the user refines into their own voice.
