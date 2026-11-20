---
name: Local feed routine
description: >-
  Use when a daily routine posts local news and event cards from a fixed source
  list without repeats, using local_feed_dedupe.py to fetch candidates, check
  them against a delivered log, and log what was posted.
---
# Local feed routine (fetch, judge, dedupe, post)

The routine that runs this skill names the folder holding the script, the rules file, and the delivered log.

## Files
- `scripts/local_feed_dedupe.py`, with three commands: `fetch` pulls raw candidates, `check` dedupes them, and `append` logs what was posted.
- The feed rules file, which lists the sources, what qualifies, the card format, and tracked items.
- The delivered file, which holds a dated Delivered log plus tracked and owed items.

## Steps
1. If the routine says to skip rest days or holidays, skip the run on those days.
2. Run `python3 scripts/local_feed_dedupe.py fetch`, or add `--source NAME` for one source. Its results are only raw material. For any source marked blocked, error, or empty, use WebFetch on that source's URL. For the other sources in the rules file, use web search.
3. Judge each candidate against the rules: location, date window, and rest days. Open every source you cite. If an item has no source you opened, leave it out, and never invent details.
4. Put the items that qualify in a JSON list like `[{"title":..,"url":..,"date":..,"venue":..,"source":..,"summary":..}]`. Run `python3 scripts/local_feed_dedupe.py check items.json` and post only the items it lists under `new`. Look over `duplicates` before dropping anything, since the matching is approximate.
5. Check the owed and tracked items too. Mention a tracked item only when something about it changed.
6. Post the cards in the format the rules file gives.
7. Log only what you posted: `python3 scripts/local_feed_dedupe.py append posted.json`.

## Quiet rule
- Stay silent when nothing qualifies: send nothing and log nothing. Message only when there are new cards to deliver, or when something failed that needs attention.

## Limits
- Some government sites send scripts a bot challenge (HTTP 202 or 403). Those sources come back as blocked, so use WebFetch for them.
- To test without touching the real log, set `LOCAL_DELIVERED=/path/to/copy.md`.
