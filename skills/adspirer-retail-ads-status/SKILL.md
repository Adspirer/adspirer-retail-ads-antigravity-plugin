---
name: adspirer-retail-ads-status
description: "Show which Amazon Ads profiles and Walmart Connect advertisers are connected and active on Adspirer Retail Ads, and how much plan usage is left. Use when the user asks what is connected, whether a connection is healthy, or how much usage remains."
---

# Connection and usage status

Load adspirer-retail-ads-tools.

1. Call get_connections_status. Show a table: platform | profile or advertiser name and id |
   marketplace | active or not | connection health.
2. Call get_usage_status. Show tool calls used, the limit, the plan name and the reset date.
3. Point out anything that needs attention: an expired or failing connection, a platform that is
   not connected, no active account on a platform, or usage close to the limit.

If the connector is not signed in, tell the user to connect Adspirer Retail Ads (in Antigravity: open Customizations, then Installed, then MCP Servers, and choose Authenticate) and stop.

This skill only reads. To connect a platform, send the user to
https://adspirer.ai/connections. Switch or activate accounts only when the user asks and confirms
the exact accounts. Never buy, upgrade or renew a plan: if usage has run out, say so, link
https://www.adspirer.com/pricing and wait.
