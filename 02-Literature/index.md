---
type: index
tags: []
aliases: []
created: 2026-07-05
modified: 2026-07-05
---

# 02 · Literature

**One reading note per source** in `papers/`, filename = `@citekey` (Better BibTeX key),
e.g. `@ames2019cbf.md`. Source-anchored: what *this* paper claims / does. Cite back to
the source of truth (Zotero) via the `zotero:` property and `[@citekey]`.

- `[@ames2019cbf]` renders as a citation; `[[@ames2019cbf]]` is an internal link. Same key.
- Each reading note **links out to the [[03-Concepts/index|Concepts]] it touches**; each
  concept links back to the papers that ground it.
- Frontmatter (see the paper template): `citekey, authors, year, venue, doi, url, zotero, status`.

Created/updated by the `ingest-paper` skill. Distilled, source-independent understanding
goes in [[03-Concepts/index|Concepts]], not here.
