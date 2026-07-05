---
name: lit-review
description: Given a topic, first grep the vault for what already exists, THEN search the web for current/seminal work, then synthesize into or update a Map of Content in 04-Maps/. Flags contradictions between the user's existing notes and new sources — that is the point. Use when the user asks for a literature review, a survey, "what do I have on X", or to build/update a topic MOC.
---

# lit-review

Vault-first, then web. The synthesis (and especially the contradictions) is the payoff —
not a list of links.

## Procedure
1. **Vault first.** `grep`/glob `02-Literature/`, `03-Concepts/`, `04-Maps/` for the topic
   and its synonyms. Inventory existing paper notes, concept notes, and any MOC. Ground the
   review in the user's own material before going outward.
2. **Then web.** Search for current + seminal work not yet in the vault (recent surveys, the
   canonical papers). Bring genuinely relevant new ones in via **ingest-paper** (at least as stubs).
3. **Synthesize into a MOC** in `04-Maps/` (from `Templates/moc.md`; create only if the
   cluster warrants it, else update the existing one). Group by sub-question / method /
   chronology; one line per link on why it matters; link **both** concepts and papers.
4. **Flag the interesting parts:** contradictions between the user's notes and new sources;
   gaps (concepts with no grounding, papers not linked to any concept); where the field
   disagrees. Call these out explicitly — don't smooth them over.
5. Add the MOC to `[[Home]]`; run `link-check`; report what was added/updated and the open threads.

## Rules
- Propose new permanent notes and stubs; get approval before large restructuring.
- Provenance on every added claim; distinguish "my prior note says" from "new source says".
