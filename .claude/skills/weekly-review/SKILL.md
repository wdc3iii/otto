---
name: weekly-review
description: Read across the vault and surface NON-OBVIOUS connections and CONTRADICTIONS in the user's thinking — the payoff synthesis workflow. Use when the user asks for a weekly review, a synthesis pass, "what connects", "what's inconsistent in my notes", or wants cross-note insight. Also runs the presence checks (website/youtube/linkedin) and surfaces the top brush-up items from the `quiz-me` review queue. Produces a report; does not create or edit permanent notes without approval.
---

# weekly-review

The highest-value workflow: read *across* areas and tell the user something they didn't
already see. This is synthesis, not summarization, and not generation.

## Procedure
1. **Scope.** Gather recent activity:
   - `Journal/daily/` for the last ~7 days and the last 1–2 `Journal/sessions/` logs.
   - Notes changed recently (`git -C <vault> log --since=7.days --name-only`, or mtime).
   - The concept/literature/MOC clusters those touch.
2. **Read for signal** — specifically hunt for:
   - **Missing links:** a concept discussed across multiple papers that aren't linked to it.
   - **Contradictions:** notes that disagree, or a note contradicted by a recently added source. *This is the most valuable output — surface it explicitly, with both sides cited.*
   - **Orphans & stubs:** concept notes with no inbound links; stubs never fleshed out.
   - **Open questions:** notes tagged `open-question`/`to-revisit` that recent work bears on.
   - **Emerging themes:** clusters big enough to deserve a new MOC in `04-Maps/`.
3. **Report** (do not silently edit the vault). For each finding: what it is, the specific
   notes involved (as `[[links]]`), and a concrete proposed action (e.g. "add
   `[[control-barrier-functions]]` ↔ `[[@ames2019cbf]]`", "these two notes disagree on X").
4. **Outward presence (quick pass).** Check that public-facing surfaces reflect recent work:
   - `website-check` — first-author papers missing from the personal website (`../website`).
   - `youtube-check` — new videos in tracked playlists (e.g. the lecture series) to ingest.
   - `linkedin-check` — profile updates worth making (low-key checklist).
   Report these alongside the synthesis findings.
5. **Knowledge currency.** Surface the top of `05-Resources/review-queue.md` (weakest-first —
   the 🔴/🟡 topics, plus any 🟢 gone stale since it was last quizzed). Offer to `quiz-me` on the
   top few so they don't drift; notes added this week with no quiz history are candidates too.
6. **Act only on approval.** If the user greenlights edits, make them, then run
   `link-check` and report results.

## Rules
- Prefer questions and contradictions over tidy summaries — friction is the point.
- Cite the user's own notes; don't import outside claims unless asked (that's `lit-review`).
