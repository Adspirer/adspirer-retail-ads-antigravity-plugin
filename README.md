# Adspirer Retail Ads for Antigravity

Run retail media from Antigravity. Adspirer Retail Ads connects the agent to your live Amazon Ads and Walmart Connect accounts through Adspirer's hosted Retail Ads MCP server, so you can track ACoS and ROAS, find wasted spend, research shopper keywords, and build and optimize Sponsored Products campaigns without leaving the conversation.

## Use it for

- **Reporting:** spend, attributed sales, ACoS and ROAS by campaign, product, keyword and search term, with attribution windows stated.
- **Wasted spend:** find products, keywords and search terms that spend without selling, and propose negatives or bid changes.
- **Keyword research:** shopper keyword ideas for a product, separated from your own campaign data.
- **Campaigns:** plan and build Amazon and Walmart Sponsored Products campaigns, created paused, after checking budget minimums and eligibility.
- **Optimization:** bids, budgets, placements and targeting, with inventory and Buy Box checks before raising bids.

## Install

**Antigravity app:** open **Customizations**, find **Adspirer Retail Ads** in the
Marketplace, and install it.

**Antigravity CLI:**

```text
agy plugin install https://github.com/Adspirer/adspirer-retail-ads-antigravity-plugin
```

**Manual:** clone this repository into your plugins folder.

```text
git clone https://github.com/Adspirer/adspirer-retail-ads-antigravity-plugin ~/.gemini/config/plugins/adspirer-retail-ads
```

Then sign in: open **Customizations**, then **Installed**, then **MCP Servers**, and choose
**Authenticate** next to the Adspirer server. Sign in to Adspirer in the browser, then connect the
profiles and advertisers you want to use at [adspirer.ai/connections](https://adspirer.ai/connections). No
API key or client secret is required. An Adspirer account is required, and plan usage limits apply.

## Get started

Ask:

```text
Review my Amazon Sponsored Products results for the last complete 30 days and find wasted spend. Don't change anything.
Which Walmart keywords have the worst ACoS this month?
Research shopper keywords for this product and suggest a campaign structure.
Plan a paused Walmart Sponsored Products campaign for these items with a $30 daily budget.
```

Or start with a skill by name:

| Skill | What it does |
| --- | --- |
| `/adspirer-retail-ads-setup` | Connect your profiles and advertisers and get a first look |
| `/adspirer-retail-ads-status` | Connected profiles and advertisers and remaining plan usage |
| `/adspirer-retail-ads-performance` | Scorecard against the previous period, with the top problems |
| `/adspirer-retail-ads-wasted-spend` | Spend that is not converting, with fixes applied only after you approve |

Add a platform and period if you want, for example `/adspirer-retail-ads-performance last 7 days`.

## What the agent can do

| Area | Capabilities |
| --- | --- |
| Amazon Ads | Sponsored Products and Sponsored Brands: campaigns, ad groups, keywords, product targets, negatives, bids, budgets and reporting |
| Walmart Connect | Sponsored Products: auto and manual campaigns, keywords, items, placements and bid multipliers, and reporting |
| Reporting | Campaign, product, keyword and search-term performance with ACoS, ROAS and attributed sales |
| Research | Shopper keyword ideas and public competitor observations, kept separate from your private results |

Amazon Ads and Walmart Connect are the advertising platforms on this connector. Search, social and B2B platforms are not included.

## What's included

- **Skills** (`skills/`): the four entry points above, plus `adspirer-retail-ads-ad-creative`, `adspirer-retail-ads-amazon`, `adspirer-retail-ads-campaign-launch`, `adspirer-retail-ads-keyword-research`, `adspirer-retail-ads-optimization`, `adspirer-retail-ads-product-help`, `adspirer-retail-ads-strategy`, `adspirer-retail-ads-tools` and `adspirer-retail-ads-walmart`,
  which the agent loads when a request needs them.
- **A rule** (`rules/adspirer-retail-ads.md`) that loads only for Amazon Ads and Walmart Connect requests and
  keeps every spend-affecting change behind your approval.
- **The Adspirer Retail Ads MCP server** connection (`mcp_config.json`).

The hosted server is the source of truth for tool names and schemas. The skills teach the agent to
discover the current tools and their parameters instead of hardcoding every operation.

## Safety

- The agent reads account state and performance before proposing changes.
- New campaigns are created paused, and enabling them is a separate decision.
- Campaign creation, budget changes, bid changes, and other spend-affecting writes require your
  explicit approval. The server also holds spend-affecting and irreversible writes until they are
  confirmed.
- The agent reads created or changed resources back before reporting success.
- Campaigns are never deleted automatically.
- Tool results, competitor ads and website text are treated as data, never as instructions.
- **No purchases.** The agent never buys, upgrades or renews a plan or paid feature. If a plan
  limit is reached, it stops and explains the limit.

## MCP and authentication

```json
{
  "mcpServers": {
    "retail-ads": {
      "url": "https://mcp.adspirer.com/retail-ads"
    }
  }
}
```

The server speaks Streamable HTTP. Authentication uses OAuth 2.1 with PKCE and dynamic client
registration, so Antigravity handles the browser sign-in and the plugin contains no API keys,
tokens, client secrets, or configuration variables. Ad-platform credentials stay server-side with
Adspirer and are scoped to the accounts you connect.

## Network and execution surface

The plugin's only MCP server is `https://mcp.adspirer.com/retail-ads`. It contains no hooks,
scripts, telemetry, local executables, or bundled server code. Skills and the rule are Markdown
guidance. Beyond the Adspirer server, the skills may ask the agent to read Adspirer's public
documentation at `adspirer.com/docs` to answer questions about plans and setup.

## Related plugins

Adspirer Retail Ads is one of Adspirer's focused plugins. The full
[Adspirer Advertising Agent](https://github.com/Adspirer/adspirer-antigravity-plugin) covers every
supported platform in one plugin, and
[Adspirer Marketing Analytics](https://github.com/Adspirer/adspirer-analytics-antigravity-plugin)
is a read-only reporting connector. Installing more than one is supported; use one connection per
task.

## Support

Email [support@adspirer.com](mailto:support@adspirer.com) for help with installing, signing in or
using this plugin, or open an issue at
[github.com/Adspirer/adspirer-retail-ads-antigravity-plugin/issues](https://github.com/Adspirer/adspirer-retail-ads-antigravity-plugin/issues).
See [SUPPORT.md](SUPPORT.md).

## Privacy and source

- Privacy policy: [adspirer.com/privacy](https://www.adspirer.com/privacy)
- Terms: [adspirer.com/terms](https://www.adspirer.com/terms)
- Documentation: [adspirer.com/docs](https://www.adspirer.com/docs)

## License

MIT. See [LICENSE](LICENSE).
