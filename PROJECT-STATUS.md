# Meta Political, Social, & Issue Ads Library Research Tool — Status

**Last Updated:** August 31, 2026

---

## Current Status

✅ **Operational** — Workflow documented, reports being generated and published.

---

## Completed

- [x] Report generation workflow documented in CLAUDE.md
- [x] GitHub Pages repo set up for publishing
- [x] Split from Meta Ad Library MCP project
- [x] LESSONS.md added — captures the regional-targeting analysis methodology (cluster-by-creative before checking geographic delivery) learned from EDF New Mexico research
- [x] Patient-Led NM & Citizens for a Healthy New Mexico brief (Aug 31, 2026) — first report shipped as both HTML and a print-ready PDF

---

## Published Reports

Reports are published to: `https://above-public-affairs.github.io/meta-ad-reports/`

Check the repo root for current inventory. Most recent:

| Report | Slug | Formats |
|---|---|---|
| Patient-Led NM & Citizens for a Healthy New Mexico | `patient-led-nm-healthy-nm-ads` | HTML + PDF |

---

## Report Delivery Formats

Reports are HTML-first. When a PDF is requested, build it with the recipe in
`LESSONS.md` ("Generating a print-ready PDF from a report") — inline all
dependencies, then drive `chrome-headless-shell` under a watchdog. Do **not**
run full Chrome with `--run-all-compositor-stages-before-draw`; it hangs and
leaks enough helper processes to exhaust the machine's process table.

---

## To-Do

- [ ] Add index page to meta-ad-reports listing all published reports
- [ ] Refine report templates based on feedback
- [ ] Consider committing the PDF build script into the repo so it's reusable across reports rather than rebuilt per session
