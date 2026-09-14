# Changelog

All notable changes to Meta Ad Library Research Tool will be documented in this file.

## [2026-09-14b]

### Fixed
- **Retracted the "24-day blackout" framing** from the Santa Monica brief published earlier today. It was wrong twice over. First, the ads never stopped: 20 Trussler ads and 3 Gill ads were still actively delivering through the period, which is precisely why disclosed spend kept rising. "Blackout" described a gap in *new creative launches*, but the word implies dark screens, and a reader would reasonably take it to mean the race had gone quiet. Second, an active-status query surfaced a **new Eli Gill ad launched Sep 14** ("Big Dad Energy"), so the "nothing new since Aug 21" claim was also false. Root cause: `compare_advertisers` with the default `ALL` status reported Gill's date range as ending Aug 21 and returned 5 ads; the same-day ad only appeared on an explicit `ACTIVE`-status query. **Lesson: never characterize an advertiser as dormant from a date range alone — confirm with an `ad_active_status: ACTIVE` query before making any claim about a campaign going quiet.**
- Corrected Eli Gill throughout: 5 → **6 ads**, $400–$895 → **$600–$1,194**, date range now May 31 – Sep 14. Report totals now **90 ads, $7,500–$16,810, 874,800–1,079,210 impressions**.
- Report reframed around what the data actually supports: one candidate (Trussler) carries 65–84% of disclosed spend, total race spend is very small, and the city's institutional actors are entirely absent from Meta. Replaced the "days since last new ad" stat with "still delivering: 23 ads," and added a callout explaining that ad count and spend move independently — spend accrues on ads already in market.

### Changed
- **Recategorized Santa Monica Neighbors** from "⚠ Unattributed / flagged — no committee filing found" to **"Issue advocacy · funders undisclosed."** The prior framing implied a compliance failure that the evidence does not support. Research into the actual thresholds found three reasons the page likely had no obligation to register: (1) under FPPC Reg. 18225, IE-committee registration attaches to *express advocacy* — express words, or content within **60 days** of an election that unambiguously urges a result — while these ads ran Apr 8–May 1, six to seven months out, with no express words, before candidate filing had opened and while Torosis was a sitting mayor rather than a candidate; (2) registration attaches at **$1,000** in independent expenditures and Meta discloses only the range **$600–$4,659**, which straddles that line (35 of 41 ads are $0–$99); (3) **a Meta "paid for by" disclaimer is a platform requirement, not a legal filing** — Meta mandates authorization for any ad touching elections, legislation, or social issues, explicitly including issue advocacy that asks for no votes. The funding opacity is still noted as a transparency observation, with the caveat that the analysis would change if the page resumes advertising inside the 60-day window. Added a matching methodology bullet so the disclaimer/filing distinction isn't conflated elsewhere.

### Added
- **Complete Ad Index** (section 06) — all 90 ads with launch date, creative theme, disclosed spend, and a direct Meta Ad Library link, grouped by advertiser and sorted by spend, so every figure in the report can be checked at source. Each block's totals tie exactly to the page-level figures Meta reports ($6,300–$10,858 / $600–$4,659 / $600–$1,194 / $0–$99), which independently confirms the index is complete. Inline Ad Library links also added throughout the timeline; the report now carries 112 ad links.

## [2026-09-14]

### Changed
- Santa Monica City Council 2026 brief refreshed through Sep 14, 2026 (supersedes the Sep 4 edition). **Headline finding of the refresh is the silence:** no advertiser in the race has launched a new ad since Aug 21, 2026 — a 24-day blackout with 50 days to Election Day. Spend rose only through accrual on already-running ads: Trussler $4,900–$9,458 → $6,300–$10,858 (42 ads, unchanged), Gill $400–$895 → $600–$1,095 (5 ads, unchanged), Santa Monica Neighbors unchanged at $600–$4,659 and now dormant four months. Combined totals now $7,500–$16,711 across 89 ads and 874,800–1,079,111 impressions.
- Added **L.A. Local Network** (Page ID 1298862009966283, funded by Surround Sound News) as a fourth advertiser, per client direction. Only its single Santa Monica ad ($0–$99, Sep 9, on the council's Realignment Plan zoning adoption) counts toward report totals; its five unrelated LA-area ads are excluded and the narrow scope is disclosed on the profile card. It is a news publisher running content promotion, not a race advertiser — the only paid Meta content about Santa Monica council decisions during the campaign blackout.
- Re-verified the zero-activity list by direct Page ID query and promoted it to its own section with a table: Torosis, Negrete, SMRR, SM Firefighters IAFF Local 1109, SMPOA, Santa Monica Forward, Coalition of SM City Employees PAC, and Santa Monicans for a Real Positive Future all still return 0 ads delivered in 2026.
- Added an annotated monthly spend chart (Chart.js annotation plugin) with candidate-filing event lines and a shaded band marking the ad blackout, plus a "What Changed Since September 4" delta section.
- Added sourced budget context to Trussler's profile: his highest-spending creative campaigns on a "$35 million deficit" while the city's finance director reported an $8.95M projected surplus, reversing the $29.6M deficit projected in Oct 2025. Both figures presented as published, with the caveat that they may describe different years or funds.
- Documented the two excluded keyword-scan hits — Tom Shadrach for City Council (Cape Coral, FL) and SCANPH / ClientEarth / Union of Concerned Scientists (national issue campaigns) — in the methodology.

### Fixed
- Horizontal overflow at mobile widths in the Santa Monica report: grid children (chart boxes, stat cards, ad cards, org rows) had default `min-width: auto`, so a Chart.js canvas held its container wider than a 375px viewport and the page scrolled sideways. Added `min-width: 0` on grid children and `max-width: 100%` on chart canvases; verified scrollWidth now equals viewport width at 375px.

## [2026-09-04]

### Added
- Santa Monica City Council 2026 — Meta Ad Spend intelligence brief. Covers the Nov 3, 2026 general election (three at-large seats) from Jan 1 – Sep 4, 2026. Finds only three advertisers with any disclosed Meta political ad activity in the race: Doug Trussler for Santa Monica City Council (42 ads, $4,900–$9,458, Jul 8–Aug 11), Santa Monica Neighbors (41 ads, $600–$4,659, Apr 8–May 1 — an issue-advocacy page attacking Mayor Torosis and the Ocean Avenue homeless-housing siting process, flagged as unattributed since no FPPC/Cal-Access or City Clerk filing was found under that name), and Eli Gill for Santa Monica City Council (5 ads, $400–$895, May 31–Aug 21). Documents that no other candidate or organization active in the race — including incumbents Caroline Torosis and Lana Negrete — has any 2026 Meta ad activity on record as of retrieval. Scoped to ad spend only, per client direction, without campaign-finance/fundraising comparison.

## [2026-08-31]

### Added
- Patient-Led NM & Citizens for a Healthy New Mexico intelligence brief — one-year analysis (Aug 2025–Aug 2026) of the two organizations behind patientlednm.org and healthynm.org during New Mexico's HB 99 medical malpractice reform fight. Presented as a single unified campaign report covering both entities as two channels of one effort: Patient-Led NM (founded by the NM Medical Society, NM Hospital Association, Sacramento Mountains Foundation, and Greater Albuquerque Medical Association) carried all paid media — $22,100–$31,450 across 50 disclaimer-filed ads and 2.8–3.3M impressions — while Citizens for a Healthy New Mexico carried research and earned media (7 op-eds, a statewide voter poll, a 223-physician survey) with zero archived advertising and no disclosed funders, staff, or board. Covers the combined campaign cadence, the February launch gap (no new creatives during the floor votes, with $8,500–$11,193 of January inventory still delivering), Citizens for a Healthy NM's Feb 2 position that the amended bill would not stop physician departures, and the campaign's conclusion 11 days after the governor's signature. Contextualized against New Mexico Safety Over Profit, the American Tort Reform Association's post-signing NM creative, and both legislative caucuses' credit-claiming. Shipped as both an interactive HTML report and a 17-page print-ready PDF.
- LESSONS.md — recipe for generating a print-ready PDF from a report, written after a headless-Chrome export hung and exhausted the machine's process table. Covers removing all network dependencies before rendering (inline Chart.js, plugins, and latin font subsets), using `chrome-headless-shell` under a mandatory watchdog instead of full Chrome, the `--run-all-compositor-stages-before-draw` flag to avoid, splicing inlined assets with literal string surgery rather than `re.sub`, and the two classes of print-CSS defect (page-break splits and colliding chart annotations) that are invisible on screen and only show up in the PDF.

### Changed
- Patient-Led NM brief restructured from an A-vs-B comparison of the two organizations into a single unified report covering both as two channels of one campaign, per client direction.
- Corrected the documented GitHub Pages host from `thecantercompany.github.io` to `above-public-affairs.github.io` in CLAUDE.md, PROJECT-PLAN.md, PROJECT-STATUS.md, and SESSION-HANDOFF.md — the old host 404s and there is no redirect. Fixed this report's shortcut to match and added a LESSONS entry to read the host from the Pages API rather than trusting the documented string. **Note: the 16 pre-existing shortcuts in `Report Shortcuts/` still point at the dead host and remain to be swept.**

## [2026-08-26]

### Added
- LESSONS.md — captures a methodology gap found during EDF New Mexico ad-targeting research: page-level regional delivery averages can mask a small, genuinely-targeted campaign when an advertiser also runs high volumes of untargeted national ads. Documents the fix (cluster ads by creative before checking regional delivery, search geographic proxies alongside place names, and use a monthly rank sweep as a backstop) for future targeting-analysis requests.

## [2026-05-13]

### Added
- Texas US Senate GOTV — Meta Ad Intelligence Brief 2024 vs 2026. Four-window comparison (2024 primary, 2024 general, 2026 primary, 2026 post-primary/runoff) of get-out-the-vote advertising on Meta's political ad archive for the Cruz–Allred and Cornyn–Paxton/Talarico cycles. Profiles 10 advertisers — Powered by People, Voto Latino, Texas Organizing Project, Voter Participation Center, Black Voters Matter Fund, Mi Familia Vota, Mi Familia en Acción, Texas Freedom Network, Texas Rising, Asian Texans for Justice — with estimated TX-only spend per window, verbatim ad creative samples, messaging evolution analysis, and a critical-absences callout for major TX GOTV orgs that don't appear in the archive (TDP, RPT, MoveTexas, Texas Majority PAC, Battleground Texas, etc.). Documents that the 2026 Democratic primary turnout doubling was not mirrored by any GOTV ad spend surge — total estimated TX GOTV spend was essentially flat across the two primary windows.

## [2026-05-12]

### Added
- Corporate GOTV on Meta 2020–2024 intelligence brief — three-cycle analysis of consumer brand and corporate-funded nonprofit GOTV advertising on Meta's political ad archive. Covers 10 anchor advertisers (Ben & Jerry's, Voto Latino, Voter Participation Center, Black Voters Matter Fund, Mi Familia Vota, VOTE411/LWV, Lyft, Vet the Vote, OLÉ NewMexico, Patagonia) with per-cycle spend trajectories, Texas & New Mexico regional delivery, messaging strategies by operator type, and a 5-year event timeline. Documents the central methodological finding that most consumer-brand GOTV (Patagonia, Old Navy, Nike, Snap, Microsoft, etc.) runs outside the political archive as commercial brand content — and analyzes what the archive does capture.

## [2026-05-05]

### Added
- 2026 Primary GOTV intelligence brief — Texas & New Mexico nonprofit advertiser landscape (Jul 2025–Mar 2026). Profiles 12 organizations including Powered by People, ACLU of Texas, BakerRipley, Voto Latino, OLÉ NM, NM Kids CAN, AFP-NM, ProgressNow NM with verbatim ad copy, spend timelines, and theme analysis.

## [2026-03-26]

### Added
- WATR Alliance NM Produced Water Reuse intelligence brief — analysis of 501(c)(6) trade association's Meta ad campaign during WQCC regulatory battle, covering organizational background, two-phase messaging strategy, demographic delivery, and strategic timing correlation with Governor's office email scandal

## [2026-03-04]

### Added
- Sam Bregman for NM Governor intelligence brief — 2026 ad analysis covering ICE enforcement messaging, campaign launch themes, demographics, and strategic positioning for the June 2026 Democratic primary
