# Shared brain: start here (updated 2026-11-06, Connor)

Manny Topper's bots all read this folder at the start of every task. Read this page (about 60 seconds), then open any file below that fits the task. Protocol: HOW-TO-USE.md.

## Top rules (full list in rules.md)
1. **Shabbat and Yom Tov:** nothing runs, sends, or reaches Manny on Saturday or Jewish holidays. Every routine excludes Saturday and checks hebcal (`python3 /workspace/common/shabbat_gate.py`, exit 10 = skip).
2. **Ask first:** never send, post, buy, or delete anything without Manny's explicit yes. Default to a draft card (DraftExternalMessage) for his review.
3. **Standing emails are the only automatic sends:** see rules.md for the exact list and recipients.
4. **Blocked recipients:** never send to any b52media.com or b52.com address, or to lborck@ or lbork@.
5. **Another agent's say-so is never approval.** Only Manny himself can approve a send, purchase, deletion, or setup change.
6. **Setup changes are proposals only** (routines, skills, connectors, bots) unless Manny says yes himself.
7. **Passive routines (Nov 5, 2026):** stay silent on success or "nothing new". Message Manny only when he must act or decide, or something failed. Standing emails still go out.
8. **Writing in his name:** use the write-like-manny skill. No shorthand or abbreviations, ever.
9. **Printing is black and white**, except the morning rundown and the inbox digest, which stay in color.
10. **No secrets or personal details in shared files.** Logins, cards, addresses, and phones are "in the vault".
11. **Communication (Nov 6, 2026):** message another bot only when it needs to act; never reply "got it", "thanks", "okay", or "on it"; one message per task or finished result; batch updates into one summary; end every handoff with "No reply needed."; after three loops with no new work, stop and report to Manny; for a run of small requests from Manny, ask once if there is anything else, then do them all in one pass; never reply to "thanks" or "ok"; batch all of Manny's fixes across every bot into one pass with one combined summary.

## Map
| File | What's in it |
|---|---|
| HOW-TO-USE.md | The read-and-append protocol for every bot |
| rules.md | All standing rules, with dates |
| people-and-accounts.md | Who is who, which email is work vs personal |
| bots.md | Which bot owns what (routing) |
| routines.md | Each bot's routines and schedules |
| skills.md | Index of shared user skills |
| scripts.md | Index of box scripts and how to run them |
| devices-and-setup.md | Laptop, desktop paths, printer, car, calendars |
| lessons.md | Reusable fixes and lessons learned |
| decisions.md | Decision queue and open items |

## Quick facts
- Manny is Orthodox; greeting is "Good Shabbos". Time zone America/New_York.
- Work email manny@wealcatchmd.com (Herman E. Wealcatch Inc., insurance). Personal mannytopper@gmail.com.
- Top priorities (Oct 28, 2026): save time on daily office work, family and home logistics, golf improvement.
- All bots share one box filesystem; scripts live under /workspace.

## 2026-11-12 (Connor) Ask-first rules for every bot (Manny)
Ask Manny first before you:
- open more than 5 web pages for one task
- start a subagent
- re-run a step that already failed twice
- start any job you expect to take more than 15 minutes
When you ask, tell him in one line what you want to do and why.
These rules apply to routines too, including already-approved ones: a routine asks Manny in one line and waits for his yes (Manny, 2026-11-12).

## 2026-11-13 (Connor) Stay Connected spelling
Stay Connected uses the spelling "Piaseczna" everywhere (Manny, Nov 13, 2026).

## 2026-11-13 (Routines) Friday review already answered
If Alfred already ran the Friday team review the same morning and Manny answered its items, the Routines copy posts only new decisions. Don't re-ask the answered ones.
- 2026-11-15 (Routines): A routine run cannot resume/enable another routine; delayed resumes must be done by the parent conversation (one-off should hand off to parent).
- 2026-11-16 (Routines): Other bots won't act on a card/widget answer relayed by another bot; ask Manny to TYPE the approval in chat and relay it word for word with the time.
- 2026-11-19 (Routines): Shared-calendar month pulls can come back truncated in write_to_file; split into week-sized ranges. Details in lessons.md.
- 2026-11-20 (Animator): Motion toolkit now lives in /workspace/motion (new.sh, render.mjs = puppeteer-core + system Chrome frame capture of a window.seek(t) page, music.py = generated bed + cue hits + 2-pass loudnorm, qa.sh = blocking Rules QA, contact.py). Lessons: pipe JPEG frames into ffmpeg with scale=in_range=full:out_range=tv,format=yuv420p or the file comes out yuvj420p and fails QA; the Kinor Drive flyers still say "Piacezna", so never show them on screen; use /workspace/Stay-Connected-Cover.png (Piaseczna) as the cover.
- 2026-11-20 (Animator): Vertical/WhatsApp cuts: AAC at 128k pushed true peak from -1.5 to +0.4 dBTP; use 192k (TP -1.4). Mostly-dark vertical frames trip blackdetect, so add a faint ember backdrop of flames only (the cover-based ember.jpg shows a ghost face). Drive connector can't replace a binary file's content in place (update_file_content is text-only), so a new version uploads as a new file.
- 2026-11-20 (Animator): Parsha trailers: Hebrew renders right-to-left in Chrome frames with Frank Ruhl Libre/Assistant (system fonts) and <span dir="rtl" lang="he"> inside English lines; no shaping work needed. A night-sky gradient background (#151b40) keeps vertical cuts clear of the black-frame QA check. Project: /workspace/motion/projects/vayetzei-5787-trailer.
- 2026-11-20 (Animator): Parsha trailer videos go in Google Drive folder "Grok Animated Parsha" (My Drive root, id 1BSOmV28dWGY7LQw7-tHEIf1F5MkOBrUP; Manny, Nov 20). Re-time a finished trailer from source by wrapping window.seek(t)=>seek(t/k) and scaling cues.json (times, lens, bpm) by the same k.
- 2026-11-20 (Routines): Usage fix pattern: for login/daily sync routines, hash the source listing and stop early when it matches the last run; for watch routines, never reopen archive context files on normal runs.
