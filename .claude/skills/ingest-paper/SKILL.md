---
name: ingest-paper
description: Turn a source — a PDF dropped in 00-Inbox/, an arXiv link/id, a DOI, or a raw citation — into a literature reading note in 02-Literature/papers/ named @citekey, with bibliographic frontmatter, a structured summary (problem / method / result / limitations), and proposed links to 03-Concepts/. Degrades to a metadata+abstract stub when full text isn't available. Use when the user drops a paper or asks to ingest/summarize/file a specific paper.
---

# ingest-paper

Create one literature note per source. Grounded strictly in the source — never invent
authors, DOIs, or claims.

## 1. Identify the source & get metadata
- **PDF in inbox:** read it (Read tool handles PDFs; or `pdftotext` for bulk text). Pull title/authors/year/venue; find a DOI/arXiv id on the first page if present.
- **arXiv id/link:** `curl -sL "https://export.arxiv.org/api/query?id_list=<id>"` (https, follows redirect) → title, authors, published, summary/abstract.
- **DOI:** Crossref `curl -sL "https://api.crossref.org/works/<doi>"`, or OpenAlex `https://api.openalex.org/works/https://doi.org/<doi>?mailto=wcompton@caltech.edu`.
- **Raw citation:** use the fields given; enrich only if an identifier is present.

## 2. Citekey & filename
Use the entry's existing Better-BibTeX key if provided. Else generate
`<firstauthorlastname><year><firstsignificanttitleword>`, lowercase ASCII
(e.g. `schulman2017proximal`). Filename = `@<citekey>.md`.

## 3. Dedup (before writing)
`grep -rl` in `02-Literature/papers/` for the same `doi`/`arxiv`/`citekey`. If a note
exists, update it instead of duplicating; report the skip.

## 4. Write the note (from `Templates/paper.md`)
Fill frontmatter (`citekey, authors, year, venue, doi, arxiv, url, status`; `mine: true`
only if the user is an author). Then:
- **Full text available** → structured summary: TL;DR / Problem / Method / Key results /
  Limitations, in your own words. Delete the metadata-only callout.
- **Metadata-only** (harvested citation, paywalled) → paste the abstract if you have it,
  keep `status: to-read` and the `> [!todo] metadata-only stub` callout. Still useful.

## 5. Propose concept links
For each core concept the paper grounds/uses: `grep` `03-Concepts/`; link `[[concept]]`
if it exists, else create a minimal stub (title + one-line + `to-revisit` tag) and link it.
Add a `[@citekey]` back-reference under that concept's **Grounding**. Report stubs created.

## 5b. Save the PDF
Download the PDF where legally available → `attachments/@<citekey>.pdf`, and set the
`pdf:` frontmatter to that path.
- arXiv: `https://arxiv.org/pdf/<id>` (always). Open-access DOI / landing page: fetch if directly downloadable.
- Paywalled / not found → set `pdf: missing` and add the citekey to the flagged list (the
  user will obtain it). Never store a wrong or fabricated PDF.

## 6. Finish
Update `02-Literature/index.md` if warranted, run `.claude/scripts/link-check`, and report:
note created/updated, full-vs-stub, concepts linked/stubbed.

## Rules
- No fabricated metadata or claims; mark anything you couldn't verify.
- API politeness: add `mailto=` to OpenAlex; avoid unkeyed Semantic Scholar for bulk (429).
