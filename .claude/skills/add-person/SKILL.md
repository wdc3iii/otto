---
name: add-person
description: Draft or update a person page (type: person) in People/ for a researcher or collaborator — a grounded bio, their contributions to the field, what's relevant to otto's focus areas (with agreements/contrasts to the user's own line), links to the papers they authored in otto, and their non-paper presence (site, talks, posts). Use when the user says "add a person", "make a page for <name>", or wants to profile/track a researcher.
---

# add-person

Create or refresh a `People/<kebab-name>.md` entity page (`type: person`). Research-grounded,
links-heavy, synthesis-forward. Draft it as an editable base (mark with an `ai-draft` callout);
never fabricate a bio.

## Procedure
1. **Gather sources.** Find the person's lab/personal homepage, Google Scholar, and a couple of
   authoritative pages; pull affiliation, role, training, and their major lines of work. Cite
   what you use; flag anything uncertain.
2. **Cross-reference otto.**
   - Papers they authored: `grep -rl "<Surname>" 02-Literature/papers/` then confirm via the
     `authors:` frontmatter → collect `@citekey`s + titles.
   - The [[03-Concepts/index|concepts]] / [[04-Maps/index|MOCs]] their work touches.
3. **Draft from `Templates/person.md`:**
   - Frontmatter: `type: person`, ≤3 taxonomy `tags` (their focus areas), `aliases`,
     `affiliation`, `role`, `homepage`, `scholar` (+ optional `orcid/github/twitter`).
   - Sections: **Bio** · **Contributions to the field** · **Relevance to otto** (the payoff —
     link concepts/MOCs and *surface where their approach agrees with or contrasts my own
     line*) · **In otto — authored works** (grouped `[[@citekey]]` links) · **Elsewhere**
     (non-paper: site, talks, interviews, posts, startups) · **Sources**.
4. **Wire it in.** Add the page to `People/index.md`; optionally backlink it from the person's
   most otto-relevant papers and from a related MOC.
5. **Verify.** Run `.claude/scripts/link-check` and `frontmatter-validate`; report results.

## Rules
- Ground the bio in real sources — never invent positions, awards, or affiliations; mark inference.
- **"Relevance to otto" is why the page exists** — connect to my concepts/papers and be specific
  about agreement/contrast, not a generic CV.
- Not a rolodex: add someone when their work genuinely intersects mine.
- Pairs with `quiz-me` (quiz yourself on a person you just added) and `ingest-discussion`.
