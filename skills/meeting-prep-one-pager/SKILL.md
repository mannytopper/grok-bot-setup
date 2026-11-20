---
name: meeting-prep-one-pager
description: >-
  Use when building, refreshing, or finalizing a one-page black-and-white
  meeting prep sheet from calendar events, using the prep_filter.py and
  build_sheet.py helpers.
---
# Meeting prep one-pager

1. Fetch the candidate events with the calendar connectors (Google Calendar and Outlook calendar). Convert Outlook UTC times to the user's zone. Write them to a JSON list with these fields: source, id, title, start, end, all_day, status, my_response, organizer, attendees, description, location.
2. Run `python3 /workspace/meeting-prep/prep_filter.py events.json`. If it prints nothing, stop and send nothing. Otherwise each item is `prep` or `finalize-open-draft`. Items with `personal_hint` need a judgment call, and an entry with no other attendees is not skipped for that reason alone.
3. Gather background through connectors: the invite, related Gmail and Outlook threads, earlier sheets, handoff notes and memory. Never invent numbers or facts. Mark anything unknown with `<span class="unk">`.
4. Write content.json with title, time, location, people, purpose, agenda[], questions[], background, unknowns and sources. Then run `python3 /workspace/meeting-prep/build_sheet.py content.json <stem> --status draft`. If it exits with code 2, the sheet is longer than one page, so trim it and rebuild.
5. Append a log line (`calendar|id|start ISO|title|draft`) for each id, including the mirror id.
6. Show the preview PNG and the PDF first. Only after that, ask whether there is anything to add before finalizing.
7. To finalize, work in any additions and rebuild. Then run `python3 /workspace/meeting-prep/build_sheet.py --finalize <stem>.html --event-id <id>` once for each log id. Send the final PDF and preview, then copy the final to the destination folder, moving any older version into its archive folder.

The template is /workspace/meeting-prep/template/onepager.html. It is grayscale only, with no color coding or heavy fills, on one Letter page.
