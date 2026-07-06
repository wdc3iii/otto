---
name: quiz-me
description: Quiz the user on a topic from otto (a concept, paper, person, or MOC) with Socratic questions to test and refresh their knowledge. Two-way transfer — (1) capture the user's answers, opinions, and viewpoints back INTO the relevant notes (their own words, authoritative, not ai-draft), and (2) judge familiarity and maintain a ranked brush-up list in 05-Resources/review-queue.md. Use when the user says "quiz me", "test me on X", or wants to review / stay current on a topic.
---

# quiz-me

Active recall + knowledge capture. Pick a topic, ask, listen — and let information flow **both
ways**: sharpen the user's recall, and enrich the vault with what they know and think.

## Procedure
1. **Pick the topic.**
   - If the user names one (concept / paper / person / MOC), use it.
   - Else propose from `05-Resources/review-queue.md` (weakest / stalest first), or from recently
     added notes.
   - Read the target note + its close links so every question is grounded in what's actually in otto.
2. **Quiz Socratically.** Ask **4–8 questions, one at a time** (wait for each answer):
   - Mix recall ("what is X / why does it matter"), application, and connections
     ("how does X relate to [[Y]]?"), plus **at least one opinion prompt**
     ("what's your take on…?", "where do you disagree with the literature?").
   - Adapt: deeper where strong, simpler where shaky. Don't reveal the answer before they try.
3. **Capture knowledge (both directions).** As they answer:
   - **Gaps/corrections:** if they're off or unsure, give the right answer briefly and cite the note.
   - **New knowledge & viewpoints:** fold what they add back into the relevant note(s). The
     user's own words are **authoritative — NOT `ai-draft`**. Use a dated callout:
     `> [!quote] My take (YYYY-MM-DD): …` for opinions/viewpoints, or add facts to the body.
     **Propose the edits and apply on approval** — never silently rewrite a note.
4. **Score & update the review queue.** For each topic covered, judge familiarity —
   🔴 shaky · 🟡 partial · 🟢 solid — and update `05-Resources/review-queue.md`: upsert the row
   with confidence, `last quizzed` = today, and the specific **gaps to review**. Re-rank
   weakest-first; retire consistently-🟢 items to the bottom.
5. **Report.** Short recap: what was solid, what to brush up (link the queue), which notes you
   updated with their viewpoints.

## Rules
- **Question first, teach second** — this is active recall, not a lecture.
- The user's opinions are first-class knowledge: capture them attributed and specific, don't
  paraphrase into blandness.
- Honor the guardrails: propose note edits, apply on approval; run `link-check` after edits.
- Pairs with `add-person` (quiz yourself on someone you just added to expose blind spots) and
  `ingest-discussion` (which uses the same `My take` viewpoint convention).
