---
name: Weekly parsha sheet build
description: >-
  Use when building the one-page weekly parsha PDF for teens from a per-week
  content file, then saving it to the user's computer and printing it.
---
# Weekly parsha sheet build

The builder lives in `/home/box/parsha/build/` (see its `README.md`). Only the content is new each week; layout, CSS, border, footer and icon library are fixed.

## Steps
1. **Find the week.** Run `python3 /home/box/parsha/build/hebcal_week.py` (add `--json` for machine output). It prints the coming Shabbos's diaspora parsha, aliyah boundaries, maftir and haftarah. Exit code 2 means Friday or Shabbos is Yom Tov: build and send nothing.
2. **Write the content file.** Copy the latest file in `/home/box/parsha/content/` to `<parsha-slug>-<year>.json` and rewrite only that week's material: names (English and Hebrew), verse range, theme, date line, haftarah, banner scene SVG, the 7 aliyos (Hebrew title ראשון…שביעי, Hebrew topic, verses from Hebcal, icon, summary, takeaway; maftir on the last), 3–4 charts drawn as inline SVG graphics, 4 Big ideas, footer icons. Reuse icons by name from `icons.svg` where they fit.
   - Content rules: English for ages 13–18; every person's name in Hebrew inside `<bdi>`; God written as "Hashem"; grayscale only, no meaning carried by color or shade, no large dark fills or gradients.
3. **Build.** `python3 /home/box/parsha/build/build_parsha.py /home/box/parsha/content/<slug>.json -o /home/box/parsha/<slug>.pdf`. On `BUILD FAILED` (overflow, rule break, not one page), fix the content (usually shorten text) and rerun.
4. **Look at it.** Open the grayscale PNG written next to the PDF and check that the Hebrew renders and nothing looks off.
5. **Deliver.** Copy the PDF to the user's computer folder for parsha sheets, named like `Chayei Sarah 5787.pdf`. If that file already exists, don't print again. Otherwise print one copy with PowerShell `Start-Process -FilePath <pdf> -Verb Print`, wait about 30 seconds, then close Adobe with `Get-Process | Where-Object { $_.ProcessName -match 'Acro' } | Stop-Process -Force`.
6. **Report.** Send the PDF with one sentence naming the parsha and saying whether it was saved and sent to the printer, or say what failed.
