---
name: blues-recap-pdf
description: >-
  Use when building the graphical St. Louis Blues game-recap PDF, or attaching
  it to the morning rundown after a Blues game.
---
# Blues recap PDF

Script: `/workspace/blues-recap/make_recap.py` (README in the same folder). Data comes from the public NHL API (api-web.nhle.com); logos are cached in `cache/logos`, fonts in `fonts/`.

## Run
```bash
/workspace/blues-recap/.venv/bin/python /workspace/blues-recap/make_recap.py --since <YYYY-MM-DD>
```
Options (from the script): `--date YYYY-MM-DD` (a given game; default the latest completed game), `--since YYYY-MM-DD` (make a PDF only if the latest completed game is on or after that date), `--out PATH` (default `out/blues-recap-<gamedate>.pdf`). Plain `python3` also works; it re-execs into the venv.

In the morning run, set `--since` to the day after the previous rundown's date window, so each game is recapped once (after a missed run, widen `--since` to cover the missed day).

## Exit codes
- **0**: PDF made. stdout is only the absolute PDF path.
- **2**: `NO_GAME: <reason>`. No new completed game. Not an error; skip the recap.
- **3**: `API_ERROR: <reason>`. NHL API unreachable. Skip the recap and note it once.
- **1**: other failure (traceback on stderr).

## Missing venv
If the script says reportlab is missing or `/workspace/blues-recap/.venv` is gone, rebuild it:
```bash
python3 -m venv /workspace/blues-recap/.venv && /workspace/blues-recap/.venv/bin/python -m pip install reportlab cairosvg pypdf
```
(pypdf is needed by the rundown to append the recap.) Then rerun.

## Attach to the rundown
On exit 0, pass the path to the rundown builder: `make_rundown.py ... --blues-recap <path>`. That appends the recap after page 1 and links the score card to it. On exit 2 or 3, omit the flag. The recap replaces text stat tables; don't add those. Sending the rundown is the morning-combined-run skill's job.
