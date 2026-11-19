---
description: Connect Meta Ads (Facebook and Instagram) and TikTok Ads to Adspirer, choose the accounts to work on, and get a first look at what is running.
---

# Set up Adspirer Social Ads

Load adspirer-social-ads-tools and adspirer-social-connect-ad-accounts.

1. Call get_connections_status. If it fails because the connector is not signed in, tell the user
   to connect the Adspirer Social Ads connector (in Claude Code: run /mcp, choose
   adspirer-social-ads and sign in), then stop and wait. Never ask for a password or token in chat.
2. List what is connected: Meta ad accounts and TikTok advertisers. Name the active account on
   each platform.
3. If a platform the user wants is missing, give them https://adspirer.ai/connections and wait.
   If several accounts exist and it is unclear which to use, ask. Activating or switching accounts
   changes the active set, so call activate_ad_accounts only after the user confirms the exact
   accounts.
4. Take a first look at the last 30 days on each connected platform: get_meta_campaign_performance
   for Meta, and get_tiktok_campaign_performance through tiktok_ads_read for TikTok. Skip a
   platform that is not connected; do not invent numbers for it.
5. Finish with a short summary: what is connected, what is not, spend, results and cost per
   result for each platform, and what to try next: /adspirer-social-ads:performance-review for a
   full scorecard or /adspirer-social-ads:wasted-spend to find spend that is not converting.

This command changes no campaign and creates no files. Build a brand workspace only if the user
asks for one.
