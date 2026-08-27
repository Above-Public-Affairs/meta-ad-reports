# Session Handoff

**Last session:** August 26, 2026

## Where we are

This session was a chat-based research request, not a new report: the client asked
whether Environmental Defense Fund is running ads targeting New Mexico. No report was
generated — findings were delivered conversationally, with a draft client email.

## What was found

- EDF's three Meta ad entities (501(c)(3), EDF Action (c)(4), EDF Action Votes PAC)
  together spend ~$2.5M–$3.3M on Meta over the past ~20 months, almost entirely on
  national fundraising and federal-issue advocacy.
- Initial page-level regional analysis found no NM targeting — wrong conclusion. The
  client then supplied a screenshot of a live EDF ad, which led to finding a real,
  small, NM-targeted campaign the first pass had missed: "Cut oil and gas methane
  waste and pollution on the Navajo Nation" (cutmethane-navajo.org), 8 ads, ~$3.5K–$5.1K
  spend, launched Jul 20 2026, still active. New Mexico is the #1 delivery region,
  reached by all 8 ads.
- Verified (web search) that the Navajo Nation reservation spans AZ/NM/UT only — not
  Colorado — which matters because the campaign's delivery data includes Colorado,
  meaning the actual buy is a broader Southwest/Four-Corners-region target, not one
  precisely bounded to the reservation.
- Blended CPM on the Navajo campaign is elevated (~$14.74, range $11–$19) vs. EDF's
  typical $3–$8 national CPM. Frequency math argues against "narrow reservation
  audience" as the cause — more likely a small total budget keeping the campaign in
  Meta's auction learning phase, plus video-format cost.

## What shipped this session

- `LESSONS.md` — the reusable finding: cluster ads by creative before running a
  regional-delivery check, or a small targeted campaign gets averaged away by an
  advertiser's high-volume national ad activity. Includes the fix as a checklist.

## Known gotchas

- The Meta Ad Library MCP connector was unreliable this session — most tool calls
  failed silently and had to be routed around via direct HTTP calls to the same
  Railway-hosted server (`meta-ad-library-mcp-production.up.railway.app/mcp`). Worth
  checking connector health before the next research session.
- `get_ad_details` fails on EDF's page specifically — the page is too large for the
  tool to scan by ad ID. Use `analyze_spend_by_region` with a `search_terms` filter
  scoped to the specific campaign's creative text instead.
- A gap in coverage: Aug 10–21, 2026 repeatedly failed to return ad data for EDF's c3
  page across multiple retry granularities (monthly/weekly/daily). Ads spanning wider
  date ranges still surfaced in neighboring windows, so the residual risk is low, but
  a campaign confined entirely to that window would have been missed.

## Next steps (if picked up again)

- No report was requested or built for this research — if the client wants one,
  build a proper HTML intelligence brief per the standard workflow in CLAUDE.md.
- Client email draft (corrected version, acknowledging the initial miss) was provided
  in-chat but not sent — confirm whether it went out.
