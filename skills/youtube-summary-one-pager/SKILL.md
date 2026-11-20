---
name: youtube-summary-one-pager
description: >-
  Use when someone sends a YouTube link and wants it summarized, in chat and/or
  as a graphical one-page PDF/PNG summary.
---
# YouTube summary + graphical one-pager

Reads a YouTube video through its captions (no watching needed), writes a plain-language summary, and optionally renders a one-page graphic (US Letter PDF + PNG). Scripts live in `/workspace/video-summary/` on the shared box.

## 1. Get the transcript
```sh
cd /workspace/video-summary && python3 get_transcript.py "<youtube url>" out
```
- Writes `out/<id>.txt` (transcript) and `out/<id>.meta.json` (title, channel, duration).
- Needs `yt-dlp` and `youtube-transcript-api` (`pip install -U yt-dlp youtube-transcript-api` if missing). Captions come from youtube-transcript-api because yt-dlp subtitle downloads often hit HTTP 429.
- If the video has no captions at all, hand the video to a video-watching helper instead (ask the user first if that needs a subagent).

## 2. Read and summarize
- Read the transcript in chunks (`cut -b` ranges); it is one long line.
- Auto-captions drop or garble names and non-English terms (e.g. Hebrew). Fill them in only from clear context and say so in the summary and the footer note. Never invent quotes or numbers.
- Chat summary: one-line intro (speaker, channel, length), then 4-6 short bolded sections in plain sentences.

## 3. One-pager (when asked for a graphic/one-pager/PDF)
Write a JSON file:
```json
{"title":"...","meta":"Speaker · Channel · 41:50","url":"https://www.youtube.com/watch?v=...",
 "lead":"one-sentence framing",
 "sections":[{"heading":"...","points":["...","..."]}],
 "takeaway":"one sentence","note":"Summarized from auto-captions; ..."}
```
- Use 6 sections (fits a 2x3 grid) with 3-4 short points each; keep each point under about 25 words.
Then render:
```sh
python3 render_onepager.py summary.json /workspace/video-summary/<slug>
```
- Outputs `<slug>.pdf` and `<slug>.png`; it prints the page count. If it spills past 1 page, shorten points and re-render.
- Look at the PNG before sending. Attach the PDF (and PNG image if useful) in chat.

## Notes
- Read-only: never posts, comments, or downloads the video file itself.
- Clean up `out/` transcripts when no longer needed.
