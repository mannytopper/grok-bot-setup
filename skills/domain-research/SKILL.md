---
name: domain-research
description: >-
  Use for domain-name industry research: market data, sales comps and
  valuations, aftermarket trends, registry/ICANN/UDRP/trademark questions, best
  practices, or auditing a domain portfolio listing export against a master
  list.
---
# Domain research

## Scope
- **Covers:** domain-industry market data, sales comps and valuations, trends, regulations (ICANN, registries, UDRP and trademark) and best practices.
- **Out of scope:** give a brief note and offer a related domain-industry alternative.
- **No buying, bidding, listing changes or price changes.** Research and recommendations only, unless the person explicitly approves a specific change.

## Hard rules
- Never invent numbers: prices, sales, traffic, SEO or revenue. Every figure gets a cited public source, or it's stated as not found.
- Separate verified facts, inferences (labeled as such) and recommendations.
- Flag sources that are vendor-owned or that you couldn't open directly (403 errors, pages gated behind JavaScript, search-snippet-only reads).
- Dan.com shut down in June 2025; its listings live under Afternic.
- Printables are grayscale one-pagers unless the person says otherwise.

## Preferred sources
- **Sales and market data:** DNScroll (daily volume and venue totals), NameBio (sales database and daily reports), DNJournal (weekly top sales), DropCatch (recaps via DomainGang), GoDaddy auction recaps, Sedo weekly (via TheDomains), Afternic notes, NamePros and Domain Name Wire.
- **DNScroll daily report URL pattern:** `https://dnscroll.com/daily-sales/daily-market-report-for-<month>-<day><suffix>-<year>/` (for example `daily-market-report-for-october-27th-2026`). Go straight to the dated page.
- **When NameBio blocks access, use these fallbacks in order:**
  1. NamePros threads that quote NameBio results.
  2. The NameBio daily feed at https://www.domaining.com/feed/namebio/.
  3. The paid NameBio API, only if the person has one.

  Say which fallback you used and flag the read as indirect.
- **Registry and ownership:**
  - Always check the registry's own RDAP first, for example Verisign for .com at `https://rdap.verisign.com/com/v1/domain/<name>`. It gives creation and expiry dates, registrar and status.
  - Third-party WHOIS sites can be wrong (one showed a registered name as available), so never rely on them alone.
  - Use DNS lookups (for example dns.google) for MX and live use.

## Valuation method
1. **Snapshot:** pattern (for example LNN, dictionary word, brandable), length, TLD, meanings and trademark conflicts, registry data, live use (parked, redirect, email via MX), and any public listing or asking price.
   - For numeric and LNN names, note lucky and unlucky digits. Lucky digits are 8, 6 and 9, and 88 and 888 especially. Unlucky are 4, and to a lesser degree 7 in some markets. These matter mostly to Chinese buyers and move wholesale demand.
   - Treat digit luck as a labeled inference, not a price adjustment, unless comps show the effect.
2. **Prior sales of the name itself:** check NameBio (or its fallbacks), DNJournal, NamePros and DNW. If none is found, say so.
3. **Comparables:** recent sales of the same pattern and TLD, each with date, price, venue and source.
   - Use comps from the last 24 months.
   - If there are none, widen step by step: first older comps (state their age), then a nearby pattern or TLD (state the difference).
   - When you widen, label the valuation as qualified and say why.
4. **Two ranges, each tied to its comps:**
   - **Wholesale** (investor to investor).
   - **End user** (a business buying it to use).
5. **Recommendation:** list, hold, or accept or counter an offer, with terms to consider (escrow, payment structure, email migration if the domain carries live email).
6. **Write-up:** list everything you couldn't verify.

## Daily market summary
- Cover yesterday's reported volume, the top public sales (domain, price, venue, date) and a takeaway, citing each source.
- When NameBio and DNScroll report different counts or totals, give both with citations and note that they count sales differently. Don't pick one or average them.
- If the usual daily report isn't published yet, say so instead of guessing.
- When asked for "one paragraph" (or any length in paragraphs), write prose sentences, not bullets.

## Portfolio listing audit (for example Afternic)
1. Never click tracked links in emails. The person signs in to the marketplace directly and creates a read-only API key, or exports a file.
2. **Export these fields:** domain, listing status, BIN and minimum-offer price, lease-to-own status and term, landing-page setting, views and leads, and search stats if the account offers them.
3. Compare the export against the person's master spreadsheet. Produce an exception report listing mismatches only, and change nothing.
4. The person reviews exceptions by hand. Sometimes the spreadsheet is the side that's wrong.
5. Updates happen only after explicit approval, in batches of 25–100, with a backup first and a change log (what, when, old value, new value).

## Done when
Every number is sourced or marked not found, the ranges are tied to cited comparables (with their age stated), and nothing was bought, listed or changed.
