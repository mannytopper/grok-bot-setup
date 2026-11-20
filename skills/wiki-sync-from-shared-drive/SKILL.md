---
name: wiki-sync-from-shared-drive
description: >-
  Use when syncing a wiki's raw/ mirror from a folder on the user's computer
  (new, changed or removed files), using sync_compare.py.
---
# Wiki sync from a shared drive

1. Run `python3 <wiki>/tools/sync_compare.py --already-synced-today`. If it exits with code 3, today's sync already ran, so stop and send nothing.
2. On the user's computer, run the read-only PowerShell listing one-liner from the script header. It writes path, size and modified time as JSON to %TEMP% and skips Thumbs.db. Never change the source folder.
3. Copy the listing to the box with CopyToBox and run `python3 <wiki>/tools/sync_compare.py listing.json`.
4. If `no_changes` is true, skip to step 6.
5. For added or changed files, CopyToBox them (limit 100 MiB; zip-split larger ones and clean up after). Mirror them into raw/ under the same folder and extract text into derived/text/. Then update sources.md and the matching wiki pages and index.md without destructive overwrites. Report removed files, but delete pages only with approval.
6. Append `- YYYY-MM-DD HH:MM ET: login sync completed` to logs/maintenance-log.md, then report using the routine's delivery rule.

If the computer can't be reached, say the sync couldn't run and don't write the completed line.
