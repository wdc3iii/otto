# otto — Project Plan

> Synthesis of `second_brain_plan.txt` (your prep brief) + current (2025–2026) web
> research on AI-native Obsidian vaults, Claude Code workflows, and PKM methodology.
> This plan *refines* your brief; it does not replace it. The phase structure and
> **Checkpoint Protocol** from your brief still govern execution — nothing gets
> built until you say `go`.

---

## 0. TL;DR — what the research changed

Your brief is well-grounded; most of it survives contact with current practice. The
research produced **one strategic confirmation** and a **short list of concrete
additions**, nothing that requires a rethink.

**Strategic confirmation.** Across every genuine first-person account, the durable,
trusted use of an AI + vault system is **retrieval / synthesis** ("agent as
librarian"), not net-new generation. Generation is only safe when (i) strictly
grounded in the vault, (ii) human-gated, (iii) treated as first-draft scaffolding.
This is exactly your priority ordering (reading & synthesis > generation), and it's
the single most robust finding — corroborated by independent authors *and* learning
science (the "generation effect": writing is where the learning happens, so the
agent should sharpen *your* words on concept notes, not replace them).

**Concrete additions (the delta vs. your brief):**
1. **Elevate MOCs out of `02-Literature/`** to a top-level maps layer so a topic hub
   can link *concepts + papers together* (the payoff for lit reviews). *(Decision D1.)*
2. **Adopt `kepano/obsidian-skills`** — confirmed real, MIT, authored by Obsidian's
   CEO; teaches correct wikilink / frontmatter / `.base` / `.canvas` syntax. *(D2.)*
3. **Route note moves through the official Obsidian CLI, never `mv`.** OS-level renames
   silently break every inbound `[[wikilink]]` — the #1 reported hazard. Add a
   link-integrity check script and a hard guardrail.
4. **Prefer Bases over Dataview** for indexes. Bases is now a *core* feature and its
   `.base` files are plain YAML — trivially agent-authorable, fast at scale.
5. **Frontmatter schema hardening** — Obsidian 1.9 requires plural list forms
   (`tags`/`aliases`), ISO-8601 dates, and type-stable keys. Enforce via a Templater
   template + a validation step.
6. **Provenance discipline in CLAUDE.md** — every claim links back to its source;
   never invent citations or connections; mark inferred vs. sourced. Critical for a
   researcher doing lit reviews.
7. **Controlled tag vocabulary** file — agents over-tag and invent tags otherwise.
8. **Optional session-log automation** via hooks (`SessionStart` reads recent logs,
   `Stop` writes one) instead of relying on the agent to remember. *(D3.)*

> ⚠️ Cutoff note: several sources post-date my Jan-2026 training (Karpathy's LLM-Wiki
> gist, Obsidian 1.10 / Bases API, the official Obsidian CLI GA). The research agents
> verified them live, but we'll sanity-check exact install commands / CLI verb names
> at execution time rather than trusting them blind.

---

## 1. Validation — what in your brief is already right

- **Literature ↔ Concepts separation** (`02-Literature/papers` = per-source reading
  notes; `03-Concepts` = atomic evergreen notes). This is simultaneously Ahrens'
  literature-vs-permanent split *and* Matuschak's source-vs-concept-oriented rule —
  the most-endorsed single decision in all of PKM. Keep it exactly.
- **filename = citekey** for papers — near-universal academic practice.
- **Numbered top-level folders** (`00-Inbox` … ) — recognized Zettelkasten-in-Obsidian
  convention.
- **Concepts are a flat namespace** (not nested under source/topic) — Matuschak's core
  rule; correct.
- **Capture-before-organize + Inbox** — directly counters the "collector's fallacy,"
  the #1 abandonment cause.
- **Session logs as the memory layer** and **per-folder `index.md`** — both match the
  converged agent-vault pattern (read an index first; append to a log).
- **Guardrails** (never delete, never OS-rename heavy-linked notes, keep plans out of
  the vault, ≤3 tags, everything in git) — all independently corroborated as the exact
  failure modes people hit. Keep them; we're *adding* to them, not changing them.

---

## 2. Recommended vault skeleton (final)

Change vs. your brief: MOCs promoted to a top-level `04-Maps/`; downstream folders
renumbered. Everything else is your structure.

```
otto/
├── second_brain_plan.txt     # your prep brief (delete after setup)
├── PROJECT-PLAN.md           # this file (delete after setup)
├── CLAUDE.md                 # agent standing instructions (Phase 2)
├── Home.md                   # LYT "Home" note — human entry point + agent routing
├── .claude/                  # skills (incl. obsidian-skills), settings, hooks, scripts
│   ├── skills/               #   obsidian-markdown, obsidian-bases, json-canvas, (+cli)
│   ├── scripts/              #   link-check, frontmatter-validate
│   └── taxonomy.md           #   controlled tag vocabulary (single source of truth)
├── 00-Inbox/                 # raw capture, unsorted. Agent-safe zone.
├── 01-Projects/              # active outputs with a deadline / definition of done
│   ├── papers/               #   one folder per paper
│   ├── talks/                #   one folder per talk
│   └── teaching/             #   per-course materials
├── 02-Literature/
│   └── papers/               # one note per source, filename = @citekey
├── 03-Concepts/              # atomic evergreen notes (one idea each), densely linked
├── 04-Maps/                  # MOCs / lit-review hubs — link BOTH concepts + papers
├── 05-Resources/             # reference material, code snippets, configs, cheatsheets
├── 06-Archive/               # completed / inactive
├── Meetings/                 # dated meeting notes
├── Journal/
│   ├── daily/                # daily notes
│   └── sessions/             # agent session logs (the memory layer)
└── Templates/                # note templates (paper, concept, moc, daily, meeting, session)
```

**Why `04-Maps/` instead of `02-Literature/topics/`:** a subfield hub (e.g.
"Whole-Body Control for Bipeds") is only useful for a lit review if it curates the
*concepts you've distilled* alongside the *papers that ground them*. Nesting it under
Literature couples it to sources and under-delivers on synthesis. A top-level maps
layer lets a MOC span both trees and become the outline of an actual review/talk.

**On a `raw/` layer:** the Karpathy pattern keeps immutable sources in a `raw/` the
agent never edits. For you, the "raw" source of truth for papers is **Zotero** (PDFs +
annotations), not the vault — so we don't need a `raw/` tree. Reading notes cite
`[@citekey]` back to Zotero; `05-Resources/` holds anything else. Provenance is
enforced as a *rule*, not a folder.

---

## 3. Frontmatter schema + naming conventions

Decide the key set **once**, populate via Templater, keep types stable — this is what
makes Bases queries and agent edits reliable.

**Common to every note**
```yaml
type:      concept        # concept | paper | moc | project | daily | meeting | resource
tags:      [rl, locomotion]   # LIST, lowercase, ≤3, from .claude/taxonomy.md only
aliases:   []             # LIST
created:   2026-07-05     # ISO-8601 date (type: date, not text)
modified:  2026-07-05
```

**Paper notes (`02-Literature/papers/@citekey.md`)** add:
```yaml
citekey:   ames2019cbf
authors:   [Ames, Coogan, Egerstedt]   # LIST
year:      2019           # number
venue:     ECC
doi:       10.23919/ECC.2019.8796030
url:       https://...
zotero:    zotero://select/items/...
status:    read           # to-read | reading | read
```

**Naming**
- Papers: `@citekey.md` (Better BibTeX key, e.g. `@ames2019cbf.md`). The `@` prefix
  unlocks a neat duality — `[@ames2019cbf]` renders as a citation, `[[@ames2019cbf]]`
  is an internal link. Same key, one vs. two brackets.
- Concepts / MOCs: kebab-case (`control-barrier-functions.md`, `bipedal-locomotion.md`).

**Rules the schema depends on**
- `tags`/`aliases` **must be YAML lists** (Obsidian 1.9 removed the singular forms).
- Frontmatter tags auto-lowercase and strip `#`. Prefer frontmatter tags over inline
  `#tags` for machine-parseability.
- One key = one type globally. Never reuse a key with mixed types.

---

## 4. Tooling stack

**Obsidian plugins**
- **Templater** (not core Templates) — needed to populate structured frontmatter and
  run logic on note creation. Essential.
- **Zotero Integration** (mgmeyers) + **Better BibTeX** (Zotero side) — the literature
  pipeline: stable citekeys, metadata + annotation import. Essential for `ingest-paper`.
- **Bases** (core, enable it) — indexes/dashboards. Prefer over Dataview.
- **Dataview** — optional, only if you later need task rollups or inline-field queries.
- **obsidian-git** — sync (Phase 5); **disable its auto-commit** so it doesn't race
  agent commits.

**Agent-side (`.claude/`)**
- **`kepano/obsidian-skills`** — copy `obsidian-markdown`, `obsidian-bases`,
  `json-canvas` (+ `obsidian-cli` if we adopt the CLI) into `.claude/skills/`. MIT.
- **Official Obsidian CLI** — for *link-safe* moves/renames (`obsidian move …` goes
  through Obsidian's API and rewrites links). The agent uses this instead of `mv`.
- **Scripts** — `link-check` (grep the vault for `[[…]]` that resolve to no file) and
  `frontmatter-validate` (valid YAML, required keys, `tags` is a list). Run at session
  end / before commit. *Never trust the agent's self-report — verify with the script.*

**Bases usage examples** (both are your stated needs, both map cleanly):
- *All papers by year* → a `.base` filtered to `type == "paper"`, `groupBy: year`.
- *Concepts linking to a topic* → embed a `this`-relative Base in the MOC
  (`file.hasLink(this.file)`), so the hub auto-lists everything pointing at it.

---

## 5. Guardrails (your 6 + additions)

Your originals stand. Additions from the research:

7. **Never `mv`/rename a note at the OS level.** Use the Obsidian CLI, or (if editing
   files directly) rewrite every inbound `[[link]]` and then run `link-check` to prove
   nothing broke. OS renames silently orphan links; this is the most-reported failure.
8. **Provenance.** Every claim in a note links to its source (`[@citekey]` / `[[…]]`).
   Never invent a citation or a connection not supported by the material. Mark inferred
   content as inferred. No speculation dressed as fact.
9. **Controlled tags.** Only tags in `.claude/taxonomy.md` may be applied; reuse before
   inventing; propose additions rather than adding silently.
10. **Verify, don't self-report.** After any batch of edits, run the link/frontmatter
    scripts and report the *actual* result ("47 links, 0 broken"), not "done."
11. **Section/block-level edits over full-file overwrites**; commit before bulk ops so
    `git diff` is the undo button.

---

## 6. Phased execution plan

Same phases and **Checkpoint Protocol** as your brief — work in order, stop at each
`CHECKPOINT N`, wait for `go N`. Deltas from your brief are marked **[+]**.

### Phase 0 — Prerequisites & decisions
- Confirm Obsidian will open this folder as a **local** vault; confirm `claude` runs
  from here. *(Both true: `obsidian` + `claude` are installed; folder is local.)*
- **Not a git repo yet** → propose `git init` + `.gitignore` (ignore
  `.obsidian/workspace*.json`, `.obsidian/cache`, `.trash/`, `.DS_Store`; **keep**
  `.obsidian/` config and `.claude/`).
- Resolve **decisions D1–D3** (§7).
- **[+]** Confirm whether to install `obsidian-skills` and the Obsidian CLI now.
- **CHECKPOINT 0** — summarize environment + decisions, wait.

### Phase 1 — Vault skeleton
- Create the §2 tree; add a short `index.md` to each top-level folder + a root `Home.md`.
- **CHECKPOINT 1** — show tree + index stubs.

### Phase 2 — CLAUDE.md
- Fill in the skeleton from your brief §4, **[+]** folding in: provenance rules, the
  no-OS-rename rule, controlled-tag rule, verify-don't-self-report, the frontmatter
  schema (§3), and a context-loading order (read `Home.md`/indexes first, not the whole
  vault). Write it as day-one onboarding, not documentation.
- **CHECKPOINT 2** — draft, iterate to approval (expect 1–2 rewrites).

### Phase 3 — Memory + core skills
- `Templates/session.md` (Context / Changes / Open threads / Decisions).
- Wire CLAUDE.md: read last 1–2 session logs at start, write one at end.
- **[+]** *Optional (D3):* add hooks — `SessionStart` injects recent logs + active
  projects; `Stop`/`PreCompact` writes the session log automatically. Otherwise keep it
  manual (in-vault logs, no lock-in — the default).
- Scaffold skills: **`daily`**, **`capture`**, **`weekly-review`** (the payoff:
  surface non-obvious connections *and contradictions* across areas).
- **[+]** Add **`vault-lint`** — orphans, broken links, tag drift, contradictions.
- **CHECKPOINT 3** — show template + skills.

### Phase 4 — Research workflows
- **`ingest-paper`** — PDF/arXiv → `@citekey.md` reading note (frontmatter + structured
  summary: problem/method/result/limitations) + proposed `03-Concepts/` links (stub
  missing concepts). Grounded strictly in the source; no invented claims.
- **`lit-review`** — grep the vault first, *then* web, then synthesize into / update a
  `04-Maps/` MOC. **Flag contradictions** between your notes and new sources — that's
  the point.
- **`concept`** — turn a messy note into an atomic evergreen note *in your own words*,
  linked to grounding papers. (Agent refines your phrasing; it doesn't ghost-write.)
- **`talk-prep`** — pull relevant paper + concept notes into
  `01-Projects/talks/<name>/`, build an outline from *your* material.
- **CHECKPOINT 4** — show skills.

### Phase 5 — Remote access (optional, last)
- Vault in a **private git repo**; `talos` holds the working clone.
- **Tailscale** — *not currently installed*; install on `talos` + phone.
- Phone → Termius (SSH) → `talos` → `claude` in the vault. Pull before, push after.
- **Topology matters more than transport:** prefer **one working tree** (phone SSHes
  into `talos`, which also runs Obsidian) to avoid multi-clone merge divergence.
  Disable obsidian-git auto-commit; don't run agent bulk edits on files open in the app.
- If already committed `.obsidian/workspace.json` churns: `git rm --cached` it.
- **CHECKPOINT 5** — outline commands before executing.

---

## 7. Decisions to confirm before Phase 0

Reply with your picks (or just `go` to accept all recommendations and start Phase 0).

- **D1 — MOC placement.** *Recommended:* top-level **`04-Maps/`** (MOCs span concepts +
  papers). Alternative: keep them under `02-Literature/topics/` as in your brief.
- **D2 — obsidian-skills scope.** *Recommended:* install the **3 format skills**
  (`obsidian-markdown`, `obsidian-bases`, `json-canvas`) + **`obsidian-cli`** (needed
  for link-safe moves). Alternatives: format-skills only / skip entirely.
- **D3 — session-memory automation.** *Recommended to start:* **manual** in-vault
  session logs (simplest, no lock-in), add **hooks** later once the flow is proven.
  Alternative: wire hooks now.
- **D4 — paper filename.** *Recommended:* `@citekey.md` (unlocks the citation/link
  duality). Your brief used `citekey.md` without the `@`. Minor; pick one.

---

## 8. Sources (strongest primaries)

- Karpathy, *LLM Wiki* gist — https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f
- kepano, *obsidian-skills* — https://github.com/kepano/obsidian-skills
- Andy Matuschak, *Evergreen notes* (esp. "…should be concept-oriented") — https://notes.andymatuschak.org/Evergreen_notes
- Bob Doto, *permanent vs evergreen notes* — https://writing.bobdoto.computer/misconceptions-about-the-relationship-between-permanent-and-evergreen-notes/
- Alexandra Phelan, *Zotero & Obsidian academic workflow* — https://medium.com/@alexandraphelan/an-updated-academic-workflow-zotero-obsidian-cffef080addd
- Obsidian Bases syntax / changelog — https://help.obsidian.md/bases/syntax · https://obsidian.md/changelog/2025-08-18-desktop-v1.9.10/
- JSON Canvas spec — https://jsoncanvas.org/
- Obsidian Git tips (gitignore / conflicts) — https://publish.obsidian.md/git-doc/Tips-and-Tricks
- eferro, *maintaining an Obsidian wiki with Claude Code* — https://eferro.substack.com/p/how-i-use-claude-code-to-maintain
- Scott Bell, *6-month AI second-brain retrospective* — https://www.myyearindata.com/posts/obsidian-second-brain-ai-agents/
- Eva Keiffenheim, *why PKM systems fail* — https://evakeiffenheim.substack.com/p/the-fatal-flaw-in-most-personal-knowledge

*(Fuller source lists — including MCP-server options and memory-architecture repos we
deferred — are captured in the session research and can be surfaced on request.)*
