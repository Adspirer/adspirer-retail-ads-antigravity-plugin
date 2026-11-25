---
name: adspirer-retail-ads-setup
description: "Connect Amazon Ads and Walmart Connect accounts and optionally establish an approved retail brand workspace. Use when the user asks what is connected, how to link a profile or advertiser, or sees a not-connected or auth error."
---

# Account setup

Load adspirer-retail-ads-tools. Let the user finish browser OAuth; never request credentials in chat.
Call get_connections_status, then use list_amazon_profiles or list_walmart_advertisers through the read routers when needed.
Resolve the intended profile/advertiser, marketplace and currency. Do not activate accounts without approval.
Direct connection questions to https://adspirer.ai/connections and current official docs. Walmart account connection can require granting Adspirer partner access and verifying an advertiser ID; do not describe every ad-platform connection as OAuth.

## Optional workspace

Do not require setup for a simple question. Read only user-designated brand/product files; never recursively ingest unrelated files or secrets.
With explicit permission, create or update BRAND.md and STRATEGY.md while preserving existing content. Ask before appending to unrelated files.
Record products/ASINs/SKUs/item IDs, voice and substantiated claims, margin assumptions, marketplace, inventory constraints, goals, approved budget and attribution conventions.
Keep observed spend separate from authorized future spend. Use actual read-only performance snapshots; mark missing data.
Create a private decision log only on request, never credentials or raw personal data.
Finish with connections, evidence, gaps and actual files saved, then resume the original request.

## First run

1. Call get_connections_status. If it fails because the connector is not signed in, tell the user
   to connect the Adspirer Retail Ads connector (in Antigravity: open Customizations, then Installed, then MCP Servers, and choose Authenticate), then stop and wait. Never ask for a password or token in chat.
2. List what is connected. Use list_amazon_profiles through amazon_ads_read and
   list_walmart_advertisers through walmart_ads_read to name each profile or advertiser with its
   marketplace and currency. Name the active one on each platform.
3. If a platform the user wants is missing, give them https://adspirer.ai/connections and wait.
   Walmart Connect can need partner access and an advertiser id rather than a sign-in. If several
   profiles exist and it is unclear which to use, ask. Activating or switching accounts changes
   the active set, so call activate_ad_accounts only after the user confirms the exact accounts.
4. Take a first look at the last 30 days on each connected platform:
   get_amazon_campaign_performance through amazon_ads_read for Amazon, and
   get_walmart_ad_group_performance through walmart_ads_read for Walmart. Skip a platform that is
   not connected; do not invent numbers for it.
5. Finish with a short summary: what is connected, what is not, spend, attributed sales, ACoS and
   ROAS for each platform, and what to try next: /adspirer-retail-ads-performance for a
   full scorecard or /adspirer-retail-ads-wasted-spend to find spend that is not converting.

A first run changes no campaign and creates no files. Build a brand workspace only if the user
asks for one.
