---
name: calendar-one-way-sync
description: >-
  Use when copying events one way from one calendar to another (for example
  Outlook to Google, or personal calendars into a shared family calendar) on a
  schedule, with change tracking so only real changes are written.
---
# One-way calendar sync with change tracking

Inputs come from the routine: source calendars, target calendar, window (for example today plus 60 days), the marker format, calendars that must never be copied, and the state and cache file paths.

## Rules
- Skip silently on the user's rest days or holidays if the routine says so. Use a holiday-check script if one exists, for example `python3 /workspace/common/hebcal_check.py`.
- Never add attendees and never send notifications.
- Never touch target events that don't carry this sync's marker, because those are other people's own entries.
- Use read-only connectors on the sources. Use batch create and update tools on the target (up to 50 per call), and fall back to single calls if a batch fails. Check results so nothing is created twice.

## Steps
1. **Load state.** Read the state file, which maps each source event id to its last-seen `updated` timestamp (or a hash of title, start, end, location, description and status) and to its copy's id.
2. **Read sources** for the window through the calendar connectors.
3. **Diff.**
   - If the stored value matches and the copy still exists, skip it.
   - If an event is new, create a copy with the same title, time and location, a short description, and a marker such as `[sync:<srcCalId>:<eventId>]` or `[outlook:<id>]`.
   - If an event changed, update its copy.
   - If a source event is gone or cancelled, delete its copy, but only copies with this sync's marker.
4. **Recurring series.** When the connector exposes a series with a recurrence rule, copy it as one recurring event marked with the series id. The first time you do this, delete the older per-instance copies of that series. If the connector can't create recurring events, copy each instance.
5. **Leave alone** any copy that someone deliberately retitled on the target when the source hasn't changed, and note it.
6. **Prune state** for events now outside the window, without deleting anything.
7. **Save state.** Optionally write a short cache, for example the next 7 days of events as JSON, so later routines such as a morning rundown can reuse it instead of re-reading the calendars.
8. **Report.** Say nothing in chat on success unless the routine says otherwise. On failure, send one line saying what failed.
