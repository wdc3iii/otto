---
name: capture
description: Process raw material in 00-Inbox/ — break a dump, paste, link, or transcript into atomic notes, file them into Literature/Concepts/Projects/Resources, add schema frontmatter and wikilinks from the controlled taxonomy, and report. Use when the user says "capture", "process my inbox", or drops raw text to be filed. For PDFs or arXiv papers, use the ingest-paper skill instead.
---

# capture

Turn raw inbox material into well-formed, filed notes. Capture beats perfect filing —
but this step is where filing happens. Propose; the user disposes.

## Procedure
1. **Read** the item(s) in `00-Inbox/` (or the text the user pasted).
2. **Route** each idea to its home:
   - A source/paper (PDF, arXiv, DOI) → hand off to **ingest-paper**.
   - A distilled idea in the user's own thinking → **03-Concepts/** (atomic, kebab-case).
   - Notes *about* a specific source → **02-Literature/papers/** (`@citekey`).
   - Deadline-bound work → **01-Projects/**. Reference/snippet/config → **05-Resources/**.
   - Genuinely unsure → **ask**, don't guess.
3. **Atomize.** One idea per note. For concept notes, keep the user's own words; sharpen,
   don't ghost-write.
4. **Frontmatter** per the CLAUDE.md schema (`type`, `tags` ≤3 from `.claude/taxonomy.md`,
   `aliases`, `created`, `modified`). Propose a new tag in taxonomy.md rather than inventing one.
5. **Link.** Add `[[wikilinks]]` only to notes that actually exist (glob/grep first); if a
   target doesn't exist yet, use plain text or create a deliberate stub — never a ghost link.
6. **Update** the destination folder's `index.md` (and `Home.md` for a new MOC).
7. **Verify & report.** Run `.claude/scripts/link-check` and report the real result. List
   what was created, where, links added, and anything that didn't fit the taxonomy.

## Rules
- Don't delete the raw inbox item unless the user says so — report it as processed instead.
- Never fabricate a citation or a connection the material doesn't support.
