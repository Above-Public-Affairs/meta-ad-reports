# Lessons

## Regional targeting analysis: cluster by creative before checking geography

**What happened:** A client asked whether EDF was running ads targeting New Mexico. Our system averaged ad delivery across EDF's entire account (2,691 ads/463 clusters over ~20 months) and concluded there was no NM-specific targeting. The client then sent a screenshot of an EDF ad they'd seen — a live, NM-targeted "Cut methane on the Navajo Nation" campaign (8 ads, $3.5K–$5K spend, New Mexico reached by 8 of 8 ads). Re-checking confirmed it was real and had been missed.

**Root cause:** Page-level regional breakdowns average across everything an advertiser runs. EDF posts ~250 national fundraising ads/month; an 8-ad state-specific campaign is statistically invisible in that average — it never cracked New Mexico into the top 8 regions except in the exact month it launched, and even then only barely. Compounding this: the campaign's creative said "Navajo Nation," not "New Mexico," so a keyword search on the state name also missed it.

**Fix — always do both when checking if an advertiser targets a place:**
1. **Cluster ads by creative/campaign first**, then run the regional breakdown on each cluster independently, not on the advertiser's account as a whole. A targeted campaign's signal disappears into page-wide noise.
2. **Search geographic proxies, not just place names** — tribal nations, river basins, regional utilities/regulators (e.g. "Arizona Corporation Commission"), metro areas, and known local landmarks in addition to the state name itself.
3. Do a monthly rank sweep of the state across the full page as a backstop — a launch month should show a visible rank jump even if it's not #1, which is the tell that something clustered exists worth isolating.

**Applies to:** any Meta Ad Library research task where the deliverable is "does Advertiser X target Region Y" — not just EDF, not just New Mexico.
