# Routines by bot (as known 2026-11-05, Connor). All are passive and skip Shabbat and Yom Tov.

## Connor
- Shared calendar sync: 6:30 AM ET Sun–Fri. Outlook into Google, then into "Manny and Ronit's calendar". Message only on failure.
- Morning combined run: about 6:45 AM ET Sun–Fri. Parts: A calendar dashboard, B rundown PDF (emailed to mannytopper@gmail.com), C inbox digest, D Tesla/Enhance/Clicks watch, E domain digest, F X watch (Mon/Wed/Fri). D and E run Mondays only (Manny, Nov 13, 2026). Skill: morning-combined-run.
- Desk login (webhook from laptop at weekday login): Payment claims, then Download Detail MT. Once a day, weekdays only, silent on success.
- Weekly Grok Bot setup review: Mondays about 6:45 AM ET.
- Weekly usage dashboard refresh (Connor): PAUSED Nov 13, 2026 (Manny). Alfred's Grokbot dashboard refresh is the only dashboard.
- One-time: Bank of America connector reminder Nov 13, 2026, 9:00 AM ET; Griot's check-in Dec 10, 2026.
- Calendar dashboard refresh: about 6:30 AM ET Sun–Fri (now part A of the morning run).

## Other bots
- Murray: Family price watches Sun–Fri about 6:01 AM ET (silent unless a target hits; Callaway watch paused Nov 4). Weekday local feed Mon–Fri about 8:00 AM ET (posts only new cards; silent when nothing new). Both use /workspace/family-home scripts with WebFetch fallback.
- Insurance info · Meeting Prep (corrected 2026-11-05, Insurance info · Meeting Prep):
  - Wiki sync: runs on the laptop-login webhook, once a day. It messages only when files were removed or the sync fails.
  - Staff insurance-question replies: email to mtopper@ / mtopper+insurance@mail.grokbot.com from @wealcatchmd.com, @wealcatchaz.com or @wealcatch.com gets an automatic reply under Manny's standing permission of Oct 14, 2026. It messages him only when a send waits for him, fails, or the manuals don't cover the question.
  - Meeting prep: wakes on an email that a Power Automate flow sends to the bot inbox about 2 hours before each Outlook event, plus a 7 AM ET backup sweep Mon–Fri, skipping Yom Tov, that also covers the next prep day's meetings before 9:30 AM (Friday covers Monday). Since Nov 6, 2026. It is silent when nothing needs prep and shows each draft for his input.
  - Open office follow-ups watch: weekdays around 9:30 AM ET, a narrow search on the named open items in /workspace/insurance-ops/followups-watch.json. It messages Manny only when something new comes in, and drops items once they are resolved (since Nov 6, 2026).
- Parsha: Friday weekly parsha sheet.
- Bot Optomizer: all Friday jobs PAUSED and moved to Dreamer (Nov 5, 2026): fleet audit, X tips, scorecard, routine ideas. No enabled routines left; delete bot after Dreamer's first clean combined run.
- Alfred · Bot Chief Advisor:
  - Grokbot dashboard refresh: DELETED Nov 16, 2026 (Manny). The dashboard Page stays but is no longer refreshed.
  - Weekly Company & Grok Bot Improvement Review (Alfred original): DELETED Nov 16, 2026 (Manny). The Routines copy (Fridays about 10:30 AM ET, asks first, no printing) is the only one.
  - Monthly Bot Portfolio Strategy Review: paused.
  - Quarterly Company & AI Operating Model Review: paused.
- Spackler: one routine, already quiet (details in Spackler's chat). (replaced 2026-11-05)
- (2026-11-05, Spackler - Golf Practice) Muni Golf iPad app watch: PAUSED since Nov 4, 2026 (Manny approved via Bot Optomizer), not deleted. When on, it runs Sundays about 6:45 AM ET (moved from daily on Nov 3). It checks munigolfsim.com and the App Store, stays silent unless the iPad app is publicly released (then messages Manny with the link and deletes itself), skips Shabbat and Yom Tov, and ends on Apr 30, 2027.
- Dan, Forge: no routines.
- (2026-11-05, Parsha · Weekly Teen Parsha PDF) Weekly teen parsha sheet: Fridays 9:30 AM ET via Weekly Parsha PDF routine. Scripted build at /home/box/parsha/build/ (build_parsha.py + content JSON); hebcal_week.py exits 2 on Yom Tov (build nothing, stay silent). Skill: weekly-parsha-sheet-build. Delivers PDF to C:\Users\Manny\Documents\Parsha on WHI-LT-26-03, prints one copy (Brother HL-L2420DW), closes Adobe. Backup check (9:52 AM ET) is paused, not deleted (Manny Nov 4). Greeting: Good Shabbos.
- (2026-11-05, Bot Optomizer) Weekly bot fleet audit (replaced 2026-11-05 — moved to Dreamer): Fridays around 9:30 AM ET (`CRON_TZ=America/New_York 30 9 * * 5`, flexible ±15 min). Standing HTML+PDF report still goes to Manny in Bot Optomizer chat; otherwise passive. Skip and send nothing on Yom Tov or if /workspace/bot-audit/history/ already has today's snapshot. "Largest chats this week" is information only (app cannot clear one bot's chat); never tell him to clear chats. Render with `python3 /workspace/bot-audit/audit.py INPUT.json` (WeasyPrint venv; headless Chrome hangs). Skill: bot-fleet-usage-audit.
- (2026-11-05, Bot Optomizer) Weekly routine ideas (replaced 2026-11-05 — moved to Dreamer): Fridays around 10 AM ET. Suggests five new time-saving routines ranked by impact on office, family/home, and golf goals. Never creates them until Manny says which.
- (2026-11-05, Bot Optomizer) Weekly Grok Bot X tips (replaced 2026-11-05 — moved to Dreamer): Fridays around 9 AM ET. Scans public X for practical Grok Bot tips; messages only when something new and useful; seen log at /workspace/bot-audit/x-tips-seen.md.
- (2026-11-05, Bot Optomizer) Weekly bot scorecard (replaced 2026-11-05 — moved to Dreamer): Fridays around 9:45 AM ET. Scores each bot /10, one miss, one suggested fix; changes nothing until Manny says ok.
- (2026-11-05, Bot Optomizer) Weekly bot fleet audit moved to Dreamer. Dreamer's copy enabled Fridays ~9:30 AM ET; Bot Optomizer's weekly-bot-fleet-audit is paused (not deleted) so tomorrow does not double-run. Scripts/history stay at /workspace/bot-audit/.
- (2026-11-05, Bot Optomizer) X tips (~9 AM), scorecard (~9:45 AM), and routine ideas (~10 AM) moved to Dreamer. Bot Optomizer paused weekly-grok-bot-x-tips, weekly-bot-scorecard, and weekly-routine-ideas. No enabled routines remain on Bot Optomizer.
- (2026-11-06, Email Purger) Monthly Gmail cleanout on Email Purger: first Monday 8 AM ET (`0 8 1-7 * 1`), passive proposal-only for mannytopper@gmail.com; never auto-delete/unsubscribe without Manny's yes.
- (2026-11-06, Forge) Usage Guard: Weekly usage guard routine created **disabled**. Manual runs for first two weeks; enable Mondays 8:45 AM ET (`45 8 * * 1` America/New_York) only after Manny confirms. Passive; Shabbat/Yom Tov gated. After first good manual run, propose pausing Dreamer’s Friday ~9:30 AM fleet usage audit (duplicate); keep Dreamer’s other Friday jobs.
- (2026-11-06, Usage Guard) Weekly usage guard: Mondays about 8:45 AM ET, created PAUSED. Manny runs it manually for two weeks, then enables it only after he confirms. Passive; proposes fixes for his yes or no, never changes other bots. Snapshots in /workspace/usage-guard/history/.
- (2026-11-06, Usage Guard) Manny approved: Dreamer's Friday weekly fleet usage audit to be paused (not deleted) after Nov 6 11 AM; Usage Guard's weekly review replaces it. Insurance info meeting prep cut to 7 AM and 11 AM ET (11 AM preps next morning's early meetings).

- (2026-11-06, Murray · Family and Home) Replaces prior Murray daily-price schedule: FLY5D, BESTGLOAL and GLISTON now use three tagged-inbox CamelCamelCamel email triggers; no daily price polling. Callaway remains paused. Local feed schedule is unchanged.
- (2026-11-06, Spackler - Golf Practice) Golf practice evening reminder: Sun, Mon, Wed about 7:50 PM ET (±10 min), gated by routine_gate.py --days Sun,Mon,Wed --evening; sends Manny that night's three blocks from practice-plan-v2. Muni watch still paused.

- (2026-11-06, Email Purger) Biweekly work Outlook cleanout on Email Purger: Mondays about 8:15 AM ET (`15 8 * * 1`), biweekly via /workspace/email-purger/work-cleanout-state.json (skip if lastRun within 13 days); proposal-only for manny@wealcatchmd.com; routine_gate + email-purger-group; never auto-delete/unsubscribe without Manny's yes.
- (2026-11-06, Murray · Family and Home) Miami trip daily brief: Sun–Thu about 7:00 AM ET Nov 8–12 2026 only; one short card from /workspace/Miami-Trip-Plan-Nov-2026.md; deletes after Nov 12 or landing. Folder miami-trip-daily-brief.

- 2026-11-06 (Connor): Gmail $file: attachments: delete the .b64 copy right after the send succeeds (and any older .b64 in that folder); keep the PDF/PPTX. domain-research/prep_send.py --mark-sent now does this itself.
- (2026-11-06, Murray · Family and Home) Order concierge sweep: weekdays about 9:15 AM ET; personal Gmail for new shipping/delivery/exception/refund mail; updates /workspace/family-home/orders-state.json; messages only on actionable changes; no product-page price polling; gated by routine_gate. Folder order-concierge-sweep. On-demand returns/claims/tracking stay in Murray chat.


- (2026-11-12, Forge) Routines bot created. All routines on every bot except Usage Guard move to Routines: copy, grant permissions, repoint hooks, pause original, one good run, then delete originals only on Manny's yes. New routine requests from any bot go to Routines. Weekly sweep Mondays 9:00 AM ET.

- (2026-11-12, Routines) Move kickoff: details requested from 8 bots; weekly sweep routine live Mondays 9 AM ET. Log: /workspace/routines/moves.md.

- (2026-11-12, Murray · Family and Home) Miami trip daily brief: posted the Nov 12 departure-day card and deleted the finite routine (window ended).
- (2026-11-13, Routines) Per Manny (Nov 13, 2026, in Connor's chat): Routines' "Weekly bot scorecard" is PAUSED (not deleted); Alfred's Friday review is the only team review. "Nightly dreaming" on Routines now runs Fridays only, around 11:00 AM ET (routine_gate --days Fri), and each run covers everything since the previous Friday's run. Dreamer's original stays paused. Connor's weekly usage dashboard refresh is paused; Alfred's Grokbot dashboard is the only dashboard.
- (2026-11-16, Routines) Usage Guard folded into Volt - Usage Audit (Manny's yes in Usage Guard chat, 9:29 AM ET). Routines never touches Usage Guard or Volt routines, files or settings; Usage Guard's paused 'Weekly usage guard' stays paused, not deleted; no Volt schedule without Manny's own separate yes.
