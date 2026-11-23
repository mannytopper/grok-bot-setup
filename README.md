# Grok Bot setup snapshot

Private snapshot of Manny Topper's Grok Bot fleet: bot profiles, reusable skills, routine prompts and schedules, and shared standing rules.

**Exported:** November 20, 2026 (America/New_York); updated November 20, 2026, 1 PM ET  
**Source:** on-disk files from the shared Grok Bot box (`/home/box/agent-data` and `/workspace`)  
**Repository:** private

This is a point-in-time copy. It is not a live sync, and it does not restore bots by itself.

## Contents

| Path | What is in it |
|---|---|
| `bots/` | One folder per bot, with `profile.json` and `settings.json` (and any other plain config found) |
| `skills/` | Every skill from the workflows library (`SKILL.md` plus helper files) |
| `routines/` | Routine prompts, the Nov 12, 2026 inventory/schedule table, context notes, handoff prompts, and retired prompts |
| `shared/` | Shared standing rules: `INDEX.md`, Connor's `BRIEF.md`, and the other current shared-brain documents |

## Bots (15)

These are the bot folders present on disk at export time. Titles come from each bot's profile (`Name · Title` when the title field was empty).

| Name | Title | Description | Folder |
|---|---|---|---|
| Alfred | Bot Chief Advisor | Builds, manages, and evolves the right Grok Bot organization as the company changes. | `alfred-bot-chief-advisor` |
| Murray | Family and Home | Manny's Family and Home bot. | `murray-family-and-home` |
| Ultimate Privacy Scrub | — | Finds your name, address, and phone on people-search sites, files the opt-outs, and rechecks them every 3 months to keep them down. | `ultimate-privacy-scrub` |
| Dan - Gen Research/Domain Work | — | Performs deep, verifiable research on user-specified topics, citing all sources, and flagging unverifiable or biased information. | `dan-gen-research-domain-work` |
| Dreamer | Bot Team Optomizer | Reviews your bot team's work every night, turns repeated fixes and lessons into reusable skills and memories, and proposes ongoing goals for each bot, so your team gets better over time. | `dreamer-bot-team-optomizer` |
| Parsha | Weekly Teen Parsha PDF | Makes Manny a one-page weekly parsha PDF aimed at 13–18 year olds. | `parsha-weekly-teen-parsha-pdf` |
| Forge-New Bot Builder | — | Forge designs a new Grok Bot for any job you describe: a complete, ready-to-run spec in minutes, then creates the bot once you say yes. | `forge-new-bot-builder` |
| Email Purger | — | Reviews Manny's inbox, groups newsletters, promotions, stale threads, and other unneeded mail by type, and prepares delete, archive, and unsubscribe actions. | `email-purger` |
| Animator-Video Creator | — | A personal motion graphic designer. | `animator-video-creator` |
| Routines | — | Routines houses and runs every routine for Manny Topper's bots (except Usage Guard and Volt - Usage Audit, which are never touched; never create a Volt schedule). | `routines` |
| Insurance info | Meeting Prep | Manny's insurance and office operations bot at Wealcatch Insurance. | `insurance-info-meeting-prep` |
| Spackler - Golf Practice | — | Manny's golf practice coach. Builds his weekly home practice plans for Sunday, Monday and Wednesday after 8 PM (Garmin R50, bump turn board, divot board), all grayscale and in full sentences. Refreshes his Arccos Dashboard Page every Friday and writes the key stats to /workspace/golf/practice-state.md. The current plan is /workspace/golf/practice-plan-v2.pdf, with a copy in C:\Users\Manny\Documents\Golf Practice on his laptop. The Arccos Dashboard Page opens from his desktop shortcut "Arccos Dashboard". | `spackler-golf-practice` |
| 🛍️ SHOPPING AGENT: BEST PRICE COUPONS DISCOUNT CODES | — | Finds the lowest verified total price for anything you want to buy, tests coupon codes, and shows every discount and how it applies. | `shopping-agent-best-price-coupons-discount-codes` |
| Connor | Executive Assistant | Executive Assistant to Manny Topper. | `connor-executive-assistant` |
| Volt - Usage Audit | — | Volt watches Manny Topper’s Grok Bot plan usage and routines. | `volt-usage-audit` |

Usage Guard, Call List Remover, Bot Optomizer, and other retired bots are documented in `shared/bots.md` but no longer have profile files on disk, so they are not under `bots/`. Animator-Video Creator is included because its profile is on disk.

## Skills (63)

Names and descriptions are taken from each skill's YAML frontmatter.

| Skill | Description | Folder |
|---|---|---|
| Academy standing-rules gap | Use when checking, read-only, whether each bot's actual behavior follows the user's standing rules (shared brain rules plus each bot's own profile), and listing gaps with evidence and proposed fixes. | `academy-standing-rules-gap` |
| aeo-geo-site | use this when building or updating a website for SEO plus AEO/GEO (AI assistants, ChatGPT, Copilot, Gemini) so pages are machine-readable, intent-clear, and citable | `aeo-geo-site` |
| ai-citation-sources | use this when AI answers (ChatGPT, Copilot, Gemini, Perplexity, AI Overviews) cite third-party pages instead of your site for prompts you care about, and you need to list those sources and pick a draft-only action for each one | `ai-citation-sources` |
| ai-search-gap-loop | use this when you want a site to show up more in Google and in AI answers (ChatGPT, Copilot, Gemini, Perplexity, AI Overviews) and need a repeatable loop: map buyer decisions to queries and prompts, measure both channels, diagnose each lost prompt, make one change, rerun, and log the result | `ai-search-gap-loop` |
| Auditing a bot at 30 days | Use monthly, or when a bot seems lazy, noisy, or ignored, to decide from run history whether each of its routines should stay, be rewritten, or be cut. Report only; changes nothing. | `auditing-a-bot-at-30-days` |
| blues-recap-pdf | Use when building the graphical St. Louis Blues game-recap PDF, or attaching it to the morning rundown after a Blues game. | `blues-recap-pdf` |
| calendar-one-way-sync | Use when copying events one way from one calendar to another (for example Outlook to Google, or personal calendars into a shared family calendar) on a schedule, with change tracking so only real changes are written. | `calendar-one-way-sync` |
| calendar-tidy-check | Use when checking the user's upcoming calendar for clashes, unanswered or tentative invites and placeholder events, including the heads-up section of the morning rundown. | `calendar-tidy-check` |
| chatgpt-images-browser-playbook | Needs Grok Bot or a browser agent. Use when generating stills on chatgpt.com with a signed-in browser session. Images UI only, one still per dispatch, no API keys, no cookie scraping, no sleep-poll loops. Session-only; hand the box to the owner for login/2FA. | `chatgpt-images-browser-playbook` |
| Checking live status before review | Use right before sending a person any item for review, approval, or a decision (a PR, issue, draft, deploy, or approval request), so the ask reflects the item's live state and not stale memory. | `checking-live-status-before-review` |
| coach | Use this when a draft needs a structural read before line-edit: thesis, arc, and teach test first, style second. | `coach` |
| conducting-deep-research | Conducts source-backed, goal-directed research that combines a scholarly evidence review with an institution, company, or funding map. Use when a request needs both an evidence review and an organization or funding map. Not for quick lookups or general research write-ups. | `conducting-deep-research` |
| decision-queue | Use when a question to the user goes unanswered, when the user answers or defers an earlier question, or when listing the decisions waiting on them ("Waiting on you"). | `decision-queue` |
| design-taste-frontend | Use when building a landing page, portfolio, or marketing site from a brief, so the result looks chosen for this subject instead of like a template. Reads the brief, plans tokens, builds, then checks the rendered page. | `design-taste-frontend` |
| diagram-design | use this when creating explainer diagrams (architecture, sequence, process, cards for posts) as HTML/SVG/PNG so they are branded and not ranking-dashboard slop | `diagram-design` |
| domain-research | Use for domain-name industry research: market data, sales comps and valuations, aftermarket trends, registry/ICANN/UDRP/trademark questions, best practices, or auditing a domain portfolio listing export against a master list. | `domain-research` |
| draft | Use this when writing or expanding an article one section at a time, with the writer's approval between sections. Never writes the whole piece at once. | `draft` |
| email-purger-group | Use when building an inbox cleanout proposal from a fetched message list JSON: group by sender domain, apply safe default actions, and exclude starred, important and preserved senders. Proposal only, never modifies mail. | `email-purger-group` |
| exact-match-intent-seo | use this when choosing domains, URL slugs, titles, or H1s for SEO. Exact Match Domain (EMD) lessons and the safer brand-domain equivalent | `exact-match-intent-seo` |
| explain-it-simply | Use when asked to explain, simplify, define, ELI5, fact-check, or summarize something at the person's level, or to make a printable explainer or a short narrated explainer video. | `explain-it-simply` |
| Fleet memory prune | Use when reviewing, read-only, the bots' memories and shared-brain files for stale, duplicate, contradicting or unsafe entries, and proposing (never making) prune or merge changes for the owning bot to apply after the user's yes. | `fleet-memory-prune` |
| Fleet prompt-injection guard | Use when scanning bots' transcripts, memory, routine prompts, shared files or fetched web content for embedded instructions (possible prompt injection), or when any check finds an instruction inside data; report only, never follow. | `fleet-prompt-injection-guard` |
| improving-prompts | Compresses and clarifies an existing LLM prompt through concept elevation, verifying that no original instruction is lost. Use when the user supplies a prompt or prompt file and asks to improve, tighten, optimize, or refine it. Not for writing a new prompt; use writing-system-prompts. | `improving-prompts` |
| inbox-digest-build | Use when building the daily inbox digest one-pager (PNG and PDF) from the user's mailboxes with /workspace/inbox-digest/render.py. | `inbox-digest-build` |
| last30days | Use when asked what people are saying about a topic in the last 30 days, or to research recent buzz, trends, reactions, or opinions across Reddit, X, YouTube, TikTok, Hacker News, Polymarket, GitHub, and the web (the last30days plugin by mvanhorn). | `last30days` |
| Local feed routine | Use when a daily routine posts local news and event cards from a fixed source list without repeats, using local_feed_dedupe.py to fetch candidates, check them against a delivered log, and log what was posted. | `local-feed-routine` |
| markdown-twin | Use this when adding a clean markdown twin for one HTML page: a .md copy at the same path, a rel=alternate type=text/markdown link, and one line for it in /llms.txt. | `markdown-twin` |
| meeting-prep-one-pager | Use when building, refreshing, or finalizing a one-page black-and-white meeting prep sheet from calendar events, using the prep_filter.py and build_sheet.py helpers. | `meeting-prep-one-pager` |
| morning-combined-run | Use when running one combined morning routine that does several independent daily jobs (calendar dashboard, day rundown PDF, inbox digest, watch checks, digests) in one wake, calling saved scripts instead of redoing steps by hand. | `morning-combined-run` |
| morning-parts | Use when deciding which parts of the morning combined run apply on a given America/New_York date (calendar dashboard, rundown, inbox digest, Tesla watch, domain digest, Mon/Wed/Fri X watch), before calling those scripts. | `morning-parts` |
| motion-picker | use this when choosing one animation library for a page, a diagram, or a short clip, and when applying the calm, snappy, or playful timing numbers. Keeps motion to one moment, names the license, and honors reduced motion | `motion-picker` |
| muni-golf-watch | Use when checking whether the Muni Golf iPad app is publicly released (App Store search plus munigolfsim.com), including a watch routine. | `muni-golf-watch` |
| no-ai-slop | Load first for any text that will be published (X posts and replies, Reddit comments, LinkedIn, ads, site, PRs). Edits out AI-writing tells with the smallest change that works, or flags them without rewriting. Matches the writer's own published voice, never adds facts, and checks every number, name, and negation survived the edit. | `no-ai-slop` |
| outline | Use this when turning a seed, interview, or set of facts into a writing plan before drafting an article. | `outline` |
| Price watch routine | Use when a scheduled routine checks watched product listings against price targets with a helper script (price_watch.py plus a JSON state file), falling back to WebFetch when a page is blocked, and alerts only when something newly qualifies. | `price-watch-routine` |
| Process TransactNOW Payment Claims | Use when emailing unread Payment claims from Vertafore TransactNOW Claims and deleting them after send. | `process-transactnow-payment-claims` |
| redesign-existing-projects | Use when improving the design of a site or app that already exists. Audits the live pages, ranks the problems by impact, and fixes them in small reviewable steps on the current stack without breaking features. | `redesign-existing-projects` |
| route-to-the-right-bot | Use whenever Manny asks or passes along something in any bot's chat, to decide which of his bots owns it and hand it there so the work is done and kept in that bot's chat. | `route-to-the-right-bot` |
| routine-gate | Use when a scheduled routine needs a single yes/no on whether to run today (weekday allow-list plus Shabbat / Yom Tov), before any fetch, send, or browser work. | `routine-gate` |
| Routine healthcheck | Use when running a read-only check of every bot's routines for token waste, failures, duplicates and runs that break the user's rules, using only server-side routine status, and ranking proposed fixes. | `routine-healthcheck` |
| Running efficient recurring work | Use when building, running, or auditing any recurring routine or multi-step workstream (monitors, digests, briefs, audits), to cut wasted reads, repeated checks, and restarts while keeping quality. | `running-efficient-recurring-work` |
| Running founder office hours | When a founder or CEO brings a product idea, strategic bet, pricing, focus, hiring, fundraising or kill decision and wants a hard-nosed startup-advisor pressure test (adapted from YC-style office hours in garrytan/gstack). | `running-founder-office-hours` |
| Running unattended routines and triggers | Use when creating or editing a scheduled routine or event trigger that runs while nobody is watching, so it never stalls on an approval, never fires on noise, and is tested before it is trusted. | `running-unattended-routines-and-triggers` |
| Saving a job as a skill | Use after running a job cleanly by hand, when turning it into a reusable skill, or when reviewing an existing skill that keeps producing inconsistent results. | `saving-a-job-as-a-skill` |
| shabbat-gate | Use at the start of any routine, reminder or scheduled job in any of the user's bots, to decide whether it may run or message the user, because nothing runs or reaches him on Shabbat or Yom Tov. | `shabbat-gate` |
| ship-post | Use when something just shipped (a merged PR, a release, a deploy, a week of commits) and you want one build-in-public post for X, plus a Reddit draft if asked. Starts from the git history, asks the owner one question, picks the one change a user would notice, and allows no number the commits or the owner can't back. Drafts only. | `ship-post` |
| show-me | use this when opening or rewriting a pull request description, or when the user needs a visual explanation of code shape, flow, or structure. Keep PR bodies easy to scan with the smallest clear diagram | `show-me` |
| social-copywriting | Use this when writing or adapting copy for X or LinkedIn so it matches the platform instead of sounding like a press release. | `social-copywriting` |
| source-check | Use this after drafting an article, before publish, to verify every factual claim and statistic against a named source. | `source-check` |
| storytelling-hooks | Use this when writing a storytelling hook for a post. You get a hook in your own words, with every blank filled by a real fact. Do not copy another writer's hooks. | `storytelling-hooks` |
| top-edit | Use this as the last mechanical pass before publishing, to screen AI tells and house-style misses that a slop word-list can skip. | `top-edit` |
| Transcript healthcheck | Use when running a read-only check of the bots' recent transcripts for friction (errors, retries, loops, user corrections, stalled or abandoned tasks) and rating each bot green, yellow or red with evidence. | `transcript-healthcheck` |
| Verified deep research | Use when asked to research a topic, compare options, answer a question that needs sourced, verifiable evidence, or write a deep research report (optionally including what practitioners say on X), with bias flagged, unsourced reasoning labeled, and a confidence level on each finding. | `verified-deep-research` |
| vertafore-download-detail-mt | Use when running, exporting, cleaning and emailing the AMS360 "Download Detail Modified MT" report from Vertafore, or answering questions about its date range or filters. | `vertafore-download-detail-mt` |
| vertafore-renewals-policy-expiration | Use when pulling the AMS360 renewals-due list: run the Vertafore "Policy Expiration" report, clean it into a 30-day / 31-60-day workbook, and deliver it. | `vertafore-renewals-policy-expiration` |
| Weekly parsha sheet build | Use when building the one-page weekly parsha PDF for teens from a per-week content file, then saving it to the user's computer and printing it. | `weekly-parsha-sheet-build` |
| whetstone-signal | Use this when ad campaigns that let the platform pick the audience (Meta Advantage+, Google Performance Max, Google Demand Gen, or similar) bring plenty of cheap leads, signups, or clicks that rarely turn into revenue. Helps you choose the conversion event the algorithm should chase, score and send back higher quality conversions, and check the results against your own backend numbers. Also use it when setting up a new automated campaign and deciding what to optimize for. | `whetstone-signal` |
| wiki-sync-from-shared-drive | Use when syncing a wiki's raw/ mirror from a folder on the user's computer (new, changed or removed files), using sync_compare.py. | `wiki-sync-from-shared-drive` |
| write-like-manny | Use when drafting any email, reply, Slack, text, or other message that will go out in Manny Topper's name, so it sounds like him (work at Wealcatch or personal). | `write-like-manny` |
| writing-prose | Writes and edits prose for people in a plain, conversational, short house style with no em dashes. Use when drafting or revising documentation, READMEs, explanations, blog posts, or other human-facing prose. Not for prompts written for agents; use writing-system-prompts or composing-agent-prompts. | `writing-prose` |
| x-article | Use this when writing or rewriting an X Article (long-form on x.com/i/article), with images between sections, a first-line hook, and no invented numbers. | `x-article` |
| x-tips-dedupe | Use when a weekly X-tips routine has candidate post URLs and must drop ones already in the seen log before messaging, or append newly reported ones. | `x-tips-dedupe` |
| x-watch-deck-build | Use when running a periodic X (Twitter) watch for posts about a topic and turning new finds into a PowerPoint deck plus an email summary, skipping anything already reported. | `x-watch-deck-build` |
| youtube-summary-one-pager | Use when someone sends a YouTube link and wants it summarized, in chat and/or as a graphical one-page PDF/PNG summary. | `youtube-summary-one-pager` |

## Routines (32 current prompts)

Current prompt files live in `routines/prompts/`. Supporting parts for the morning combined run are in `routines/prompts/morning-parts/`. Schedules, owners, and move notes from the November 12, 2026 inventory are in `routines/inventory.md`. Context write-ups and handoff prompt copies are in `routines/context/` and `routines/handoff/`.

| Routine | Summary | File |
|---|---|---|
| ams weekday reminder | Moved from Connor to Routines on Nov 16, 2026 (Manny said yes). | `routines/prompts/ams-weekday-reminder.md` |
| answer emailed insurance questions | Moved to Routines from Insurance info · Meeting Prep on Nov 12, 2026. | `routines/prompts/answer-emailed-insurance-questions.md` |
| Arccos Dashboard Friday refresh (requested by Manny via Spackler, Nov 20, 2026: "refresh every friday") | 1. | `routines/prompts/arccos-dashboard-friday-refresh.md` |
| biweekly work outlook cleanout | Moved to Routines from Email Purger on Nov 12, 2026. | `routines/prompts/biweekly-work-outlook-cleanout.md` |
| carrier bulletin and rate-change digest | Created by Routines on Nov 20, 2026 (Manny picked idea 4 from the weekly routine ideas). | `routines/prompts/carrier-bulletin-digest.md` |
| Erev Shabbos and Yom Tov prep card | Created by Routines on Nov 20, 2026 (Manny picked idea 3 from the weekly routine ideas). | `routines/prompts/erev-shabbos-prep-card.md` |
| golf practice evening reminder | SKIP WINDOW (added Nov 17, 2026 at Manny's request "Pause golf practice this week", relayed by Connor): if today's America/New_York date is from 2026-11-17 through 2026-11-21,… | `routines/prompts/golf-practice-evening-reminder.md` |
| griots interior cleaner checkin | Moved from Connor to Routines on Nov 16, 2026 (Manny said yes). | `routines/prompts/griots-interior-cleaner-checkin.md` |
| grokbot dashboard refresh | Moved to Routines from Alfred · Bot Chief Advisor on Nov 12, 2026. | `routines/prompts/grokbot-dashboard-refresh.md` |
| meeting prep docs 2 to 4 hours before each meeti | Moved to Routines from Insurance info · Meeting Prep on Nov 12, 2026. | `routines/prompts/meeting-prep-docs-2-to-4-hours-before-each-meeti.md` |
| monday waiting on you list | Moved from Connor to Routines on Nov 16, 2026 (Manny said yes). | `routines/prompts/monday-waiting-on-you-list.md` |
| monthly bot portfolio strategy review | Moved to Routines from Alfred · Bot Chief Advisor on Nov 12, 2026. | `routines/prompts/monthly-bot-portfolio-strategy-review.md` |
| monthly gmail cleanout | First-Monday check (added Nov 13, 2026): run `date +%u` and `date +%d` (America/New_York). | `routines/prompts/monthly-gmail-cleanout.md` |
| morning combined run | Moved from Connor to Routines on Nov 16, 2026 (Manny said yes). | `routines/prompts/morning-combined-run.md` |
| muni golf ipad app watch | Moved to Routines from Spackler - Golf Practice on Nov 12, 2026. | `routines/prompts/muni-golf-ipad-app-watch.md` |
| open office follow ups watch | Moved to Routines from Insurance info · Meeting Prep on Nov 12, 2026. | `routines/prompts/open-office-follow-ups-watch.md` |
| order concierge sweep | Moved to Routines from Murray · Family and Home on Nov 12, 2026. | `routines/prompts/order-concierge-sweep.md` |
| overdue work email nudge | Created by Routines on Nov 13, 2026 (Manny picked idea 1 from the weekly routine ideas). | `routines/prompts/overdue-work-email-nudge.md` |
| parsha trailer handoff | Parsha trailer handoff (created Nov 20, 2026 in Routines at Animator-Video Creator's request, relayed as Manny's ask). | `routines/prompts/parsha-trailer-handoff.md` |
| quarterly company ai operating model review | Moved to Routines from Alfred · Bot Chief Advisor on Nov 12, 2026. | `routines/prompts/quarterly-company-ai-operating-model-review.md` |
| quarterly people search recheck | Moved to Routines from Privacy Scrubber on Nov 13, 2026 (Manny asked Privacy Scrubber to move it). | `routines/prompts/quarterly-people-search-recheck.md` |
| resume golf practice reminder | Moved to Routines from Spackler - Golf Practice on Nov 12, 2026. | `routines/prompts/resume-golf-practice-reminder.md` |
| shared calendar sync | Moved from Connor to Routines on Nov 16, 2026 (Manny said yes). | `routines/prompts/shared-calendar-sync.md` |
| sunday family week ahead | Created by Routines on Nov 13, 2026 (Manny picked idea 3 from the weekly routine ideas). | `routines/prompts/sunday-family-week-ahead.md` |
| weekday local feed | Moved to Routines from Murray · Family and Home on Nov 12, 2026. | `routines/prompts/weekday-local-feed.md` |
| weekly company grok bot improvement review | Moved to Routines from Alfred · Bot Chief Advisor on Nov 12, 2026. | `routines/prompts/weekly-company-grok-bot-improvement-review.md` |
| weekly grok bot setup review | Moved from Connor to Routines on Nov 16, 2026 (Manny said yes). | `routines/prompts/weekly-grok-bot-setup-review.md` |
| weekly practice plan tune-up | Created by Routines on Nov 20, 2026 (Manny picked idea 5 from the weekly routine ideas). | `routines/prompts/weekly-practice-plan-tune-up.md` |
| weekly renewals due list | Created by Routines on Nov 13, 2026 (Manny picked idea 2; he chose 30 and 60 day windows, not 90). | `routines/prompts/weekly-renewals-due-list.md` |
| weekly usage leak check | Requested by Manny in Volt's chat, Nov 16, 2026 (relayed by Volt). | `routines/prompts/weekly-usage-leak-check.md` |
| wiki sync on login company forms rates | Moved to Routines from Insurance info · Meeting Prep on Nov 12, 2026. | `routines/prompts/wiki-sync-on-login-company-forms-rates.md` |
| Yearly Do Not Call registry check | Requested by Manny via Alfred (Manny's yes in Alfred's chat, Nov 13, 2026: "yes to all three merge steps"). | `routines/prompts/yearly-do-not-call-check.md` |

### Retired routine prompts

- `bestgloal-email-price-watch.md`
- `family-price-watches.md`
- `gliston-email-price-watch.md`

## What was left out on purpose

- Chat transcripts, memories, and agent `store.db` databases
- Avatars, attachments, browser data, cookies, and caches
- Credentials, vault contents, tokens, `.env` files, and GitHub auth config (`~/.config/gh`)
- Host-level secret and cookie files under agent-data
- Any single file larger than 5 MB
- Routine backup copies, wiki-sync email/export files, and X-tips candidate logs
- Workspace working files (PDFs, run artifacts, prior export zips) that are not bot, skill, or routine definitions

## Redaction

Before this snapshot was committed, copies were scanned and sensitive values were replaced with `[REDACTED]`. Manny's own addresses and company or bot-inbox addresses were kept. Personal phone numbers, home addresses, and other personal email addresses were removed.

Redactions applied in this export:

- personal email: 26

## Counts

- Bots: 15
- Skills: 63
- Current routine prompt files: 32
- Files copied into this repository: 218
