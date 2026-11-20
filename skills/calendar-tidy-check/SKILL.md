---
name: calendar-tidy-check
description: >-
  Use when checking the user's upcoming calendar for clashes, unanswered or
  tentative invites and placeholder events, including the heads-up section of
  the morning rundown.
---
# Calendar tidy check

Script: `python3 /workspace/calendar-tidy/tidy_check.py [--cache FILE] [--today YYYY-MM-DD] [--days 14] [--exceptions /workspace/calendar-tidy/exceptions.json]`. It reads the newest calsync rundown cache (`/workspace/calsync/rundown-cache-YYYY-MM-DD.json`) and prints JSON with `conflicts`, `unanswered_invites` and `notes` (placeholders), ready for the rundown `heads_up` block. The exceptions file is a JSON list of title substrings never to flag (for example "hatzalah"); add to it when the user says an item is deliberate. The check runs inside the morning rundown, which shows "Overlaps / conflicts" and "Unanswered invites" from the `heads_up` block of its data JSON (`/workspace/morning-rundown/README.md`). Use this skill to fill that block, or to run the check on request.

## Steps
Run the script first; do the steps below by hand only for dates the cache does not cover, or to review its output.
1. **Window:** today through about 2 weeks ahead (Eastern time).
2. **Events:** reuse the same morning's calendar pulls (calsync rundown cache and the calendar dashboard's events) before calling the calendar connectors. Fetch only dates no pull covers.
3. **Flag:**
   - same-day clashes: events whose times overlap, and timed events on the same day as an all-day or untimed commitment that may clash;
   - invites the user hasn't answered, and RSVPs left tentative;
   - placeholders: holds or blocks with no real details, or with a time range that looks like a hold.
4. **Skip deliberate items:** do not flag anything the user said was deliberate. Check memory for such notes and the exceptions file if it exists. Don't re-flag an item already flagged unless it changed.
5. **Report:** for the rundown, put short lines in `heads_up.conflicts` and `heads_up.unanswered_invites` (an empty list shows "None"); placeholders can go in `heads_up.notes`. On request, reply in chat with the same items, each with date, time and what to decide.
6. Read only. Never accept, decline, move or delete events without the user's yes.
