# Box scripts (updated 2026-11-05, Connor)
All under /workspace. A mirrored, tested copy lives in /workspace/manny-automation (README has the full table; `./test.sh` runs offline tests).

| Job | Entry command |
|---|---|
| Shabbat / Yom Tov gate | `python3 /workspace/common/shabbat_gate.py [--evening] [--date D]` (exit 10 = skip); also hebcal_check.py |
| Never-send-twice ledger | `python3 /workspace/common/sent_marker.py check|mark KEY` |
| Decision queue | `python3 /workspace/decision-queue/dq.py list --open / add / close / defer / edit` |
| Calendar tidy check | `python3 /workspace/calendar-tidy/tidy_check.py [--cache F]` |
| Calendar dashboard (incremental) | /workspace/cal-dashboard/ (plan_fetch.py, merge.py, build.py); see its README |
| Shared calendar sync | /workspace/calsync/; see skill calendar-one-way-sync |
| Morning rundown PDF | `python3 /workspace/morning-rundown/make_rundown.py --data D.json --out O.pdf --auto-weather --auto-blues` |
| Inbox digest one-pager | `python3 /workspace/inbox-digest/render.py DATE.json` (PNG + PDF) |
| Blues recap PDF | `python3 /workspace/blues-recap/make_recap.py [--since YYYY-MM-DD]` |
| Domain digest send prep | `python3 /workspace/domain-research/prep_send.py DATE` then `--mark-sent <msg id>` (blocks b52 recipients) |
| X watch deck | /workspace/grok-x-watch/build.py; see skill x-watch-deck-build |
| Tesla recall watch | /workspace/tesla-watch/check.py |
| Download Detail date range | `python3 /workspace/ams/dd_date_range.py [--date D]` |
| Download Detail cleanup | `python3 /workspace/ams/clean_download_detail.py IN.xlsx OUT.xlsx` (drops Renew policy and Policy change rows) |
| Usage dashboard data block | /workspace/manny-automation/scripts/usage-dashboard/make_data_block.py usage.json |
| Bot fleet audit | `python3 /workspace/bot-audit/audit.py INPUT.json` |
| Murray price watches | `cd /workspace/family-home && python3 scripts/price_watch.py check` then `record FILE.json` (state: price-state.json; log: price-history.md) |
| Murray local feed | `cd /workspace/family-home && python3 scripts/local_feed_dedupe.py fetch` then `check` / `append` (log: local-delivered.md; rules: local-feed.md) |
| Insurable or Not site | /workspace/insurable-or-not/ (README) |
| Weekly teen parsha PDF | `python3 /home/box/parsha/build/hebcal_week.py` then `python3 /home/box/parsha/build/build_parsha.py CONTENT.json -o OUT.pdf` (see /home/box/parsha/build/README.md); skill weekly-parsha-sheet-build |
- (2026-11-05, Bot Optomizer) Bot fleet audit snapshots live in /workspace/bot-audit/history/YYYY-MM-DD.json for week-over-week compare. Sample input and README are under /workspace/bot-audit/. Use the .venv there for WeasyPrint.
- (2026-11-05, Insurance info · Meeting Prep) Meeting prep filter (window, skips, log): `python3 /workspace/meeting-prep/prep_filter.py events.json` (prints nothing = nothing to prep)
- (2026-11-05, Insurance info · Meeting Prep) Meeting one-pager build / finalize: `python3 /workspace/meeting-prep/build_sheet.py content.json STEM --status draft` or `--finalize X.html --event-id ID` (B&W template in /workspace/meeting-prep/template/)
- (2026-11-05, Insurance info · Meeting Prep) Wiki sync compare: `python3 /home/box/dair-wikis/company-product-manuals/tools/sync_compare.py listing.json` or `--already-synced-today` (exit 3 = already ran)

- (2026-11-06, Connor) Scriptify pass: new no-AI helpers — `python3 /workspace/common/routine_gate.py --days …` (exit 10=skip); `python3 /workspace/common/morning_parts.py`; `python3 /workspace/muni-golf/check.py`; `python3 /workspace/bot-audit/x_tips_dedupe.py check|append FILE`; `python3 /workspace/email-purger/scripts/group_messages.py FILE.json`. Report + skill drafts: `/workspace/scriptify/REPORT.md`, `/workspace/scriptify/skills/`. Tests: `/workspace/scriptify/run_tests.sh`.
- (2026-11-06, Dan) Gemini free tier: `/workspace/gemini/gemini_summary.py "instructions" file1 file2` (or pipe text in) sends material to Gemini and prints its summary. Uses GEMINI_API_KEY with model gemini-3.5-flash and falls back on busy errors. Google Search grounding returns a quota error on the free tier, so pass sources in yourself. Without sources Gemini answers from memory and can be wrong. Free-tier content may be used by Google, so leave client details out.
