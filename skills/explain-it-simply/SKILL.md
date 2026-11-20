---
name: explain-it-simply
description: >-
  Use when asked to explain, simplify, define, ELI5, fact-check, or summarize
  something at the person's level, or to make a printable explainer or a short
  narrated explainer video.
---
# Explain it simply

## 1. Pin the level and the mode
- Use the level the person states. Otherwise infer it from how they asked, and default to a smart non-expert.
- Pick one mode:
  - **Quick answer:** 2–4 sentences.
  - **Deep dive:** sections, with examples.
  - **ELI5:** everyday analogy first, then the real mechanism.
  - **Visual:** a diagram, a mermaid chart, or a one-pager.
  - **Video:** see section 5.
- If the level or mode is genuinely unclear and it changes the result, ask one short question. Otherwise just pick.

## 2. Explain
- Lead with the one-sentence answer, then the mechanism in plain words.
- Define every term the first time it appears.
- Use one concrete example.
- Say what it is NOT if that's a common confusion.
- Analogies are aids, never a replacement for the actual mechanism.
- End with 1–2 natural follow-up questions, only when useful.

## 3. Facts, sources and tags
- Check any factual, current, numeric or disputed claim against real sources, and cite each one.
- Never invent numbers, quotes or sources.
- Tag inline:
  - **[No source]** for a claim you couldn't verify.
  - **[AI-generated analysis]** for your own reasoning, examples or inferences.
  - **[Bias flag]** when sources are vendor-owned, partisan or otherwise interested. Say why.
  - Note when a source was read only partially, for example through search snippets.
- For a document they gave you, summarize only what's in it and point to the section.
- For heavier research, also follow the verified-deep-research skill.

## 4. Printables
- Default to one page. Respect the person's print preferences; if they print black and white, design for grayscale with no color coding.
- Build HTML and render it to PDF with headless Chrome:
  `google-chrome --headless --disable-gpu --no-pdf-header-footer --print-to-pdf=out.pdf file:///path/page.html`
  (weasyprint and reportlab may not be installed.)
- **Check the page count:** `pdfinfo out.pdf` must show the expected Pages.
- **Check grayscale:** render with `pdftoppm -r 50 -png out.pdf chk`. In Python, confirm every pixel's max(R,G,B) minus min(R,G,B) is 0, or near 0 for anti-aliasing.

## 5. Narrated explainer video (only when asked)
- **Length:** the requested length always wins. With no request, aim for 60–90 seconds. Use 3–4 scenes for videos under about 45 seconds, and 4–6 for longer ones.
1. **Script:** save script.json as a plain list of scenes, each with an id, narration and visual notes. Check that any helper script you reuse expects the same shape.
2. **Voice:** use the platform voice if it's available and funded. Otherwise use free local TTS with kokoro-onnx (pip `kokoro-onnx`; model files `kokoro-v1.0.onnx` and `voices-v1.0.bin`; voice `af_heart` works well). Make one WAV per scene, then join them into narration.wav.
3. **Word timings:** run faster-whisper (small.en or better) with word_timestamps over each scene WAV. Correct homophones and domain terms against the script.
4. **Visuals:** Manim Community, one scene class per script scene, each lasting as long as its audio.
   - Keep all labels and key visuals out of the bottom ~20% of the frame; captions go there.
   - `manim -qh` renders to `media/videos/<file>/1080p60/`, not 1080p30. Find clips by globbing, and don't hardcode the folder or the scene count.
5. **Captions:** build an .ass subtitle file with word-by-word highlighting from the timings, offset by each scene's start time.
6. **Assemble:**
   - Write concat.txt with one `file '<clip>.mp4'` line per scene, in order.
   - Run: `ffmpeg -y -f concat -safe 0 -i concat.txt -i narration.wav -map 0:v -map 1:a -vf "ass=captions.ass" -c:v libx264 -pix_fmt yuv420p -c:a aac -shortest final.mp4`
7. **Verify:**
   - Use `ffprobe` to confirm there's an h264 video stream, an aac audio stream, and the expected duration.
   - Extract frames at about 4 points (`ffmpeg -ss <t> -i final.mp4 -frames:v 1 f<t>.png`) and look at each one. Captions should be readable and not covering labels, and visuals should match the narration.
   - **Video-review step:** when a video-review tool or subagent is available, ask it to describe the finished video and confirm it matches the script before you describe it to anyone. If none is available, say the video was checked by frame sampling only.
- **Worked example:** /workspace/dent/ holds a full pipeline (script.json, tts.py, align.py, scenes.py, build.py). Reuse it with edits:
  - align.py expects script.json to be a plain list.
  - build.py hardcodes 5 scenes and the 1080p30 folder.
  - build.py writes concat.txt but doesn't run the final ffmpeg step, so run the command above.
  - /workspace/explainer-tests/dimples/ is a 4-scene, ~28-second version.

## 6. Turning a recording or PDF into a video
- **Recording:** transcribe with faster-whisper, tighten the transcript, add captions, and keep the person's voice.
- **PDF:** summarize it into a script first, then follow section 5.

## Done when
The person has the explanation at their level, every factual claim is sourced or tagged, and any file or video has been checked by opening it.
