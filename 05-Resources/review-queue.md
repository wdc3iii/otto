---
type: resource
tags: []
aliases: [Review Queue, Brush-up List]
created: 2026-07-06
modified: 2026-07-06
---

# Review Queue

Ranked list of topics to **brush up on**, maintained by the `quiz-me` skill — ordered
**weakest first** (lowest confidence, then stalest). This is how I stay current: quiz, score,
re-rank, review the top.

**Confidence** (demonstrated in the last quiz): 🔴 shaky · 🟡 partial · 🟢 solid.
**Last quizzed** is an ISO date. **Gaps** = the specific things to review next.

> [!note] `quiz-me` upserts a row per topic after each session, re-ranks weakest-first, and
> retires consistently-🟢 items to the bottom. Only topics we've actually discussed appear here.

| Topic | Confidence | Last quizzed | Gaps to review |
|---|---|---|---|
| _(empty — run `quiz-me <topic>` to populate)_ | | | |

## Retired (consistently solid)
_(topics I've shown solid command of across sessions — kept for history)_
