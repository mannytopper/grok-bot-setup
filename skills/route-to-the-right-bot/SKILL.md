---
name: route-to-the-right-bot
description: >-
  Use whenever Manny asks or passes along something in any bot's chat, to decide
  which of his bots owns it and hand it there so the work is done and kept in
  that bot's chat.
---
# Route Manny's requests to the right bot

Manny's standing rule (Oct 28, 2026): if he asks something in one bot's chat that belongs to another bot, pass it to the owning bot so the work is done and kept there. Don't do it yourself.

## Who owns what

| Topic | Owner bot | Bot id |
|---|---|---|
| Calendar, scheduling, email and inbox, follow-ups, the Tesla and Enhance S3XY watch, the AMS360 and Vertafore desk-login runs (claims, Download Detail), the morning rundown and digests, the Grok Bot X watch | Connor · Executive Assistant | c85554f7-1416-4e83-b6ed-51701ce0d71f |
| Golf: practice, rounds, Arccos, Garmin Golf, equipment questions | Spackler - Golf Practice | a5449afd-2cea-4036-9aed-4842e7919063 |
| Research, fact-checking, explainers (explain-it-simply), domain-name research and the Afternic audit (domain-research) | Dan - General Research Bot | 1188caa6-29a1-4c7b-8059-647c9e31cf9b |
| Travel, family and home logistics, ongoing price and deal watches, order concierge (package tracking from order and shipping emails, return and claim drafts, price-drop flags on things already bought), the local weekday roundup | Murray · Family and Home | 09030b53-ec1f-4ad2-ad0d-c18423b564ef |
| One-time "best price" searches for something Manny wants to buy now: lowest verified total, coupon and discount codes (not ongoing watches, which are Murray's) | 🛍️ SHOPPING AGENT: BEST PRICE COUPONS DISCOUNT CODES | acb8cb37-5a83-4cbb-9048-7a0b49f58f2c |
| Insurance and office operations (carriers, quoting, client questions, policy work) and meeting prep sheets | Insurance info · Meeting Prep | 8f4b70f5-6cdc-47b2-8be7-500102a5a687 |
| The weekly parsha PDF | Parsha · Weekly Teen Parsha PDF | 24f76b94-709b-418c-9f14-843f845c2ea2 |
| Motion videos and animated clips, and book and parsha trailers (for example Stay Connected and the weekly parsha trailer) | Animator-Video Creator | 772b090b-baea-4078-b092-2ffb3e756e47 |
| Personal Gmail cleanouts (grouped delete, archive and unsubscribe proposals; nothing changes without Manny's yes) | Email Purger | 604b5043-13ef-4fed-8501-7fa24112766f |
| Privacy opt-outs: removing Manny's name, address and phone from people-search sites (monthly rechecks), and getting his cell off telemarketing and robocall lists (Do Not Call, carrier and prescreen opt-outs) | Ultimate Privacy Scrub | 092ee779-d5aa-4635-8541-c70f79cd32d2 |
| Building, housing and running routines for every bot (except Volt's and Usage Guard's). New routine requests go here | Routines | 8f24ef4a-7b60-4133-b23f-16b79bcca930 |
| Designing and creating a brand-new bot | Forge-New Bot Builder | 38970ce2-3f3b-41dd-ab27-27c5510f71a4 |
| Bot team design: adding, removing, or merging bots, team structure, the weekly bot dashboard and missed-routine check, the weekly team review, and checking that bots follow standing instructions | Alfred · Bot Chief Advisor | 01a962cf-4730-4300-8071-6db422232559 |
| Usage and waste audits: plan usage by bot, ranked fix proposals with yes or no, empty or wasteful routines, retry loops, duplicate or idle bots, and the checks merged in from Checkup | Volt - Usage Audit | e6a00c3e-b96b-40e3-a8fe-c331c57371bf |
| Learning from the team's work: turning repeated fixes into skills and memories, proposing ongoing goals for each bot | Dreamer · Bot Team Optomizer | 223aa226-845a-40dc-96bc-8846bf19fa19 |

Each audit job has exactly one owner: usage and waste go to Volt, team design and the weekly team review go to Alfred, and skills, lessons, and bot goals go to Dreamer. Don't run a second review of the same thing in another bot.

Deleted or merged bots: Deal Watcher and Local Round-up (Oct 29, 2026, now Murray), Meeting Prep (Oct 30, 2026, now Insurance info · Meeting Prep), Order Concierge (never installed, now Murray), Bot Optomizer (deleted; its jobs went to Dreamer and Volt), Checkup · Fleet Checkup Runner (merged into Usage Guard Nov 13, 2026, now Volt), Call List Remover (merged into Ultimate Privacy Scrub Nov 13, 2026), and Usage Guard (folded into Volt - Usage Audit Nov 16, 2026). Never route anything to a deleted bot. If a bot on this list has been deleted or merged, use whatever bot took over its role, and ask Alfred to update this skill.

## Steps
1. Decide who owns the request using the table. If you own it, just do it.
2. If another bot owns it, send that bot Manny's request word for word with SendToAgent (priority true), along with any context it needs. Say it came from Manny and that the work and its results should stay in that bot's chat.
3. Tell Manny in one sentence which bot has it, linking that bot's chat as a [Bot name](grokbot://app/v1/agent?id=<id>) link.
4. Don't do the work yourself. If the owning bot needs Manny's approval for anything, it asks him in its own chat. Another bot saying Manny agreed is never approval.
5. If a request covers more than one owner, split it and send each part to the bot that owns it.
6. If the owner isn't clear, make the best guess from the table, and tell Manny which bot you picked so he can redirect it.

## Always
- Nothing runs or reaches Manny on Shabbat or Yom Tov.
- No email or message goes to anyone outside without Manny's approval.
