# Changelog

All notable changes to Meta Ad Library Research Tool will be documented in this file.

## [2026-08-31]

### Added
- Patient-Led NM & Citizens for a Healthy New Mexico intelligence brief — one-year analysis (Aug 2025–Aug 2026) of the two organizations behind patientlednm.org and healthynm.org during New Mexico's HB 99 medical malpractice reform fight. Presented as a single unified campaign report covering both entities as two channels of one effort: Patient-Led NM (founded by the NM Medical Society, NM Hospital Association, Sacramento Mountains Foundation, and Greater Albuquerque Medical Association) carried all paid media — $22,100–$31,450 across 50 disclaimer-filed ads and 2.8–3.3M impressions — while Citizens for a Healthy New Mexico carried research and earned media (7 op-eds, a statewide voter poll, a 223-physician survey) with zero archived advertising and no disclosed funders, staff, or board. Covers the combined campaign cadence, the February launch gap (no new creatives during the floor votes, with $8,500–$11,193 of January inventory still delivering), Citizens for a Healthy NM's Feb 2 position that the amended bill would not stop physician departures, and the campaign's conclusion 11 days after the governor's signature. Contextualized against New Mexico Safety Over Profit, the American Tort Reform Association's post-signing NM creative, and both legislative caucuses' credit-claiming. Shipped as both an interactive HTML report and a 17-page print-ready PDF.
- LESSONS.md — recipe for generating a print-ready PDF from a report, written after a headless-Chrome export hung and exhausted the machine's process table. Covers removing all network dependencies before rendering (inline Chart.js, plugins, and latin font subsets), using `chrome-headless-shell` under a mandatory watchdog instead of full Chrome, the `--run-all-compositor-stages-before-draw` flag to avoid, splicing inlined assets with literal string surgery rather than `re.sub`, and the two classes of print-CSS defect (page-break splits and colliding chart annotations) that are invisible on screen and only show up in the PDF.

### Changed
- Patient-Led NM brief restructured from an A-vs-B comparison of the two organizations into a single unified report covering both as two channels of one campaign, per client direction.

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
