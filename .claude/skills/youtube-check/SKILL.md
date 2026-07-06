---
name: youtube-check
description: Check tracked YouTube playlists for new videos not yet ingested into otto and create grounded notes for them (e.g. new lectures in the Summer Thoughts series). Use when the user asks to check for new videos, ingest a lecture/talk video, or as part of the weekly review.
---

# youtube-check

Ingest new videos from tracked playlists into otto. A playlist is "tracked" if some note has a
`playlist:` frontmatter field (e.g. [[summer-thoughts-on-autonomy]]); a video is "ingested" if
its id appears in some note's `video:` field.

## Procedure
1. **Detect.** Run `.claude/scripts/youtube-check` and report its output. It discovers tracked
   playlists, fetches each public RSS feed, and lists videos whose id isn't yet in any note.
2. **Ingest each new video** as a note modeled on the existing lecture notes in
   `01-Projects/talks/summer-thoughts-on-autonomy/`:
   - Pull the video's title + `<media:description>` from the feed
     (`https://www.youtube.com/feeds/videos.xml?playlist_id=<ID>`).
   - Frontmatter: `type: project`, apt taxonomy `tags`, `recorded:` (published date),
     `video:` (the `youtu.be/<id>` URL — this is what marks it ingested), `series:` (link to
     the hub).
   - Body: summary **from the description** (the user's own words — don't fabricate beyond it),
     a short "Key ideas" scaffold for the user to expand, and grounded links to the concepts /
     papers it touches.
3. **Wire it in.** Add the new lecture to its series hub's list, and (if it's a new series) add
   a hub note with a `playlist:` field so future runs track it. Consider the website
   `/lectures/` page (via the `website-check` skill) if the series is published there.
4. **Verify.** Run `.claude/scripts/link-check`; report the result.

## Rules
- Never invent lecture content beyond the published description — leave a scaffold to fill in.
- Keep filings under `01-Projects/talks/`; the taxonomy has no `talk`/`lecture` type yet
  (using `type: project`) — flag if that becomes worth adding to the schema.
