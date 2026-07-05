---
type: index
tags: []
aliases: []
created: 2026-07-05
modified: 2026-07-05
---

# Journal

- `daily/` — daily notes, filename `YYYY-MM-DD.md`. Created by the `daily` skill; carries
  over unfinished tasks and surfaces active [[01-Projects/index|project]] priorities.
- `sessions/` — **the agent's memory layer.** One log per Claude Code session, filename
  `YYYY-MM-DD-HHMM.md` from the session template. At session start the agent reads the
  last 1–2 logs; at session end it writes a new one (Context / Changes / Open threads /
  Decisions).

This is where the agent "remembers" across sessions — kept in-vault and in git (no lock-in),
rather than in an external store.
