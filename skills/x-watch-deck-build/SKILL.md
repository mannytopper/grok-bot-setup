---
name: x-watch-deck-build
description: >-
  Use when running a periodic X (Twitter) watch for posts about a topic and
  turning new finds into a PowerPoint deck plus an email summary, skipping
  anything already reported.
---
# X watch and deck build

Inputs come from the routine: search terms, the period covered (since the last run), the output folder, the recipient, and the email subject format.

## Steps
1. **Search.** Use the built-in X tools (public search, posts, users), not the browser, to find posts since the last run that match the search terms.
2. **Dedupe.** Skip post IDs listed in earlier `ids-YYYY-MM-DD.txt` files in the output folder and in memory. Skip spam and off-topic matches. Never invent posts, authors, links or engagement numbers.
3. **Describe each find:** its title or first line, the author's @handle, `https://x.com/<handle>/status/<id>`, and a one-line summary. Mark it `promising: true` with a short reason when it clearly stands out (high engagement for its age, a well-known account, or an especially useful idea).
4. **Write `finds-YYYY-MM-DD.json`:** `{"date","date_label","range_label","finds":[{"title","author","url","summary","promising","reason"}]}`.
5. **Build** with the reusable builder: `python3 build.py finds-YYYY-MM-DD.json` (for example in `/workspace/grok-x-watch/`). It writes `grok-x-watch-DATE.pptx`, `body-DATE.txt` and `ids-DATE.txt`, with promising finds first. Don't write one-off per-day build scripts. Change `build.py` if the layout needs to change.
6. **Email.** Check Sent for today's subject first and never send twice. Send one Gmail with the body text and the .pptx attached directly. If the connector needs the attachment's encoded content, write it to a `.b64` file and pass the argument as `$file:/path/to/file.b64`; never paste base64 text into the tool call. If nothing is new, send a short "Nothing new." email with no deck.
7. **Log** the reported IDs (they're in `ids-DATE.txt`) and save a short memory fact.
