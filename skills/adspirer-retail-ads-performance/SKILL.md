---
name: adspirer-retail-ads-performance
description: "Review Amazon and Walmart spend, attributed sales, ACoS, ROAS, item performance and budget pacing without changing campaigns. Use when the user asks how their retail campaigns are performing or wants a weekly or monthly report."
---

# Read-only performance review

Load adspirer-retail-ads-tools and confirm account, marketplace, dates, timezone, currency, ad product and attribution window.
Amazon campaign/product/search-term/placement reports and Walmart keyword/item/ad-group/page-type/platform/video reports serve different scopes. Do not assume report parity.
Distinguish near-real-time Walmart stats from historical warehouse reports. Missing/stale data is not zero performance.
Use filters and bounded limits, not exhaustive billed pagination. Report whether displayed rows are a subset and whether summary totals cover the full filtered set.
Show spend, attributed sales, orders, ROAS, ACoS, CTR/CPC and pacing only where available. Compute ratios from comparable totals, not averages of row ratios.
Do not sum incompatible currencies or attribution windows, double-count overlapping reports, or present ad-attributed sales as incremental revenue.
Check stock, buybox and eligibility before attributing poor conversion solely to ads.
Lead with supported findings and uncertainties. Hand proposed actions to adspirer-retail-ads-optimization; this skill never changes resources.

## Default review

Use the platform and period the user gave. With none given, cover every connected platform for
the last 30 complete days, compared with the 30 days before.

1. Call get_connections_status. Work only on connected platforms and their active profile or
   advertiser. If more than one could be meant, ask which one.
2. Amazon, through amazon_ads_read: run get_amazon_campaign_performance and
   get_amazon_product_performance. When Seller Central data is connected, add
   get_amazon_combined_performance for total sales and TACoS.
3. Walmart, through walmart_ads_read: run get_walmart_ad_group_performance and
   get_walmart_ad_item_performance. Use get_walmart_out_of_budget for campaigns that capped out.
4. Show one scorecard per platform: spend, impressions, clicks, CTR, CPC, orders, attributed
   sales, ACoS, ROAS, and the change against the previous period. Keep marketplaces and currencies
   separate. Compute ratios from totals, not from averages of rows.
5. List the three findings that matter most, each with the campaign or product and the numbers
   behind it, then at most three recommended actions.
6. Say what limits the numbers: attribution windows, reporting lag, a row limit that shows only
   part of the data, or stock and buy box problems that ads cannot fix.

A review changes nothing. If the user wants to act on a recommendation, describe the exact
change, wait for their approval, and follow adspirer-retail-ads-optimization.
