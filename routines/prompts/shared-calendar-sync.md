Moved from Connor to Routines on Nov 16, 2026 (Manny said yes). Wherever this says "this Grok Bot chat" or "Connor's chat", it now means the Routines chat. Every send rule, recipient limit and gate below is unchanged.

---
Wakes: Manny approved on Nov 6, 2026 switching this sync from every morning to (a) a webhook ping that his Power Automate flow sends whenever an event on his Outlook calendar is added, updated or deleted, plus (b) one full reconcile run every Sunday at about 6:30 AM ET. A burst of Outlook edits can send several pings close together; that's expected. Each wake just runs the change check below, and when nothing differs it writes nothing and ends quietly.

Gate first (no-AI script, routine-gate skill, Manny approved Nov 6, 2026): run `python3 /workspace/common/routine_gate.py --days Sun,Mon,Tue,Wed,Thu,Fri`. Exit 10 means skip (Shabbat, Saturday or Yom Tov): do nothing and send nothing; the next wake or Sunday reconcile catches up. If the script errors, fall back to checking yourself: never run on Shabbat (Saturday) or a Jewish holiday (Yom Tov); if today is Yom Tov, skip silently.

This routine has two steps. Do step 1 first, then step 2. Work efficiently: write only what actually changed. On a webhook wake, step 2 may be limited to the Outlook copies (the primary-calendar events carrying an [outlook:] marker) and their shared copies; the Sunday reconcile always does the full step 2 for every source.

Batch writes: when several events need creating or updating, use the Google Calendar connector's batch tools (create or update up to 50 events per call) instead of one call per event. If a batch call fails or isn't available, fall back to one call per event for the affected items. Check results so nothing is created twice.

Change check (both steps): keep a state file at /workspace/calsync/state.json mapping each source event id to its last-seen "updated" timestamp (or a hash of title, start, end, location, description, status) and to its copy's id. For each source event, if the stored value matches and the copy still exists, skip it with no write. Only create, update, or delete when something differs. Update the state file at the end of each step.

Step 1: Outlook to Google.
- Read Manny's Outlook calendar (the user-Outlook-calendar connector) for today through the next 60 days.
- Copy each meeting into his primary Google Calendar (mannytopper@gmail.com) with the same title, time, location, and a short description.
- Put [outlook:<outlookEventId>] in each copy's description.
- Create copies that are missing, update copies whose details changed, and delete copies whose Outlook meeting is gone or cancelled.
- Don't add attendees and don't send notifications.
- Never touch Google events that have no outlook marker.

Step 2: shared calendar.
- Sync Manny's events into the shared calendar "Manny and Ronit's Calendar" (ID 4db3b7567d51f0e360c5c30a996e34e1715c794a1995c684e2a628b37990e365@group.calendar.google.com). Ronit has edit access at [REDACTED].
- Sources: mannytopper@gmail.com (primary, including the Outlook copies from step 1), the TA calendar, and HCC Tee Times. Never copy from the Mom & Dad Medical or Hatzalah calendars.
- Window: today through the next 60 days.
- Each copy carries the marker [sync:<srcCalId>:<eventId>] in its description.
- Recurring series: when the source is a recurring event series that the connector exposes as a series (with a recurrence rule), copy it as ONE recurring event with the same rule, marked [sync:<srcCalId>:<seriesId>], instead of one copy per instance. The first time a series is handled this way, delete the older per-instance copies of that same series (their markers point at instances of that series id) so nothing shows twice. If the connector can't create a recurring event, fall back to per-instance copies.
- Create copies that are missing, update copies whose title, time, location, or description changed, and delete copies whose source event is gone or cancelled.
- Never touch events that have no sync marker. Those are Ronit's own additions.
- Don't add attendees and don't send notifications.

Rundown cache: after step 2, when this run read the primary, TA and HCC Tee Times calendars, save those events for today through the next 7 days (title, start, end, location, calendar, attendee response status for Manny) to /workspace/calsync/rundown-cache-YYYY-MM-DD.json. The 6:45 AM morning run reuses it when it exists for today and reads the calendars itself when it doesn't, so a missing cache is fine.

Run on Connor's computer only. Delivery: no one is messaged on success or when nothing changed. Message Manny in this Grok Bot chat (Connor's chat) only if a run fails, in one short line.
