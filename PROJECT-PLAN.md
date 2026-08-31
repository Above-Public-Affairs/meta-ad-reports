# Meta Political, Social, & Issue Ads Library Research Tool

## Project Overview

A research workflow and methodology for generating intelligence briefs on political, social, and issue advertising using Meta's Ad Library. This project houses the report generation process and published reports, separate from the underlying MCP server.

---

## Goals & Objectives

1. **Intelligence Briefs** — Generate professional-grade reports on political ad activity for policy analysts, journalists, and campaign strategists
2. **Published Reports** — Maintain a public archive of completed reports via GitHub Pages
3. **Methodology** — Document and refine the research workflow for consistent, high-quality analysis

---

## Project Structure

```
Meta Political, Social, & Issue Ads Library Research Tool/
├── CLAUDE.md            # Report generation workflow & guidelines
├── meta-ad-reports/     # GitHub Pages repo with published HTML reports
├── PROJECT-PLAN.md      # This file
└── PROJECT-STATUS.md    # Current status
```

---

## Workflow Summary

The intelligence brief workflow (detailed in `CLAUDE.md`) follows these steps:

1. **Define Topic & Scope** — Establish topic, date range, geography; do background research
2. **Define Report Boundary** — Page-bounded, keyword-bounded, or hybrid approach
3. **First Data Pull** — Initial research using Meta Ad Library MCP tools
4. **Second Data Pull** — Dig deeper for gaps, opposition, outliers, connections
5. **Develop Insights** — Correlate with real-world events, classify objectives, validate claims
6. **Generate HTML Report** — Self-contained, mobile-friendly, professional voice
7. **Save and Publish** — Push to GitHub Pages

---

## Dependencies

- **Meta Ad Library MCP** — The underlying MCP server providing API access (separate project)
- **GitHub Pages** — Hosting for published reports at `https://above-public-affairs.github.io/meta-ad-reports/`

---

## Publishing Workflow

1. Generate HTML report following `CLAUDE.md` guidelines
2. Save to `meta-ad-reports/[topic-slug].html`
3. Commit and push to GitHub
4. Report available at `https://above-public-affairs.github.io/meta-ad-reports/[topic-slug].html`
