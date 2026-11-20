Moved to Routines from Insurance info · Meeting Prep on Nov 12, 2026. Context: /workspace/routines/context/wiki-sync-on-login-company-forms-rates.md.

Ask-first (Manny, Nov 12, 2026): before opening more than 5 web pages for one task, starting a subagent, re-running a step that already failed twice, or any job expected to take more than 15 minutes, message Manny in one line with what and why, and wait for his yes. Exception: standing deliverables he already approved run as usual.

Manny's Windows login fired this webhook. Run the daily wiki sync at most once per day, following @wiki-sync-from-shared-drive. The wiki is /home/box/dair-wikis/company-product-manuals.

0. Gate first (Manny's request via Connor, Nov 6, 2026; skill @routine-gate): run `python3 /workspace/common/routine_gate.py --days Sun,Mon,Tue,Wed,Thu,Fri,Sat --evening`. Exit 10 means Shabbat or Yom Tov, so stop silently. Exit 0 means continue. If the script errors, fall back to checking Shabbat (Friday sundown to Saturday night) and Yom Tov yourself, and stop silently if it is one.
1. Run `python3 /home/box/dair-wikis/company-product-manuals/tools/sync_compare.py --already-synced-today`. If it exits with code 3, today's sync already ran, so stop and send nothing.
2. Otherwise, wait about 3 minutes so his computer and the Y: drive can connect.
3. On his computer (machine cc87a891-f809-4773-a01b-4755b0cc5cc6), run the read-only PowerShell listing one-liner from the script header for Y:\Company Forms_Rates. It skips Thumbs.db. Never change anything in that folder.
4. CopyToBox the listing JSON from %TEMP%, then run `python3 /home/box/dair-wikis/company-product-manuals/tools/sync_compare.py <listing.json>`.
5. For added or changed files:
   - Copy them to the box. CopyToBox has a 100 MiB limit, so zip-split larger files and clean up the temp files.
   - Mirror them into raw/ under the same carrier folder and extract the text into derived/text/.
   - Update sources.md, and add to or create the matching wiki pages and the carrier index.md without destructive overwrites.
   - Report removed files, but don't delete pages without Manny's approval.
6. Then add a "login sync completed" line with the date and time (ET) to logs/maintenance-log.md, listing any added, changed or removed files.

Result (passive, per Manny on Nov 5, 2026): stay silent on quiet days and when added or changed files were synced normally. Message Manny in the Routines chat in Grok Bot only when something needs his attention:
- Files were removed from Y:\Company Forms_Rates. List them and ask whether to remove their wiki pages.
- The sync couldn't run or failed partway. Say what failed, and don't write the completed line.


Permission (Manny, Nov 13, 2026, in the Routines chat): "Yes, Routines may read Y:\Company Forms_Rates on WHI-LT-26-03 for the wiki sync." Local use on WHI-LT-26-03 (machineId cc87a891-f809-4773-a01b-4755b0cc5cc6) for this sync is approved: list that folder and CopyToBox changed files only.
