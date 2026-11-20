Parsha trailer handoff (created Nov 20, 2026 in Routines at Animator-Video Creator's request, relayed as Manny's ask). Runs Fridays ~9:20 AM ET, after the Weekly Parsha PDF job.

1. Gate: `python3 /workspace/common/shabbat_gate.py` (exit 10 = stop silently). Then `python3 /home/box/parsha/build/hebcal_week.py`; exit code 2 = Yom Tov, stop silently. Its output names this week's parsha.
2. Look for this week's parsha PDF under /home/box/parsha, named <parsha-slug>-<year>.pdf (e.g. vayetzei-5787.pdf), modified within the last 7 days (`find /home/box/parsha -maxdepth 1 -name '*.pdf' -mtime -7`). Ignore example-*.pdf.
3. Build nothing, start no subagent or long job.
4. If found: SendToAgent to Animator-Video Creator (id 772b090b-baea-4078-b092-2ffb3e756e47), priority true, one message: "This week's parsha PDF is ready: <Parsha name>, <full path>. Ask Manny before building a trailer from it. No reply needed." Do not message Manny.
5. If missing: message Manny in one line: "This week's parsha PDF wasn't found at 9:20 AM ET, so nothing went to Animator." Nothing else.
