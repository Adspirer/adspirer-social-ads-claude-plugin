---
description: Find Meta and TikTok ad spend that is not converting, such as campaigns, ad sets, placements and tired creatives, and propose fixes that are applied only after you approve.
argument-hint: "[platform] [period, e.g. last 30 days]"
---

# Wasted-spend review

Load adspirer-social-ads-tools and adspirer-social-ads-optimization.

Use the platform and period the user gave. With none given, cover every connected platform for
the last 30 complete days.

1. Call get_connections_status. Work only on connected platforms and their active accounts.
2. Meta, through meta_ads_read: run analyze_meta_wasted_spend and detect_meta_creative_fatigue.
   Use optimize_meta_placements when placements are part of the waste.
3. TikTok, through tiktok_ads_read: run analyze_tiktok_wasted_spend and
   detect_tiktok_creative_fatigue.
4. Separate items with spend and no results from items with a high cost per result. Do not call
   an item wasted when the sample is small, when it is still in the learning phase, when
   conversions are still arriving, or when the pixel looks broken.
5. Report the top items by spend with the evidence, and the total at stake per currency. For each
   one propose the smallest fix: a creative refresh, a placement or audience exclusion, a budget
   change, or a pause of the narrowest resource.
6. Stop and wait. Apply only the changes the user explicitly approves, through meta_ads_write or
   tiktok_ads_write, with confirm set only after that approval. Then read the changed resources
   back and report what was applied and anything the platform rejected.

Nothing is changed until the user approves a specific change.
