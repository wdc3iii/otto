---
name: vault-lint
description: Health-check the vault — run link-check and frontmatter-validate, then find orphaned notes, tag drift (tags outside the taxonomy), notes missing from their folder index, and empty stubs. Use when the user asks to lint, audit, or health-check the vault, or before a commit or sync. Reports and proposes fixes; never auto-deletes or auto-renames.
---

# vault-lint

Structural hygiene. Report first, fix only with approval, and honor the guardrails
(never delete a note, never OS-rename a linked note).

## Procedure
1. **Broken links.** Run `.claude/scripts/link-check`; report its output verbatim.
2. **Frontmatter.** Run `.claude/scripts/frontmatter-validate`; report errors/warnings.
3. **Orphans.** List concept/literature notes with zero inbound links (exclude
   `index`/`home`/`moc` notes and Templates). Candidates to link from a MOC or a concept.
4. **Tag drift.** Surface any tags in use that aren't in `.claude/taxonomy.md`
   (frontmatter-validate flags these) — propose either adding the tag to the taxonomy or
   retagging the note.
5. **Index coverage.** Note any file whose folder `index.md` doesn't mention it, where it
   plausibly should (MOCs, key concepts).
6. **Stubs.** Flag notes with little body (frontmatter only / a title and nothing else).
7. **PDFs.** Run `.claude/scripts/pdf-check`; flag paper notes missing `attachments/@citekey.pdf` — the user will obtain them.
8. **Report** a prioritized list. Apply fixes only on approval; for any move/rename use the
   `obsidian-cli` skill (or rewrite inbound links + re-run `link-check`).

## Rules
- This skill is diagnostic. It proposes; it does not unilaterally restructure the vault.
