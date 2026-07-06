---
name: website-check
description: Audit the personal website (Jekyll repo at ../website) against the user's first-author publications and flag anything missing or stale. Use when the user asks to check/update the website, whether a paper is on the site, or as part of the weekly review. Reports gaps and offers to draft the missing paper pages; NEVER commits or pushes the website without explicit approval (pushing to gh-pages deploys live).
---

# website-check

Keep the personal website in sync with the user's first-author publications
([[publication-record]] is the source of truth; the site lives at `../website`, Jekyll on
the `gh-pages` branch).

## Procedure
1. **Diff.** Run `.claude/scripts/website-audit` and report its output verbatim. It lists
   each first-author paper (`authorship: first|co-first` in its note frontmatter) as ON SITE
   or MISSING, matching by arXiv id then title.
2. **Freshness.** Skim for staleness the script can't catch: a preprint that's now published
   (venue changed), a new first-author paper not yet in [[publication-record]], broken links
   on existing pages.
3. **Report** a short checklist. For a MISSING paper the user wants added, draft the page
   (below) for review — do **not** deploy.
4. **Draft a paper page** (mirrors the existing posts):
   - `_posts/YYYY-MM-DD-Name.markdown` — frontmatter: `layout: post`, `title`, `author: Will
     Compton`, `tags: Research <Topic>`, `subtitle:` (venue), `category: paper`,
     `thumbnail-img`, `header-img`, `permalink: /papers/<slug>/`, `description`. Body: motivate
     → method → results, arXiv link, and a YouTube embed (verify the video id via the oEmbed
     endpoint first).
   - `_carousel/<slug>.md` — `title`, `img`, `link_url` (homepage teaser).
   - `img/<slug>/` — pull figures from the paper PDF (`pdfimages -all` + `convert`); a cropped
     teaser photo makes a good `hero`/`header-img`.
   - Ground every claim in the abstract/figures — this is a draft for the user to refine.
5. **Deploy only on approval.** Committing is fine to stage; **`git push` deploys live** — do
   it only when the user explicitly says so.

## Rules
- The website is outward-facing: propose, show, and confirm before pushing.
- If `../website` isn't found, ask for the repo path and pass it to the script.
