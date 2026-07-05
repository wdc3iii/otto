---
name: daily
description: Create or open today's daily note in Journal/daily/ from the template — carry over unfinished tasks from the most recent daily note and surface active project priorities from 01-Projects/. Use when the user asks to start their day, "daily note", "what's on today", or "carry over my tasks".
---

# daily

Set up today's daily note. Keep it light — this is a launchpad, not a report.

## Procedure
1. **Date.** Today is `YYYY-MM-DD` (ask the shell if unsure: `date +%F`).
2. **Open or create.** If `Journal/daily/<date>.md` exists, read it and stop (don't clobber).
   Otherwise create it from `Templates/daily.md`, substituting `{{date}}`/`{{time}}` with
   the real ISO date/time.
3. **Carry over tasks.** Find the most recent prior file in `Journal/daily/`. Copy its
   unchecked tasks (`- [ ]` lines under `## Tasks`) into today's `## Tasks`. Leave
   completed tasks behind.
4. **Surface active projects.** List folders/notes under `01-Projects/` that are active
   (not archived) under `## Active projects`, as `[[wikilinks]]`. If a project note has a
   `status`/next-step, show it in one line.
5. **Report** what you created/carried over. Don't invent tasks or content.

## Rules
- Never delete a past daily note. Only ever create today's or append to it.
- Tasks are the user's — carry them verbatim; don't reword or complete them.
