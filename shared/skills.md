# Skills index (updated 2026-11-05, Connor)

User skills live in /home/box/agent-data/workflows/<name>/SKILL.md and every bot can load them with the Skill tool. Bodies are not copied here.

- **blues-recap-pdf**: Use when building the graphical St. Louis Blues game-recap PDF, or attaching it to the morning rundown after a Blues game.
- **calendar-one-way-sync**: Use when copying events one way from one calendar to another (for example Outlook to Google, or personal calendars into a shared family calendar) on a schedule, with change tracking so only real changes are written.
- **calendar-tidy-check**: Use when checking the user's upcoming calendar for clashes, unanswered or tentative invites and placeholder events, including the heads-up section of the morning rundown.
- **decision-queue**: Use when a question to the user goes unanswered, when the user answers or defers an earlier question, or when listing the decisions waiting on them ("Waiting on you").
- **domain-research**: Use for domain-name industry research: market data, sales comps and valuations, aftermarket trends, registry/ICANN/UDRP/trademark questions, best practices, or auditing a domain portfolio listing export against a master list.
- **explain-it-simply**: Use when asked to explain, simplify, define, ELI5, fact-check, or summarize something at the person's level, or to make a printable explainer or a short narrated explainer video.
- **inbox-digest-build**: Use when building the daily inbox digest one-pager (PNG and PDF) from the user's mailboxes with /workspace/inbox-digest/render.py.
- **last30days**: Use when asked what people are saying about a topic in the last 30 days, or to research recent buzz, trends, reactions, or opinions across Reddit, X, YouTube, TikTok, Hacker News, Polymarket, GitHub, and the web (the last30days plugin by mvanhorn).
- **local-feed-routine**: Use when a daily routine posts local news and event cards from a fixed source list without repeats, using local_feed_dedupe.py to fetch candidates, check them against a delivered log, and log what was posted.
- **meeting-prep-one-pager**: Use when building, refreshing, or finalizing a one-page black-and-white meeting prep sheet from calendar events, using the prep_filter.py and build_sheet.py helpers.
- **morning-combined-run**: Use when running one combined morning routine that does several independent daily jobs (calendar dashboard, day rundown PDF, inbox digest, watch checks, digests) in one wake, calling saved scripts instead of redoing steps by hand.
- **price-watch-routine**: Use when a scheduled routine checks watched product listings against price targets with a helper script (price_watch.py plus a JSON state file), falling back to WebFetch when a page is blocked, and alerts only when something newly qualifies.
- **process-transactnow-payment-claims**: Use when emailing unread Payment claims from Vertafore TransactNOW Claims and deleting them after send.
- **route-to-the-right-bot**: Use whenever Manny asks or passes along something in any bot's chat, to decide which of his bots owns it and hand it there so the work is done and kept in that bot's chat.
- **verified-deep-research**: Use when asked to research a topic, compare options, answer a question that needs sourced, verifiable evidence, or write a deep research report (optionally including what practitioners say on X), with bias flagged, unsourced reasoning labeled, and a confidence level on each finding.
- **vertafore-download-detail-mt**: Use when running, exporting, cleaning and emailing the AMS360 "Download Detail Modified MT" report from Vertafore, or answering questions about its date range or filters.
- **weekly-parsha-sheet-build**: Use when building the one-page weekly parsha PDF for teens from a per-week content file, then saving it to the user's computer and printing it.
- **wiki-sync-from-shared-drive**: Use when syncing a wiki's raw/ mirror from a folder on the user's computer (new, changed or removed files), using sync_compare.py.
- **write-like-manny**: Use when drafting any email, reply, Slack, text, or other message that will go out in Manny Topper's name, so it sounds like him (work at Wealcatch or personal).
- **x-watch-deck-build**: Use when running a periodic X (Twitter) watch for posts about a topic and turning new finds into a PowerPoint deck plus an email summary, skipping anything already reported.
- **transcript-healthcheck** (2026-11-13, Dreamer): Read-only check of bots' recent transcripts for friction; green/yellow/red per bot with evidence; saves to /workspace/checkup/.
- **routine-healthcheck** (2026-11-13, Dreamer): Read-only check of routines for waste, failures, duplicates and rule breaks, from server-side status only; ranked proposals; saves to /workspace/checkup/.
- **academy-standing-rules-gap** (2026-11-13, Dreamer): Read-only comparison of each bot's behavior against the shared rules and its profile; saves to /workspace/checkup/.
- **fleet-prompt-injection-guard** (2026-11-13, Dreamer): Read-only scan for instructions hidden in data, and whether any bot acted on one; report only.
- **fleet-memory-prune** (2026-11-13, Dreamer): Read-only review of memories and shared files for stale, duplicate, contradicting or unsafe entries; proposals only.
