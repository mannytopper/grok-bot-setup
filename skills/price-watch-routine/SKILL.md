---
name: Price watch routine
description: >-
  Use when a scheduled routine checks watched product listings against price
  targets with a helper script (price_watch.py plus a JSON state file), falling
  back to WebFetch when a page is blocked, and alerts only when something newly
  qualifies.
---
# Price watch routine (script first, WebFetch fallback)

The routine that runs this skill names the folder holding the script, the state file, and the history log.

## Files
- `scripts/price_watch.py`: fetches, parses, compares, and records.
- `price-state.json`: for each item, its URL, type, rules, last-seen values, already-alerted prices, and a `paused` flag.
- `price-history.md`: the dated log. The script appends to it.

## Steps
1. If the routine says to skip rest days or holidays, skip the run on those days.
2. Run `python3 scripts/price_watch.py check`. It writes nothing and prints JSON:
   - `items.<id>.status`: fetched, blocked, error, or paused.
   - Each item's values: price, list price, coupon, effective price, stock, rating, rating count, required part.
   - `alerts`, `alert_keys`, and `needs_fallback`.
3. For each id in `needs_fallback`, open the item's URL with WebFetch, and use the browser only if WebFetch fails too. Read the same fields, apply that item's rules from the state file, and skip prices already in `alerted`. Record anything you can't read as unknown. Never guess.
4. Skip paused items, but leave them in the state file so they can be turned back on.
5. Put together the final alerts from the script's `alerts` plus anything found on fallback pages. A kit alert includes the add-on's price and the kit-plus-add-on total. Every product name is a Markdown link to its page.
6. Record the run in a JSON file shaped like `{"items":{"<id>":{price, coupon, in_stock, rating, rating_count, slide_hammer, source:"script|webfetch", note}}, "alerts_sent":["<alert key>"], "summary":"..."}`. Then run `python3 scripts/price_watch.py record that.json`. List only alerts you actually sent. Read the `qualifying_but_not_marked` warning in the output.

## Alert and quiet rules
- Alert only when an item newly meets its rule: its effective price (after any clip coupon) is below the target, every quality condition holds, and that price hasn't been alerted already.
- When nothing qualifies, send nothing, but still record the run.
- Send alerts only to the user's alert channel. Never buy anything, and never message anyone else.

## Limits
- The parser handles Amazon listings only. Captcha or stripped-down pages come back as `blocked`, and those fall back to WebFetch.
- It only sees coupons shown on the product page. Coupons that appear only at checkout are missed.
