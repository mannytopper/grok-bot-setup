---
name: morning-combined-run
description: >-
  Use when running one combined morning routine that does several independent
  daily jobs (calendar dashboard, day rundown PDF, inbox digest, watch checks,
  digests) in one wake, calling saved scripts instead of redoing steps by hand.
---
# Combined morning run

The routine's saved prompt holds the specifics: which parts run on which days, the recipients, the Page ids and the file paths. This skill is the shared pattern.

## Principles
- **Gate first.** Run a holiday or rest-day check script (for example `python3 /workspace/common/hebcal_check.py`). If it says skip, do nothing and send nothing.
- **Keep parts independent.** If one fails, note it and continue with the rest.
- **Use scripts and connectors.** Call each part's saved script instead of redoing its steps. Use the Gmail, Outlook, Google Calendar and X connectors rather than the browser. Reuse caches written by earlier routines, such as a calendar sync's rundown cache, before re-reading sources.
- **Never send twice.** Before every email, check Sent for today's subject. Attach files directly to the one send, and confirm the attachment exists first.
- **Attach by file path, never pasted base64.** When a connector needs an attachment's encoded content, write it to a `.b64` file on the box and pass the argument as `$file:/path/to/file.b64`. Never paste base64 text into a tool call, because it adds hundreds of KB to the run's usage.
- **Stay quiet.** A part with nothing new posts nothing in chat, or one line "Nothing new." if the routine asks for that. Post failures only as one line each in a single chat message at the end.
- **Respect recipients.** Only send to the recipients the routine names, and obey any never-send list.

## Typical parts (each calls its script)
- **Calendar dashboard Page:** `cal-dashboard/build.py`, overwriting the same canvas id. Don't re-read the calendars from scratch: reuse the same morning's calendar sync pulls where the dates overlap, and carry past weeks over from the previous build instead of re-pulling them. Fetch only what no earlier pull today covered.
- **Day rundown PDF:** `morning-rundown/make_rundown.py`, with an optional sports recap from `blues-recap/make_recap.py`. Email it to the user.
- **Inbox digest:** write the day's JSON, run `inbox-digest/render.py --keep-html`, post the PNG and PDF in chat, and copy the HTML to the user's computer if approved. Include open items from `decision-queue/dq.py list --open`.
- **Watch checks:** `tesla-watch/check.py` prints `{"changed": false}` when there's nothing new. Research and post only changed sources, then run `--commit`.
- **Research digest** (for example domain sales): research, then `domain-research/prep_send.py YYYY-MM-DD` to render, confirm one page, build the attachment and check the sent marker. Send with Gmail, passing the attachment as a `$file:` path, then run `prep_send.py YYYY-MM-DD --mark-sent <msg id>`.
- **X watch** on its scheduled days: follow the x-watch-deck-build skill.

## End
Write one short log fact per part that sent something. Post in chat only what the routine says goes to chat.
