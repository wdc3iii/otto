---
name: talk-prep
description: Given a talk topic and deadline, pull the relevant paper and concept notes into 01-Projects/talks/<name>/ and build an outline grounded in the user's own vault material (not generic). Use when the user is preparing a talk, seminar, or lecture and wants to assemble it from otto.
---

# talk-prep

Build a talk from the user's own material, grounded in the vault.

## Procedure
1. **Set up the project.** Create `01-Projects/talks/<slug>/` with a project note
   (`type: project`, the deadline, the venue/audience).
2. **Gather material.** `grep` the vault for relevant `03-Concepts/`, `02-Literature/`, and
   `04-Maps/` notes. Assemble a linked reading list in the project note (`[[wikilinks]]`).
3. **Draft an outline from the user's notes** — each section cites the specific
   `[[concept]]` / `[[@paper]]` it draws on. **Flag gaps** where the vault lacks material
   (candidates for `lit-review` or `ingest-paper`) rather than filling them with generic content.
4. Keep any generated slides/prose as scaffolding the user will own and revise; never
   fabricate results or over-claim.
5. Run `link-check`; report the outline, the source map, and the gaps.

## Rules
- Grounded in the vault, not generic. Surface gaps honestly. Provenance on every claim.
