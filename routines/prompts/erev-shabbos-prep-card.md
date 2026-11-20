# Erev Shabbos and Yom Tov prep card (Manny picked this Nov 20, 2026, from the weekly routine ideas, #3)
Runs Sun-Fri around 8:30 AM ET. Posts one short card in the Routines chat only on Erev Shabbos or Erev Yom Tov.
1. `python3 /workspace/common/shabbat_gate.py`. Exit 10 (today is Shabbat/Yom Tov) means stop silently.
2. Tomorrow check: `python3 /workspace/common/hebcal_check.py --date <tomorrow YYYY-MM-DD ET>`. If "skip" is false, today is not Erev, so stop silently. If true, continue (the "reason" says Shabbat and/or the Yom Tov name).
3. Gather, read-only:
   - Candle lighting time for today (and Havdalah or the next candle time if it's a 2-day Yom Tov or Yom Tov into Shabbos) for Baltimore zip 21208 from Hebcal (`https://www.hebcal.com/shabbat?cfg=json&zip=21208&M=on`, or /home/box/parsha/build/hebcal_week.py).
   - Weather for Pikesville/Baltimore MD, today through the end of Shabbos/Yom Tov, plus Sunday when the card is for Shabbos (WeatherForecast tool).
   - Events on "Manny and Ronit's calendar" (Google Calendar connector) from tonight through the end of Shabbos/Yom Tov, plus Sunday when it's Shabbos. Read only.
   - Packages due before Shabbos: open items in /workspace/family-home/purchases.md, plus a Gmail search of the last 7 days for "out for delivery", "arriving today", or "arriving tomorrow" shipping notices. List only what the sources show.
4. Post one short card to Manny (SendToUser): a title like "Erev Shabbos, Friday Nov 27" (or "Erev <Yom Tov name>"), then short lines: Candles, Weather, Calendar (each event with its time), Packages (or "none expected"). No links unless one is a tracking page. Keep it under 10 lines. Greeting at the end: "Good Shabbos" (or "Good Yom Tov").
5. If a source fails, still post the card and note the missing part in one line. Never create or change calendar events, never email or contact anyone. Start no subagent, and open at most 5 web pages.
