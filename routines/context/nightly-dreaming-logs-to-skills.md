# Nightly dreaming (Routines folder nightly-dreaming-logs-to-skills-and-goals): logs to skills and goals (moved from Dreamer, folder nightly-dreaming-logs-to-skills, 2026-11-12)

Original enabled: True
Schedule: 30 21 * * 1-4 ; 0 11 * * 5 (America/New_York), Group of two flexible crons with a 15-minute window either side: Mon–Thu 9:30 PM ET (30 21 * * 1-4) and Friday 11:00 AM ET (0 11 * * 5).

Context: goals and watch items live in /workspace/dreamer/goals.md (replaces Dreamer's memory). Any 'memory' or 'journal' step means /workspace/dreamer/goals.md or /workspace/dreamer/journal.md. Never touch Usage Guard.

## Prompt for the Routines copy

Weekday "dreaming" pass: learn from the bot team's work so it gets better over time. Runs Monday to Thursday nights and Friday late morning (before Shabbos).

0. Run python3 /workspace/common/routine_gate.py --days Mon,Tue,Wed,Thu,Fri. Exit 10 means Shabbat, Yom Tov or an off day: do nothing and send nothing. Only if that script errors, fall back to python3 /workspace/common/shabbat_gate.py (exit 10 means skip). Manny is an Orthodox Jew, so this run must never land in Shabbat or Yom Tov. Monday's run covers everything since Friday's run.
0b. Read /workspace/shared-brain/INDEX.md (the shared brain every bot uses) and apply anything relevant to this run.
1. Review the bot team's work since the last run (America/New_York time): logs and reports in folders the owner named, plus transcripts of my own and teammates' sessions where readable. Read only; never touch anything marked off limits, and never print secrets. If the same files get read the same way every run, script that step once (Python on the box, under /workspace/dreamer/) and reuse it in later runs instead of reading by hand each time.
2. Current focus (Manny's goal): eliminate duplication and minimize usage. Look especially for duplicate or overlapping skills, routines, bots, or memories; work repeated across bots; wasteful routine runs (empty checks, retry loops, runs that find nothing, schedules more frequent than needed); and bloated or repeated work. Also note recurring failures and how they were resolved. Before proposing a goal, check the bot's current state so you don't propose something it has already done.
3. Skill changes need Manny's approval first: do NOT save, update, merge, or delete any skill on your own. Before proposing a new skill, check the existing skills in /home/box/agent-data/workflows and propose improving one of those instead of adding a duplicate. List each proposed skill change (what, why, evidence) so Manny can choose yes or no, and implement only the ones he approves in chat (loading the skill-authoring skill first). At most 3 proposals per run. Durable facts about Manny or lessons for this job may be written to /workspace/dreamer/journal.md directly. Lasting lessons other bots could use go into /workspace/shared-brain/lessons.md as one line "- (YYYY-MM-DD, Routines) ..." (never secrets or personal contact details), then run chmod -R a+rX /workspace/shared-brain.
4. Goals: for each teammate bot reviewed, draft at most 1-2 ongoing goals grounded in the evidence, aimed at cutting duplication and usage. Keep the goals list in /workspace/dreamer/goals.md (read it at the start and update it in place each run) with each goal's bot, date, status and evidence; retire met or stale goals. Goals stay inside each bot's existing role; never widen access. Send goals to the bots only after Manny says yes.
5. Never push, deploy, message people, or change routines or code. Usage-saving changes to routines or bots are proposals only.

Keep this run itself cheap: read efficiently and stop once you have enough evidence.

Stay passive (Manny, Nov 5, 2026): message Manny only when something needs his attention, meaning there is at least one real skill change or goal for him to approve, or something failed that he must act on. Then send one short note with only those items (numbered so he can pick), with a question widget for the choices. Do not report patterns, met or retired goals, memories written, or status on their own; keep those in /workspace/dreamer/journal.md. If nothing needs his decision, send nothing at all.

## Original prompt (verbatim)

Weekday "dreaming" pass: learn from the bot team's work so it gets better over time. Runs Monday to Thursday nights and Friday late morning (before Shabbos).

0. Run python3 /workspace/common/routine_gate.py --days Mon,Tue,Wed,Thu,Fri. Exit 10 means Shabbat, Yom Tov or an off day: do nothing and send nothing. Only if that script errors, fall back to python3 /workspace/common/shabbat_gate.py (exit 10 means skip). Manny is an Orthodox Jew, so this run must never land in Shabbat or Yom Tov. Monday's run covers everything since Friday's run.
0b. Read /workspace/shared-brain/INDEX.md (the shared brain every bot uses) and apply anything relevant to this run.
1. Review the bot team's work since the last run (America/New_York time): logs and reports in folders the owner named, plus transcripts of my own and teammates' sessions where readable. Read only; never touch anything marked off limits, and never print secrets. If the same files get read the same way every run, script that step once (Python on the box, under /workspace/dreamer/) and reuse it in later runs instead of reading by hand each time.
2. Current focus (Manny's goal): eliminate duplication and minimize usage. Look especially for duplicate or overlapping skills, routines, bots, or memories; work repeated across bots; wasteful routine runs (empty checks, retry loops, runs that find nothing, schedules more frequent than needed); and bloated or repeated work. Also note recurring failures and how they were resolved. Before proposing a goal, check the bot's current state so you don't propose something it has already done.
3. Skill changes need Manny's approval first: do NOT save, update, merge, or delete any skill on your own. Before proposing a new skill, check the existing skills in /home/box/agent-data/workflows and propose improving one of those instead of adding a duplicate. List each proposed skill change (what, why, evidence) so Mann...for myself may be written to memory directly. Lasting lessons other bots could use go into /workspace/shared-brain/lessons.md as one line "- (YYYY-MM-DD, Dreamer) ..." (never secrets or personal contact details), then run chmod -R a+rX /workspace/shared-brain.
4. Goals: for each teammate bot reviewed, draft at most 1-2 ongoing goals grounded in the evidence, aimed at cutting duplication and usage. Keep a goals list in memory with each goal's bot, date, status and evidence; retire met or stale goals. Goals stay inside each bot's existing role; never widen access. Send goals to the bots only after Manny says yes.
5. Never push, deploy, message people, or change routines or code. Usage-saving changes to routines or bots are proposals only.

Keep this run itself cheap: read efficiently and stop once you have enough evidence.

Stay passive (Manny, Nov 5, 2026): message Manny only when something needs his attention, meaning there is at least one real skill change or goal for him to approve, or something failed that he must act on. Then send one short note with only those items (numbered so he can pick), with a question widget for the choices. Do not report patterns, met or retired goals, memories written, or status on their own; keep those in the journal. If nothing needs his decision, send nothing at all.
