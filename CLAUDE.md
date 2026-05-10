# Meta Ad Library MCP — Project Instructions

> **Always read the global CLAUDE.md** at `/Users/jc/Library/Mobile Documents/com~apple~CloudDocs/Development/CLAUDE.md` first. It contains org-wide coding workflows, project standards, and the research-first development process that applies to all projects.

## Generating Intelligence Brief Reports

When asked to generate an ad intelligence report, follow this workflow. Each step involves conversation with the user before moving on.

---

### Step 1: Define the Topic & Scope

Have a conversation with the user to establish the topic, then do outside research to become an expert before pulling any ad data.

1. **Topic** — What is the report about? Define the universe clearly.
2. **Date range** — What time period should the report cover? Always ask; don't assume.
3. **Geography** — Which countries or regions? Always confirm.
4. **Background research** — Use web searches to build deep context on the topic before touching the Ad Library. Understand:
   - The key players, organizations, and stakeholders involved
   - Recent news, legislation, or events driving the conversation
   - The arguments on all sides (proponents, opponents, neutral observers)
   - Industry terminology, acronyms, and jargon used by insiders
   - Related or adjacent issues that may show up in ad messaging
   - **Cross-platform context** — Are these groups also running Google ads, TV spots, direct mail, or other campaigns? Meta is one channel; understanding the broader media strategy makes the analysis more useful even if we can't quantify other platforms.
   - **Source credibility** — Note which sources are industry-funded vs. independent. Local news often has details national coverage misses. Understanding who funds a study or organization will matter later when interpreting their ad messaging.
5. **Keywords** — Based on the research and conversation, build a comprehensive keyword list. Think about:
   - Direct terms (e.g., "data center")
   - Related terms (e.g., "hyperscale", "cloud infrastructure")
   - Opposition framing (e.g., "data center moratorium", "water usage")
   - Industry jargon and acronyms
   - Names of specific companies, organizations, or legislation
6. **Active Pages** — As keywords are explored, maintain a running list of Facebook Pages that are advertising on this topic.

### Step 2: Define the Report Boundary

Based on the keyword exploration and Pages discovered, decide with the user:

- **Page-bounded** — The report focuses on a specific set of advertisers (useful when a few key players dominate)
- **Keyword-bounded** — The report covers all ads matching the keyword universe (useful for broad topic analysis)
- **Hybrid** — Primary focus on key Pages, but include keyword-matched ads to catch smaller or emerging advertisers

This decision shapes which tools get used most heavily in the next step.

### Step 3: First Data Pull

Run an initial round of research using the tools that fit the boundary defined above. Not every report needs every tool — let the topic guide which are relevant.

#### Available Tools

**Search**
- **`search_political_ads`** — Search by keywords, country, date range, platform, language, and more
- **`get_ad_details`** — Full details on a specific ad (demographics, regional delivery, targeting)

**Advertiser Tracking**
- **`search_pages`** — Find Facebook Pages that have run political/issue ads by name or keyword
- **`get_page_ads`** — Get all ads from a specific Page
- **`compare_advertisers`** — Side-by-side comparison of multiple Pages (ad count, spend, date ranges, platforms)

**Spending Analysis**
- **`get_top_spenders`** — Highest-spending advertisers for a topic or region
- **`get_page_spend_summary`** — Spend and impression totals for a specific Page
- **`analyze_spend_by_region`** — Geographic distribution of ad spend by state/province

**Trends & Messaging**
- **`get_ad_volume_over_time`** — Ad activity and spending over time (daily, weekly, or monthly)
- **`identify_messaging_themes`** — Word frequency analysis to surface key messaging patterns

**Demographics**
- **`get_ad_demographics`** — Age and gender breakdown for a Page or search query
- **`compare_demographic_targeting`** — Compare demographic reach patterns across multiple advertisers

**Critical note on delivery data vs. targeting intent:** All Ad Library data — demographics, geography, platform — shows **delivery results** (who saw the ad), not **targeting inputs** (what the advertiser selected). These are very different things, and reports must never conflate them.

Demographic or geographic skews in delivery data can be caused by many things *other than* explicit targeting:
- **First-party data** — The advertiser uploaded a customer/donor/supporter list. The list's composition drives delivery demographics, not age or location selectors.
- **Third-party/lookalike audiences** — An audience segment that over-indexes with a particular demographic will produce skewed delivery without the advertiser ever touching a demographic filter.
- **Algorithmic optimization** — Meta's delivery system optimizes toward users most likely to take the desired action (click, convert, engage). This creates feedback loops that can concentrate delivery in specific demographics or regions.
- **Creative resonance** — Ad content that resonates more with certain groups gets higher engagement, which Meta's algorithm rewards with more delivery to similar users.
- **Placement and platform effects** — Instagram skews younger than Facebook. Audience Network skews differently than feed. Platform selection affects demographic delivery independently of targeting.

**In reports:** Describe what the delivery data *shows* without asserting what the advertiser *intended*. Say "ads reached predominantly 65+ audiences" not "ads targeted seniors." If you infer likely targeting strategy, label it as inference and explain the evidence. A skew toward 65+ women in Texas could mean the advertiser targeted that demo explicitly, or it could mean they uploaded a donor list that happens to be older Texas women, or it could mean Meta's algorithm found that group most responsive to the creative.

### Step 4: Second Data Pull — Dig Deeper

Review the initial findings and run a second round specifically looking for:

- **Gaps** — Advertisers or angles that didn't surface in the first pull
- **Opposition** — Who's spending against the topic, not just for it
- **Outliers** — Unexpected spenders, unusual geographic targeting, demographic skews
- **Connections** — Are multiple Pages funded by the same entity? Do spending patterns correlate with events?
- **Emerging activity** — New advertisers or recent spend spikes that indicate shifting dynamics
- **Silence as signal** — Who *stopped* advertising, and when? A sudden drop can mean a campaign ended, a legislative battle was decided, or funding dried up. Absence is data.
- **Disclosure analysis** — Examine "paid for by" disclaimers. Are they PACs, LLCs, nonprofits, or individuals? The organizational structure behind an ad campaign reveals strategic intent.

Use the same tools as Step 3, but with refined queries informed by what the first pull revealed.

### Step 5: Develop Insights

Before generating the report, synthesize the ad data with real-world context. This is where raw data becomes analysis.

1. **Correlate ad activity with events** — Use web searches (especially news) to connect spending spikes, new advertisers, or messaging shifts to real-world triggers: legislation, elections, court rulings, media coverage, project announcements, etc.
2. **Identify the narrative landscape** — Who is trying to shape public opinion, and what story are they telling? Where do the narratives conflict?
3. **Follow the money** — What do spending patterns reveal about strategic intent? Are advertisers front groups, industry coalitions, grassroots organizations, or political campaigns?
4. **Classify ad objectives** — For each advertiser or ad cluster, assess the likely goal. Common objectives include:
   - **Awareness** — Shaping public perception or introducing a narrative (no clear call to action)
   - **Fundraising** — Driving donations, often with urgency language and donate buttons
   - **Action/mobilization** — Pushing people to call legislators, sign petitions, attend hearings, or vote
   - **Opposition** — Designed to block, delay, or discredit a project, policy, or candidate
   - **Reputation/brand** — Corporate image management, often from companies facing public scrutiny
   - **Voter persuasion** — Targeted at shifting opinion in a specific electorate ahead of a decision point

   The objective often reveals more about strategy than the ad text alone. An awareness campaign from an energy company reads differently than a mobilization campaign from a community group, even if both reference the same project.
5. **Spot what's missing** — Sometimes the insight is what *isn't* being said or who *isn't* advertising. Gaps in the data can be as telling as the data itself.
6. **Validate claims** — If ads make specific claims (jobs numbers, environmental impact, cost figures), use web searches to fact-check against news reporting and public records.
7. **Contextualize scale** — Raw numbers need framing. Is $500K a lot or a little for this topic, region, or time period? Is 10 advertisers concentrated or fragmented? Compare against benchmarks, prior periods, or other topics to give the reader a sense of whether the numbers are significant.
8. **Cite your sources** — Every factual claim, statistic, or contextual assertion in the report must be traceable. If an insight comes from a news article, link to it. If a spending figure comes from the Ad Library, say so. If an interpretation is an inference, label it as such and explain the evidence supporting it. Never present assumptions as facts without stating the basis.

The insights developed here should drive the report's strategic takeaway and shape how the data is presented.

### Step 5.5: Data Confirmation Checkpoint

**Before generating the report HTML**, present the user with a summary table for approval. The table must include:

| Advertiser Name | State/Location | Total Spend (Range) | Date Range of Ads | Number of Ads |
|-----------------|---------------|---------------------|-------------------|---------------|
| Example Page    | Texas          | $50K–$75K           | Mar 2024–Jan 2026 | 142           |

- Include **every advertiser** that will appear in the report — in charts, top stats, narrative, or any other section.
- Wait for the user to confirm the data is correct and in-scope before proceeding to Step 6.
- If the user flags an advertiser as out-of-scope or incorrect, remove it and re-present the updated table.
- This step is **mandatory** — never skip it, even for small reports.

### Step 6: Generate the HTML Report

Design the report structure based on the data collected. Each report should be tailored to its topic — let the data shape the layout, sections, and visualizations rather than following a fixed template. Reference existing reports in `Public Files/` for design inspiration, but adapt freely.

**Design Principles:**

Reports should be **visually rich and chart-heavy**. The reader should encounter more charts, infographics, and visual elements than walls of text. Data tells the story — visualize it.

The specific layout is up to each report, but these principles should hold across all of them:

- **Visual-first storytelling** — Every major finding should have a corresponding visualization. If you can show it in a chart, don't just describe it in a paragraph. The report should feel like an infographic-driven intelligence brief, not a text document with occasional charts.
- **Chart density** — Aim for a chart, graph, or visual element every 1-2 sections. Types to use liberally:
  - **Bar charts** — Spending comparisons, advertiser rankings, ad volume
  - **Line/area charts** — Spending over time, ad volume trends, activity timelines
  - **Donut/pie charts** — Spend share, demographic breakdowns, platform distribution
  - **Heatmaps** — Geographic targeting intensity, time-of-day patterns
  - **Treemaps** — Proportional spend by advertiser or category
  - **Stacked bars** — Multi-dimensional comparisons (e.g., spend by advertiser over time)
  - **Stat cards/KPI tiles** — Hero numbers with context (total spend, ad count, advertiser count, date range)
  - **Comparison tables with visual indicators** — Progress bars, color-coded cells, sparklines
  - **Timelines** — Annotated event timelines correlating ad activity with real-world events
  - **Flow diagrams** — Money flows, organizational relationships, funding networks
- **Infographic elements** — Use callout boxes, pull quotes from ad text, annotated screenshots, icon-driven stat blocks, and visual summaries. These break up the page and make key findings scannable.
- **Annotated spend timelines (recommended)** — When a report covers spending over time, build an annotated bar chart that overlays real-world events on the spending data. This is the single most effective visualization for connecting ad activity to context. Implementation: monthly spend bars (color-coded by campaign phase or advertiser) with vertical dashed annotation lines marking key events (legislation signed, elections, endorsements, campaign launches, etc.). Labels should appear at the top or edge of the chart with semi-transparent backgrounds. Use the Chart.js annotation plugin (`chartjs-plugin-annotation`). See the ACP report's Monthly Spend Timeline (`american-clean-power-association-ads.html`) as the reference implementation. Every report with a meaningful time dimension should include one of these.
- **Chart.js for interactivity** — Use Chart.js (loaded via CDN) for interactive charts with tooltips and hover states. Include the `<script src="https://cdn.jsdelivr.net/npm/chart.js"></script>` tag. For simpler visuals (stat cards, progress bars, heatmaps), use pure CSS/HTML.
- **Typography hierarchy** — Clear visual distinction between headings, body text, data labels, and captions. The report should scan well at a glance before reading in detail.
- **Color with meaning** — If colors represent something (pro/anti, party affiliation, stance), use them consistently throughout the report and include a legend or explanation. Define a color palette early and stick to it.
- **White space** — Give sections room to breathe. Dense data needs separation to be readable, especially on mobile.
- **Progressive disclosure** — Lead with the headline finding, then support with detail. Don't bury the insight under methodology or background. The reader should know the key takeaway within the first screen — ideally through a visual dashboard or key stats section at the top.

**Voice & Terminology:**

Write for an informed audience. The reader is a policy analyst, campaign strategist, journalist, or industry professional — not a general consumer. They don't need basic concepts explained, but they do expect precision.

- Use industry terminology naturally. Say "dark money group" not "an organization that doesn't disclose its donors." Say "astroturf campaign" not "a campaign designed to look grassroots but isn't."
- Use political ad terminology correctly: "paid for by" disclaimers, "issue ads" vs. "electoral ads," "independent expenditure," "in-kind contribution," etc.
- Refer to organizational types precisely: 501(c)(4), super PAC, trade association, advocacy nonprofit — not just "group" or "organization."
- When a term has specific meaning in the domain (e.g., "BESS" in energy, "NEPA" in permitting, "RTO" in grid operations), use it without over-explaining. First mention can include a brief parenthetical if it's niche, but don't talk down to the reader.
- Describe ad strategies using the language practitioners use: "persuasion campaign," "issue framing," "opposition research," "earned media strategy," "grasstops engagement."
- Avoid hedging language that weakens analysis. If the data supports a conclusion, state it directly. "This spending pattern is consistent with a coordinated campaign" — not "it seems like maybe these ads could potentially be related."

**Requirements:**
- Self-contained HTML — all CSS inline (no external stylesheets except Google Fonts and Chart.js via CDN)
- Mobile-friendly — responsive design with a mobile breakpoint
- Print styles included
- All ad links point to `https://www.facebook.com/ads/library/?id=XXXXX` with `target="_blank"`
- Chart data must match the date range stated in the report
- Include a strategic takeaway that provides genuine analytical insight, not just data summary
- Footer shows data source and retrieval date
- **Methodology note** — Include a brief section explaining the search parameters used, what the data covers, and its limitations (e.g., Meta's spend figures are ranges not exact amounts, keyword searches may miss ads that use different terminology, data reflects only Meta platforms). Transparency about methodology builds credibility.

### Step 7: Save and Publish

1. **Save the HTML file** to: `meta-ad-reports/[topic-slug].html`
2. **Push to GitHub Pages**:
   ```bash
   cd meta-ad-reports
   git add [topic-slug].html
   git commit -m "Add [Topic] intelligence brief"
   git push
   ```
3. **Create a shortcut** in the `Report Shortcuts/` folder:
   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
   <plist version="1.0">
   <dict>
       <key>URL</key>
       <string>https://thecantercompany.github.io/meta-ad-reports/[topic-slug].html</string>
   </dict>
   </plist>
   ```
   Save as `Report Shortcuts/[Human-Readable Title].webloc`
4. **Public URL**: `https://thecantercompany.github.io/meta-ad-reports/[topic-slug].html`

### File Naming Convention
- Lowercase, hyphenated: `texas-data-center-ads.html`, `texas-bess-ads.html`
- Pattern: `[topic-slug].html`

---

## Report Generation

### Editorial Standards

When working on political ad reports:

1. **Do NOT conflate different bills or legislative actions.** Each piece of legislation must be identified precisely by name, number, chamber, and jurisdiction. If two bills address similar topics, describe each separately — do not merge them into a single reference or imply they are the same action.
2. **Use neutral, evidence-based framing.** Avoid characterizations like "credibility gap," "suspicious," or "misleading" unless directly supported by cited evidence. Let the data speak — describe what the numbers show and let the reader draw conclusions. Analytical conclusions are welcome when grounded in evidence; editorializing is not.
3. **Characterize advertiser audiences accurately based on actual targeting data, not assumptions.** Use delivery data as described in Step 3's critical note. Never infer demographic intent from organizational type (e.g., don't assume an energy trade group "targets conservatives" without delivery data supporting it).

### Geographic Scope Discipline

When generating ad intelligence reports, **NEVER include advertisers outside the specified geographic scope.** Always verify each advertiser's geographic relevance before including them in any report, top stats, or charts. If uncertain whether an advertiser operates within the defined geography, flag it to the user rather than include it. A national advertiser that happens to run ads visible in a state is not the same as a state-focused advertiser — apply judgment about relevance, and when in doubt, exclude and note the exclusion.

---

## Changelog

**Always update `CHANGELOG.md`** in this project folder when pushing any changes — new reports, tool updates, workflow changes, bug fixes, etc. This is mandatory on every push. See the root `CLAUDE.md` for the changelog format.

---

## Troubleshooting

### URL Fetch Failures

When a URL returns a 403 error, do NOT repeatedly retry with the same method. Instead:

1. Immediately try a curl-based fallback with browser-like headers (User-Agent, Accept, etc.)
2. If curl also fails, ask the user to provide the content directly (paste text, screenshot, or alternative URL)
3. Do not attempt more than two fetches of the same URL with different methods before asking the user
