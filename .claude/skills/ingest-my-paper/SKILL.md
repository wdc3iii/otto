---
name: ingest-my-paper
description: Ingest one of the user's OWN papers AND guarantee coverage of everything it cites — create the literature note for the user's paper (mine: true), extract its full reference list, enqueue each cited work to 00-Inbox/, and run ingest-paper on each so cited works land in otto. Use when the user drops one of their own papers (ideally with its LaTeX .bib/.bbl) or asks to bootstrap otto from their prior publications.
---

# ingest-my-paper

Bootstrap coverage from the user's own bibliographies: whatever their papers cite is
guaranteed to enter the vault. Depth-1 only, dedup, idempotent.

## 1. Ingest the user's paper itself
Run **ingest-paper** on it. Set `mine: true`. This note is the hub for its citations.

## 2. Extract the reference list — accuracy-first, in this order
1. **BibTeX `.bib`** the paper used — *best*: exact, offline, carries keys + DOIs + arXiv ids.
   Ask the user for it / locate it next to the source.
2. **`.bbl`** (compiled bibliography from the LaTeX build).
3. **PDF References section** — `pdftotext` then parse entries. Fuzziest: verify the count
   looks right and watch for truncated/merged entries.

Report how many references were found and by which method.

## 3. Normalize & dedup
Normalize each ref to `{title, authors, year, doi?, arxiv?, bibkey?}`. **Prefer the
identifiers the entry already carries (DOI/arXiv)** over fuzzy title lookups — a
title-only OpenAlex/S2 search often returns the wrong paper. Dedup against the vault and
within the batch (by doi/arxiv/citekey); skip ones already ingested and report the skip list.

## 4. Enqueue (durably)
Write one small capture file per *new* reference into `00-Inbox/` as `ref-<citekey>.md`
with the normalized metadata + identifiers. This way nothing is lost if a later step fails.

## 5. Ingest each cited work
Run **ingest-paper** on each queued reference. **Depth-1 only — never recurse into
citations-of-citations.** Most become metadata/abstract stubs (`status: to-read`) — expected
and fine; they're now in the graph and searchable. Enrich best-effort via arXiv id or DOI
(arXiv API / OpenAlex with `mailto=`); leave unknown fields blank rather than guessing.

## 6. Wire the citation graph
In the user's paper note add a `## References (in otto)` section listing each cited work as
`[[@citekey]]`, so the graph is navigable from their paper outward.

## 7. Verify & report
Run `link-check` + `frontmatter-validate`. Report counts: references found / new / deduped /
stubs created / concept stubs. **For a large bootstrap, work in batches and checkpoint with
the user — do not silently create hundreds of notes.** Summarize a batch, confirm, continue.

## Rules & environment notes
- **Depth 1**, dedup, idempotent (safe to re-run).
- Bash has network: arXiv API works over https; OpenAlex is fine with `mailto=` but needs a
  DOI/arXiv id for reliable identity; **Semantic Scholar rate-limits unkeyed (429)** — avoid for bulk.
- Never fabricate metadata for a reference you can't resolve; keep the bib fields you have.
