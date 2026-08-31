# Lessons

## Regional targeting analysis: cluster by creative before checking geography

**What happened:** A client asked whether EDF was running ads targeting New Mexico. Our system averaged ad delivery across EDF's entire account (2,691 ads/463 clusters over ~20 months) and concluded there was no NM-specific targeting. The client then sent a screenshot of an EDF ad they'd seen — a live, NM-targeted "Cut methane on the Navajo Nation" campaign (8 ads, $3.5K–$5K spend, New Mexico reached by 8 of 8 ads). Re-checking confirmed it was real and had been missed.

**Root cause:** Page-level regional breakdowns average across everything an advertiser runs. EDF posts ~250 national fundraising ads/month; an 8-ad state-specific campaign is statistically invisible in that average — it never cracked New Mexico into the top 8 regions except in the exact month it launched, and even then only barely. Compounding this: the campaign's creative said "Navajo Nation," not "New Mexico," so a keyword search on the state name also missed it.

**Fix — always do both when checking if an advertiser targets a place:**
1. **Cluster ads by creative/campaign first**, then run the regional breakdown on each cluster independently, not on the advertiser's account as a whole. A targeted campaign's signal disappears into page-wide noise.
2. **Search geographic proxies, not just place names** — tribal nations, river basins, regional utilities/regulators (e.g. "Arizona Corporation Commission"), metro areas, and known local landmarks in addition to the state name itself.
3. Do a monthly rank sweep of the state across the full page as a backstop — a launch month should show a visible rank jump even if it's not #1, which is the tell that something clustered exists worth isolating.

**Applies to:** any Meta Ad Library research task where the deliverable is "does Advertiser X target Region Y" — not just EDF, not just New Mexico.

---

## Generating a print-ready PDF from a report

**What happened:** A client asked for a report as a PDF. The first attempt ran full
Google Chrome headless with `--print-to-pdf --virtual-time-budget=25000
--run-all-compositor-stages-before-draw`. It hung past the 2-minute tool timeout and
leaked enough Chrome helper processes to exhaust the machine's process table — the
shell then could not `fork` at all (even `echo` returned exit 1), so `pkill` and
`killall` were also unavailable to clean it up. Recovery required the user quitting
Chrome from the GUI. A second attempt using a bounded recipe produced a correct
17-page PDF in **2 seconds**.

**Root causes:**
1. `--run-all-compositor-stages-before-draw` combined with `--virtual-time-budget`
   can wait forever. Don't use it for PDF export.
2. No watchdog — nothing killed the process when it stopped making progress.
3. The page loaded Chart.js, the annotation plugin, and Google Fonts from CDNs, so
   render completion depended on network round-trips inside the headless run.

**The working recipe:**
1. **Remove all network dependencies first.** Download Chart.js and any plugins, fetch
   the Google Fonts CSS with a browser User-Agent, keep only the `@font-face` blocks
   whose `unicode-range` covers latin (contains `U+0000` or `U+0100`), download those
   woff2 files, and base64-inline them as `data:font/woff2`. Assert that
   `cdn.jsdelivr.net`, `fonts.googleapis.com`, and `fonts.gstatic.com` all appear zero
   times in the final HTML before rendering.
2. **Set `Chart.defaults.animation = false`** in the report so charts paint
   synchronously rather than easing in over ~1s.
3. **Use `chrome-headless-shell`, not full Chrome.** Playwright's cache usually already
   has one: `~/Library/Caches/ms-playwright/chromium_headless_shell-*/chrome-headless-shell-mac-arm64/chrome-headless-shell`.
   Flags: `--headless --disable-gpu --disable-breakpad --disable-crash-reporter
   --no-first-run --disable-extensions --disable-dev-shm-usage --no-sandbox
   --user-data-dir=<fresh dir> --virtual-time-budget=12000 --no-pdf-header-footer
   --print-to-pdf=<out>`. Create the user-data-dir **before** launching.
4. **Always wrap it in a watchdog.** macOS has no `timeout`/`gtimeout` by default, so
   launch in the background, poll `kill -0 $PID` for N seconds, then
   `pkill -9 -P $PID; kill -9 $PID` if it is still alive. Never run headless Chrome
   unbounded from a tool call.
5. **Splice the inlined assets with literal string surgery, not `re.sub`** — minified JS
   contains backslashes that `re.sub` interprets as replacement-template escapes and
   throws `bad escape \s`. Find the match span and concatenate around it.

**Verifying the output — read the pages, don't just parse the bytes:**
- Page count, `/MediaBox` (`0 0 612 792` = US Letter), and `/Subtype /Image` count are
  cheap sanity checks, but a font-name regex is easy to get wrong and produced a false
  "fonts missing" alarm here. The ground truth is rendering the pages and looking at them.
- **Print CSS defects only appear in the PDF.** This build had two the on-screen view
  could never show: a CSS-grid stat block splitting mid-card across a page break, and
  four Chart.js annotation labels for closely-spaced events collapsing into an unreadable
  pile. Fixes: `break-inside: avoid` on every card/grid/table/row container, and for
  clustered annotations raise the axis `max` to create headroom then stagger the labels
  across rows with `position: 'end'` + increasing `yAdjust`.

**Applies to:** any request to deliver an HTML report or dashboard as a PDF.
