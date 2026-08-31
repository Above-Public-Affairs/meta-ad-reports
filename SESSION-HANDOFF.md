# Session Handoff

**Last session:** August 31, 2026

## Where we are

Shipped a new intelligence brief on the two organizations behind
**patientlednm.org** and **healthynm.org** and their New Mexico activity over the
past year (Aug 30, 2025 – Aug 30, 2026), covering the HB 99 medical malpractice
reform fight. Delivered as an HTML report **and** a 17-page print-ready PDF —
the first report in this project to ship in both formats.

Branch `claude/patient-led-healthy-nm-report-86259b`, PR
[#1](https://github.com/Above-Public-Affairs/meta-ad-reports/pull/1).

## What shipped

- `patient-led-nm-healthy-nm-ads.html` — the report, 6 Chart.js charts
- `patient-led-nm-healthy-nm-ads.pdf` — 17 pages, US Letter, fonts + charts embedded
- `Report Shortcuts/Patient-Led NM & Citizens for a Healthy New Mexico.webloc`
- CHANGELOG / PROJECT-STATUS / LESSONS updates

## Key findings (for context if this comes back)

- **Only one of the two entities advertises.** Patient-Led NM spent
  $22,100–$31,450 across 50 disclaimer-filed Meta ads (2.8–3.3M impressions,
  Sep 8 2025 – Mar 12 2026). Citizens for a Healthy New Mexico has **zero**
  archived ads of any type on either of its two Facebook Pages
  (`61580293619597`, `61576981851399`).
- Patient-Led NM founders: NM Medical Society, NM Hospital Association,
  Sacramento Mountains Foundation, Greater Albuquerque Medical Association.
  ED Annie Jung. Citizens for a Healthy NM discloses no funders, staff, or board.
- The two share an evidentiary base: CHNM's 223-physician survey sampled GAMA +
  NM Medical Society members — two of Patient-Led NM's four founders. Written up
  as organizational proximity, **not** as evidence of common control or funding.
- CHNM's last published item (Feb 2, 2026) argued the amended HB 99 "won't stop
  the bleed" — i.e. it was to the *reform* side of the bill Patient-Led NM's paid
  campaign was pushing. Never retracted.
- HB 99 passed 66–3 / 40–2, signed Mar 6 2026. Patient-Led NM's last ad ran
  Mar 12 and the page has been dark since.

## Presentation note (client direction)

The first draft framed this as a contrast between the two entities ("Two Groups,
One Message, One Ad Budget"). **The client asked for a single unified report
covering both, not a comparison.** The shipped version presents them as two
channels of one campaign — combined totals lead, profiles run sequentially, and
the messaging chart shows Patient-Led NM's own vocabulary rather than setting it
against the opposition. Keep that framing preference in mind for future
multi-entity reports.

## Known gotchas

- **PDF generation:** full Chrome with `--print-to-pdf` +
  `--run-all-compositor-stages-before-draw` **hung and leaked enough processes to
  exhaust the machine's process table** — the shell could not even `fork` (`echo`
  failed) until Chrome was quit from the GUI. The working recipe is in
  `LESSONS.md`; build script lives in the session scratchpad at
  `pdfbuild/build.sh` (not yet committed — see PROJECT-STATUS to-do).
- MCP tool arg names are easy to get wrong: `search_pages` needs `search_terms`
  (not `query`), `search_political_ads` needs `ad_reached_countries` as an
  **array**, `get_ad_volume_over_time` requires both date bounds, and
  `get_ad_details` requires `page_id` alongside `ad_id`.
- `get_page_ads` on new-style numeric Page IDs (the `615…` profile IDs) returns
  Ad Library API error 33. That is **not** proof of no ads — confirm via the Ad
  Library web UI with all ad types and all statuses before reporting a zero.
- Monthly volume tools bucket by ad **launch** date, not delivery. Patient-Led NM
  shows zero ads in Feb 2026 but had $8,500–$11,193 of January inventory still
  delivering through Feb 20. State this explicitly in reports or the gap reads as
  a retreat.

## Next steps (if picked up again)

- **Shipped and live.** Merged to `main` (`9167fa8`) and published Aug 31, 2026;
  GitHub Pages build green on that exact commit. Report:
  `https://above-public-affairs.github.io/meta-ad-reports/patient-led-nm-healthy-nm-ads.html`
  (PDF at the same path with `.pdf`). PR #1 merged.
- **⚠️ Open cleanup: 16 stale `.webloc` shortcuts.** Every pre-existing shortcut in
  `Report Shortcuts/` still points at `thecantercompany.github.io`, which **404s**.
  The live host is `above-public-affairs.github.io`. Only this session's shortcut and
  the four docs were corrected. The fix is one `sed` across the folder — see the
  LESSONS entry "The published Pages host is above-public-affairs.github.io".
- A copy of the PDF was placed at the top level of the project folder (outside the
  git checkout) at the client's request, in addition to the committed copy.
- The PDF build script still lives only in the session scratchpad at
  `pdfbuild/build.sh` — committing it into the repo is a PROJECT-STATUS to-do.
- Watch items named in the report: whether Patient-Led NM restarts if HB 99's
  damages caps are challenged, whether Citizens for a Healthy NM ever files a
  first ad (which would compel a "paid for by" disclosure), and whether the issue
  carries into the 2027 session / governor's race.
