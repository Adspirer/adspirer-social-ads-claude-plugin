---
description: Read-only scorecard for your Meta (Facebook and Instagram) and TikTok campaigns, compared with the previous period, with the top problems and next actions.
argument-hint: "[platform] [period, e.g. last 7 days]"
---

# Social performance review

Load adspirer-social-ads-tools and adspirer-social-ads-performance.

Use the platform and period the user gave. With none given, cover every connected platform for
the last 30 complete days, compared with the 30 days before.

1. Call get_connections_status. Work only on connected platforms and their active accounts. If
   more than one account could be meant, ask which one.
2. Meta: call get_meta_campaign_performance. For the reason behind a change, run
   explain_meta_anomaly through meta_ads_read.
3. TikTok: through tiktok_ads_read, run get_tiktok_campaign_performance, and explain_tiktok_anomaly
   for the reason behind a change.
4. Show one scorecard per platform: spend, impressions, CPM, clicks, CTR, results, cost per
   result, ROAS where purchase value is tracked, frequency where available, and the change against
   the previous period. Keep currencies separate. Compute ratios from totals, not from averages
   of rows.
5. List the three findings that matter most, each with the campaign and the numbers behind it,
   then at most three recommended actions. When CTR is falling while frequency rises, check
   detect_meta_creative_fatigue or detect_tiktok_creative_fatigue before blaming targeting.
6. Say what limits the numbers: partial days, attribution windows, conversion lag, or pixel gaps.

This command changes nothing. If the user wants to act on a recommendation, describe the exact
change, wait for their approval, and follow adspirer-social-ads-optimization.
