# Weekly Parsha PDF (owner: Parsha · Weekly Teen Parsha PDF, folder: weekly-parsha-pdf)

- **Owner bot:** Parsha · Weekly Teen Parsha PDF
- **Original folder id:** `weekly-parsha-pdf`
- **Enabled state:** Enabled
- **Schedule/trigger:** `CRON_TZ=America/New_York 30 9 * * 5` (every Friday at 9:30 AM ET)
- **Timing:** Flexible (default; not exact)
- **Connectors/accounts:** None. Delivery is in chat, plus local execution on WHI-LT-26-03 (machineId `cc87a891-f809-4773-a01b-4755b0cc5cc6`).
- **Scripts:** `python3 /workspace/common/routine_gate.py --days Fri` (exit 10 skip, 0 run). `/home/box/parsha/build/hebcal_week.py` (exit 2 = Yom Tov; used as fallback if the gate errors). `/home/box/parsha/build/build_parsha.py CONTENT.json -o OUT.pdf` with template.html, style.css, icons.svg in the same folder. Weekly content files in `/home/box/parsha/content/`.
- **Skills:** weekly-parsha-sheet-build, routine-gate
- **Files/state:** Content JSON under `/home/box/parsha/content/`; output `/home/box/parsha/<slug>.pdf`. On the laptop: `C:\Users\Manny\Documents\Parsha`, named like "Chayei Sarah 5787.pdf". Default printer Brother HL-L2420DW. After printing, close Adobe Acrobat.
- **Memory facts:** Black-and-white printing only (grayscale, no meaning by color). Save to Documents\Parsha named "<Parsha> 5787.pdf". Print one copy, never twice; if this week's file is already there, don't print again and don't send an "already done" status. Close Acrobat after printing. RUNNING notice first, then the PDF with one sentence. Greet Manny with "Good Shabbos". Nothing on Shabbos or Yom Tov. This is a standing deliverable (RUNNING + PDF + print), otherwise passive. English for 13–18 year olds; God written as "Hashem". Read `/workspace/shared-brain/INDEX.md` at the start. Next main run: Friday Nov 13, 2026, 9:30 AM ET (Vayetzei).
- **Permissions:** Local execution on WHI-LT-26-03 (machineId `cc87a891-f809-4773-a01b-4755b0cc5cc6`): CopyFromBox of the PDF into Documents\Parsha; PowerShell Test-Path to skip a re-print; `Start-Process -FilePath <pdf> -Verb Print` on the default Brother HL-L2420DW; wait about 30 seconds; `Get-Process | Where-Object { $_.ProcessName -match 'Acro' } | Stop-Process -Force`. No email, no standing send.
- **Hooks:** None
- **Open issues:** The Friday Nov 13, 2026 run should stay with Parsha this week so only one printer copy goes out. After that, grant Routines local execution and confirm the laptop is online before pausing the original. Friday also collides with Alfred's one-pager at 10:00 AM ET, which prints on the same printer.

## Original prompt (verbatim)

```
Passive rule: stay silent on Yom Tov, when there's nothing to do, and on pure status. Only message Manny for the standing weekly-sheet deliverable he asked for (RUNNING notice + finished PDF), or when something failed and he needs to act. Never send "nothing new", success-only fluff, or routine-status notes.

First, run `python3 /workspace/common/routine_gate.py --days Fri` (skill routine-gate). Exit 10 means skip: stop silently, build, print and send nothing. Exit 0 means run. If the gate script itself errors (any other exit), fall back to `python3 /home/box/parsha/build/hebcal_week.py`: exit 2 there means Yom Tov, so stop silently.

Then run `python3 /home/box/parsha/build/hebcal_week.py` to get this week's parsha and aliyos (if it exits 2, stop silently). Before any other work, send Manny a short message in this chat saying the weekly parsha sheet is RUNNING (name the parsha).

Then run the @Weekly parsha sheet build skill (skill id weekly-parsha-sheet-build): copy the latest file in /home/box/parsha/content/ to a new <slug>-5787.json for this week, rewrite only the week's content (aliyah boundaries exactly as Hebcal gives them, diaspora), and build with /home/box/parsha/build/build_parsha.py into /home/box/parsha/<slug>.pdf. Fix and rebuild on any BUILD FAILED, and look at the grayscale PNG before delivering. Handle double parshiyos if Hebcal shows one.

Content rules: English for 13–18 year olds; every person's name in Hebrew inside <bdi>; God written as "Hashem"; title פרשת <name>; section header סדר העליות; aliyah titles ראשון … שביעי plus a Hebrew topic with an LTR verse reference; מפטיר; a summary and a Takeaway per aliyah; 3–4 charts drawn as graphics that fit the parsha; Big ideas row of four. Black-and-white printing only: grayscale, no meaning by color or shade, no large dark fills or gradients.

Deliver to Manny's Windows computer (WHI-LT-26-03): copy the PDF into C:\Users\Manny\Documents\Parsha (create it if missing) named like "Chayei Sarah 5787.pdf". If this week's file is already there, don't print again and don't send an "already done" status. Otherwise print one copy on his default printer (Brother HL-L2420DW) with the file's Print verb, wait about 30 seconds, then close Adobe Acrobat.

Who gets it: Manny in this chat only. Standing deliverable: the RUNNING notice at the start, then the PDF as an attachment with one sentence naming the parsha and saying whether it was saved to Documents\Parsha and sent to the printer. If something fails (for example his computer is offline), tell Manny in this chat what failed so he can act. No one else receives anything.
```

## Proposed Routines-copy prompt

```
Read /workspace/routines/context/weekly-parsha-pdf.md for context.

Passive rule: stay silent on Yom Tov, when there's nothing to do, and on pure status. Only message Manny for the standing weekly-sheet deliverable he asked for (RUNNING notice + finished PDF), or when something failed and he needs to act. Never send "nothing new", success-only fluff, or routine-status notes.

First, run `python3 /workspace/common/routine_gate.py --days Fri` (skill routine-gate). Exit 10 means skip: stop silently, build, print and send nothing. Exit 0 means run. If the gate script itself errors (any other exit), fall back to `python3 /home/box/parsha/build/hebcal_week.py`: exit 2 there means Yom Tov, so stop silently.

Then run `python3 /home/box/parsha/build/hebcal_week.py` to get this week's parsha and aliyos (if it exits 2, stop silently). Before any other work, send Manny a short message in the Routines chat in Grok Bot saying the weekly parsha sheet is RUNNING (name the parsha).

Then run the @Weekly parsha sheet build skill (skill id weekly-parsha-sheet-build): copy the latest file in /home/box/parsha/content/ to a new <slug>-5787.json for this week, rewrite only the week's content (aliyah boundaries exactly as Hebcal gives them, diaspora), and build with /home/box/parsha/build/build_parsha.py into /home/box/parsha/<slug>.pdf. Fix and rebuild on any BUILD FAILED, and look at the grayscale PNG before delivering. Handle double parshiyos if Hebcal shows one.

Content rules: English for 13–18 year olds; every person's name in Hebrew inside <bdi>; God written as "Hashem"; title פרשת <name>; section header סדר העליות; aliyah titles ראשון … שביעי plus a Hebrew topic with an LTR verse reference; מפטיר; a summary and a Takeaway per aliyah; 3–4 charts drawn as graphics that fit the parsha; Big ideas row of four. Black-and-white printing only: grayscale, no meaning by color or shade, no large dark fills or gradients.

Deliver to Manny's Windows computer (WHI-LT-26-03): copy the PDF into C:\Users\Manny\Documents\Parsha (create it if missing) named like "Chayei Sarah 5787.pdf". If this week's file is already there, don't print again and don't send an "already done" status. Otherwise print one copy on his default printer (Brother HL-L2420DW) with the file's Print verb, wait about 30 seconds, then close Adobe Acrobat.

Who gets it: Manny in the Routines chat in Grok Bot only. Standing deliverable: the RUNNING notice at the start, then the PDF as an attachment with one sentence naming the parsha and saying whether it was saved to Documents\Parsha and sent to the printer. If something fails (for example his computer is offline), tell Manny in the Routines chat in Grok Bot what failed so he can act. No one else receives anything.
```
