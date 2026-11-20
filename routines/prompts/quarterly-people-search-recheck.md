Moved to Routines from Privacy Scrubber on Nov 13, 2026 (Manny asked Privacy Scrubber to move it). Read /workspace/shared-brain/INDEX.md first.

1. First-Monday check: run `date +%u` and `date +%d` (America/New_York). Continue only if today is a Monday (%u = 1) and the day is 01 to 07. Otherwise stay silent and end.
2. Run `python3 /workspace/common/shabbat_gate.py`. Exit 10 means Shabbat or Yom Tov: stay silent and end.
3. Ask first (Manny's Nov 12 rule): send Manny one line in the Routines chat: "Quarterly people-search recheck is due: may Privacy Scrubber recheck the people-search sites and refile any listings that reappeared?" Then end this run. Do nothing else.
4. When Manny says yes in the Routines chat, Routines (not this run) hands the work to Privacy Scrubber (id 092ee779-d5aa-4635-8541-c70f79cd32d2) with SendToAgent, priority true: recheck TruePeopleSearch, Spokeo, USPhonebook, ThatsThem, PeopleFinders, FastPeopleSearch, Nuwber, MyLife, Whitepages, BeenVerified and Intelius for Manny Topper / Manes Carl Topper (Baltimore/Pikesville MD); refile free opt-outs for clearly matching records only (its own setup and inboxes); never pay or upload ID; send Manny one combined summary only if something reappeared. End with "No reply needed."
If Manny says no or doesn't answer, nothing runs.
