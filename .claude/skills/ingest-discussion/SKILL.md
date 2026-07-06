---
name: ingest-discussion
description: Ingest a discussion — a conversation with claude.ai or another person, or a set of notes — usually provided as a markdown file in 00-Inbox/. Extracts the concepts, claims, decisions, and especially the USER's viewpoints/opinions, and files them into otto: drafts/updates concept notes, adds the user's viewpoints (authoritative) to the relevant notes, links papers/people/concepts, and stubs what's missing. Use when the user drops a discussion/transcript/notes and says "ingest this discussion/conversation/notes".
---

# ingest-discussion

Turn a dialogue or a pile of notes into structured, linked otto knowledge — carefully
separating the user's own views (authoritative) from external claims (attributed).

## Procedure
1. **Read the source.** Take the markdown file (from `00-Inbox/` or a given path). Identify the
   format — a claude.ai / LLM chat, a conversation with a named person, or raw notes — and track
   **who said what**.
2. **Extract.**
   - **Concepts/ideas** discussed → map to existing [[03-Concepts/index|concepts]] vs. new ones.
   - **Claims/facts** worth keeping, and whether each is grounded (cite a paper) or an assertion.
   - **The user's viewpoints / opinions / decisions** — the highest-value payload.
   - **People/papers** mentioned → existing `[[@citekey]]` / [[People/index|People]] or to add.
   - Open questions and disagreements.
3. **Preserve provenance.** A discussion isn't a citable source. Keep the raw file as the anchor —
   leave it in `00-Inbox/` or park it at `05-Resources/discussions/YYYY-MM-DD-<topic>.md`
   (`type: resource`) — and attribute extracted claims to it ("from a 2026-07-06 discussion with
   X", "claude.ai chat"). **Never launder an opinion or an LLM claim into a cited fact.**
4. **File it.**
   - Update / stub the relevant **concept notes** (agent-drafted parts marked `ai-draft`).
   - Add the **user's viewpoints** to the right notes as `> [!quote] My take (YYYY-MM-DD): …`
     (authoritative, not `ai-draft`) — the same convention `quiz-me` uses.
   - Add links (concepts ↔ papers ↔ people); enqueue new papers/people for `ingest-paper` / `add-person`.
5. **Report & verify.** List what was created / updated / linked, and what you propose but didn't
   apply; run `link-check` + `frontmatter-validate`. Apply substantive note rewrites only on approval.

## Rules
- **Attribute honestly:** user opinion ≠ external claim ≠ established (cited) fact — mark each as what it is.
- Prefer updating existing concepts over spawning near-duplicates; link generously but tightly.
- The raw transcript is the provenance anchor — keep or park it, don't discard it silently.
