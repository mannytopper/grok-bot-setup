# Weekday local feed (owner: Murray · Family and Home, folder: weekday-local-feed)

- **Owner bot:** Murray · Family and Home
- **Original folder id:** `weekday-local-feed`
- **Enabled state:** Enabled
- **Schedule/trigger:** `CRON_TZ=America/New_York 0 8 * * 1-5` (weekdays around 8:00 AM ET)
- **Timing:** Flexible, 15 minutes early or late
- **Connectors/accounts:** None. Uses WebFetch, WebSearch, and curl. No local execution.
- **Scripts:** `/workspace/common/routine_gate.py`, with `/workspace/common/shabbat_gate.py` as the fallback (exit 10 = skip silently). Invoked as `python3 /workspace/common/routine_gate.py --days Mon,Tue,Wed,Thu,Fri`. Also `/workspace/family-home/scripts/local_feed_dedupe.py`.
- **Skills:** local-feed-routine, routine-gate, shabbat-gate
- **Files/state:** `/workspace/family-home/local-feed.md` and `local-delivered.md`, plus the dedupe script above.
- **Memory facts:** Manny keeps Shabbat and Yom Tov. Alerts and results go to chat only, never email. The bot never buys anything. Routines are passive. Printables are black and white. Home area is Pikesville, MD 21208 (needed for the local feed). Callaway watch stays paused and untouched.
- **Permissions:** None. Chat only, never email.
- **Hooks:** None
- **Open issues:** None beyond the shared Murray move. No hook or local execution.

## Original prompt (verbatim)

```
First run `python3 /workspace/common/routine_gate.py --days Mon,Tue,Wed,Thu,Fri` following @routine-gate. Exit 10 means skip silently; exit 0 means continue. Only if the gate errors, use the previous Shabbat/Yom Tov check (`python3 /workspace/common/shabbat_gate.py`) as fallback; skip silently on Shabbat or Yom Tov. If neither check can establish that work is allowed, do not proceed and report the failure when permitted. Read /workspace/shared-brain/INDEX.md and apply anything relevant before continuing.

Weekdays at 8:00 AM local: sweep public city/county feeds and deliver weekend/wallet/street cards. Follow @Local feed routine, working in /workspace/family-home (script: scripts/local_feed_dedupe.py). Start with `cd /workspace/family-home && python3 scripts/local_feed_dedupe.py fetch` for raw candidates; for sources it reports blocked, error, or empty (for example Baltimore County news and Aging events, Baltimore Jewish Life) and for the other sources in local-feed.md, fall back to the current method: WebFetch, curl, and web search. Before posting, run the candidates through `python3 scripts/local_feed_dedupe.py check`, and after posting, log them with `append`. If the script is missing or broken, do the sweep and dedupe by hand against local-delivered.md.

Sweep public records, calendars, and news for the user's city and county only (not a neighboring metro unless it directly hits the county). Center on the home area: Pikesville, Baltimore County, MD 21208. Baltimore City only when it directly affects the county or a Pikesville resident (for example, closures on main routes in and out such as the JFX/I-83). Place not people. No contacting anyone. Do not invent a place.

Read /workspace/family-home/local-feed.md first for the sources to use, what qualifies, what to leave out, and the items being tracked for changes (Falls Road MD 25 overnight patching, Smash House at 1500 Reisterstown Rd, Hidden Waters Cafe at 3250 Old Court Rd, the southbound JFX right-lane closure).

Weekend items: Sunday, Friday daytime, and Motzei Shabbos count; leave out Saturday-daytime and Shabbat-only events, since Manny keeps Shabbat. Wallet items: household taxes, fees, rates, assessments, utility costs, refunds, deadlines (not nonprofit-only). Street items: road closures and construction on routes he'd use, permits or zoning in or near 21208, nearby business openings, closings, or inspections, and public input on local projects. Leave out anything outside the county unless it directly affects it, niche paid events, council items with nothing specific to Pikesville, and unconfirmed claims.

Owed items: /workspace/family-home/local-delivered.md may have an "Owed to Manny" section listing items found earlier that were never posted. Re-find and open each one's source, confirm it still qualifies, and include it as a normal card, then move it to the Delivered log. Drop any owed item that can't be confirmed or has passed.

New items only: drop any item already delivered (same project, event, or business) per the dedupe check, local-delivered.md, and this conversation's earlier messages, unless something materially changed (new dates, a cancellation, an actual opening, a new cost); then send only the change in one line.

Each card: headline in plain English; 2-3 sentences a stranger would get; Why it matters (weekend/wallet/street); Retrieved date/time in the user's local timezone; Source name + full URL. No source, no item. Every item needs a source URL that was actually opened.

Type extras: Road closure: dates/times, from/to, Google Maps of the closed stretch. Public event: start-end, cost/rain if listed, venue map. Permit/zoning: plain-English ask, hearing date, comment how-to if listed, parcel map. Business open/close/inspection: kind of shop, address map, date. Council/agenda: meeting datetime, the ONE relevant item, packet link. Map links use Google Maps search or directions URLs.

Quiet hours 12am-6am local. Cite-or-omit. Do not invent. The user observes Shabbat and Jewish holidays (Yom Tov).

Passive delivery (Manny, Nov 5, 2026): post new qualifying cards to Manny in this Grok Bot chat only, never by email or anywhere else. Stay silent and send nothing on success-only, nothing-new, or routine-status runs. Message only when he needs to act or decide, or when something failed. If nothing new qualifies, send nothing at all and log nothing.
```

## Proposed Routines-copy prompt

```
Read /workspace/routines/context/weekday-local-feed.md for context.

First run `python3 /workspace/common/routine_gate.py --days Mon,Tue,Wed,Thu,Fri` following @routine-gate. Exit 10 means skip silently; exit 0 means continue. Only if the gate errors, use the previous Shabbat/Yom Tov check (`python3 /workspace/common/shabbat_gate.py`) as fallback; skip silently on Shabbat or Yom Tov. If neither check can establish that work is allowed, do not proceed and report the failure when permitted. Read /workspace/shared-brain/INDEX.md and apply anything relevant before continuing.

Weekdays at 8:00 AM local: sweep public city/county feeds and deliver weekend/wallet/street cards. Follow @Local feed routine, working in /workspace/family-home (script: scripts/local_feed_dedupe.py). Start with `cd /workspace/family-home && python3 scripts/local_feed_dedupe.py fetch` for raw candidates; for sources it reports blocked, error, or empty (for example Baltimore County news and Aging events, Baltimore Jewish Life) and for the other sources in local-feed.md, fall back to the current method: WebFetch, curl, and web search. Before posting, run the candidates through `python3 scripts/local_feed_dedupe.py check`, and after posting, log them with `append`. If the script is missing or broken, do the sweep and dedupe by hand against local-delivered.md.

Sweep public records, calendars, and news for the user's city and county only (not a neighboring metro unless it directly hits the county). Center on the home area: Pikesville, Baltimore County, MD 21208. Baltimore City only when it directly affects the county or a Pikesville resident (for example, closures on main routes in and out such as the JFX/I-83). Place not people. No contacting anyone. Do not invent a place.

Read /workspace/family-home/local-feed.md first for the sources to use, what qualifies, what to leave out, and the items being tracked for changes (Falls Road MD 25 overnight patching, Smash House at 1500 Reisterstown Rd, Hidden Waters Cafe at 3250 Old Court Rd, the southbound JFX right-lane closure).

Weekend items: Sunday, Friday daytime, and Motzei Shabbos count; leave out Saturday-daytime and Shabbat-only events, since Manny keeps Shabbat. Wallet items: household taxes, fees, rates, assessments, utility costs, refunds, deadlines (not nonprofit-only). Street items: road closures and construction on routes he'd use, permits or zoning in or near 21208, nearby business openings, closings, or inspections, and public input on local projects. Leave out anything outside the county unless it directly affects it, niche paid events, council items with nothing specific to Pikesville, and unconfirmed claims.

Owed items: /workspace/family-home/local-delivered.md may have an "Owed to Manny" section listing items found earlier that were never posted. Re-find and open each one's source, confirm it still qualifies, and include it as a normal card, then move it to the Delivered log. Drop any owed item that can't be confirmed or has passed.

New items only: drop any item already delivered (same project, event, or business) per the dedupe check, local-delivered.md, and this conversation's earlier messages, unless something materially changed (new dates, a cancellation, an actual opening, a new cost); then send only the change in one line.

Each card: headline in plain English; 2-3 sentences a stranger would get; Why it matters (weekend/wallet/street); Retrieved date/time in the user's local timezone; Source name + full URL. No source, no item. Every item needs a source URL that was actually opened.

Type extras: Road closure: dates/times, from/to, Google Maps of the closed stretch. Public event: start-end, cost/rain if listed, venue map. Permit/zoning: plain-English ask, hearing date, comment how-to if listed, parcel map. Business open/close/inspection: kind of shop, address map, date. Council/agenda: meeting datetime, the ONE relevant item, packet link. Map links use Google Maps search or directions URLs.

Quiet hours 12am-6am local. Cite-or-omit. Do not invent. The user observes Shabbat and Jewish holidays (Yom Tov).

Passive delivery (Manny, Nov 5, 2026): post new qualifying cards to Manny in the Routines chat in Grok Bot only, never by email or anywhere else. Stay silent and send nothing on success-only, nothing-new, or routine-status runs. Message only when he needs to act or decide, or when something failed. If nothing new qualifies, send nothing at all and log nothing.
```
