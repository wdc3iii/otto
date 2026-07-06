---
name: linkedin-check
description: Flag what should be updated on the user's LinkedIn — new first-author papers, new public projects (e.g. the lecture series), role changes — by comparing the otto publication record and active projects against the LinkedIn snapshot in 05-Resources/linkedin.md. LinkedIn is bot-blocked (HTTP 999), so this produces a MANUAL update checklist, not a live scrape. Use on request or in the weekly review.
---

# linkedin-check

Surface what's likely out of date on [LinkedIn](https://www.linkedin.com/in/will-compton/).
LinkedIn can't be fetched by bots (HTTP 999), so [[linkedin]] is a hand-maintained mirror and
this skill produces a checklist to update by hand.

## Procedure
1. **Read the mirror.** Open [[linkedin]] (`05-Resources/linkedin.md`): its "Current snapshot"
   (what's on the profile) and "Pending updates".
2. **Compare** against:
   - [[publication-record]] — any first-author (or notable) paper not reflected on the profile.
   - Active projects in `01-Projects/` — public outputs, especially anything with a `playlist:`
     or website page (e.g. [[summer-thoughts-on-autonomy]]).
3. **Report a checklist** of concrete edits (add project X, add publication Y). Merge with the
   "Pending updates" already in [[linkedin]]; check off anything now done.
4. **Refresh the mirror on request.** If the user pastes current profile text, update the
   "Current snapshot" in [[linkedin]] so future diffs are accurate.

## Rules
- **Low-key.** The user doesn't actively post on LinkedIn — surface project/publication gaps as
  a one-time checklist; do not nag about posting cadence or engagement.
- Never claim to have read the live profile — everything here is from the otto mirror unless the
  user provides fresh text.
