---
name: hirepulse-data-tools
description: Live business data for AI agents through eight pay-per-use Apify tools by HirePulse. Use when a task needs Google Jobs listings, a company's open jobs from its Greenhouse, Lever, Ashby, Workable, Recruitee or SmartRecruiters board, Google keyword search volume and CPC, domain SEO traffic and competitors, the Google ads a company runs by domain, YouTube transcripts in bulk, AliExpress search results with prices and units sold, or a hiring, ads and SEO intent check for a company domain. Not for LinkedIn, Workday, or AliExpress seller, shipping, review or stock data.
metadata:
  author: hirepulse
  version: "0.1"
---

# HirePulse data tools

Eight data tools that run on the Apify Store. They are pay per use, with no subscription. Higher Apify plans get volume discounts.

## Connect

Hosted MCP (nothing to install). Use the client's Apify sign-in, or send `Authorization: Bearer <APIFY_TOKEN>`:

```text
https://mcp.apify.com/?tools=hirepulse/google-ads-transparency-scraper
```

Several tools in one connection: separate them with commas, for example `?tools=hirepulse/google-jobs-scraper,hirepulse/ats-job-pulse`.

Claude Desktop, one tool, local command (put `APIFY_TOKEN` in the server's `env`):

```text
npx -y @apify/actors-mcp-server --tools hirepulse/<tool>
```

Never write the token into a file or a command line.

## Which tool to pick

| Need | Tool | Required input | Price |
| --- | --- | --- | --- |
| Jobs for a role in a country or city | `hirepulse/google-jobs-scraper` | `queries` | $0.005 per search that returns jobs + $0.001 per job |
| All open jobs of one company, from its domain | `hirepulse/ats-job-pulse` | `companies` | not stated here |
| Is this company hiring, advertising, growing in search? | `hirepulse/company-intent-radar` | `domains` | $0.03 per company report, charged only when the full report was produced |
| Google ads a company runs | `hirepulse/google-ads-transparency-scraper` | `domains` | $0.005 per domain + $0.0015 per ad |
| Search volume, CPC, keyword ideas | `hirepulse/keyword-search-volume` | `keywords` | $0.03 per lookup + $0.005 per keyword result |
| Organic traffic, ranking keywords, competitors of a site | `hirepulse/domain-seo-overview` | `domains` | not stated here |
| Transcripts of YouTube videos | `hirepulse/youtube-transcript-scraper` | `videos` | not stated here |
| AliExpress products for a keyword | `hirepulse/aliexpress-search-scraper` | `queries` | $2.50 per 1,000 products |

## What each tool returns, and when not to use it

- **Google Jobs Scraper.** Title, company, location, salary text (parsed to min and max when Google shows it), contract type, posting date, source site and apply link. Works in 90+ countries, for a whole country or one city with a radius (`location`, `radius_km`). Salary is often missing: in one test run of 30 US jobs, 5 showed a salary. Do not use it to read a company's own careers page; use the ATS tool.
- **ATS Job Scraper.** Every open job from the company's Greenhouse, Lever, Ashby, Workable, Recruitee or SmartRecruiters board. Pass a domain such as `stripe.com` or a board slug; the platform is detected automatically. Detects technologies mentioned in job titles and descriptions. Salary only where the company publishes it. Do not use it for companies on other systems.
- **Company Intent Radar.** One report per company domain: open jobs and new jobs in the last 30 days, Google ads running now and in total, organic traffic and SEO trend, email provider from MX records, a 0-100 intent score and a one-line summary. Use it to rank accounts. Do not use it when you need the full job list; use the ATS tool.
- **Google Ads Transparency Scraper.** For a domain: advertiser name and id, verified flag, ad format (text, image or video), first and last shown dates, preview image and Transparency Center link. `mode: "summary"` gives one row per domain. `only_new_ads` gives monitoring of new ads. Free Apify plan: 1 domain, up to 5 ads.
- **Keyword Search Volume.** Google monthly search volume, CPC, competition and keyword ideas. Free Apify plan: real data for the first 3 keywords of each run; that preview depends on availability and can be paused.
- **Domain SEO Overview.** Estimated organic traffic, ranking keywords, traffic value and competitor domains for any domain. The numbers are estimates.
- **YouTube Transcript Scraper.** Transcripts in bulk, with timestamps. Free Apify plan: the first 3 videos of each run.
- **AliExpress Search Scraper.** Per product: `product_id`, `title`, `url`, `image_url`, `price`, `original_price`, `discount_percent`, `currency`, `rating`, `sold`, `sold_text`, `is_sponsored`, `listed_since`, `ship_to`. You choose the currency and the ship-to country. 60 products per page. It does **not** return the store or seller name, shipping cost, delivery estimate, reviews or stock. Free Apify plan: 100 products per run.

## Rules for calling them

1. Start small: one query, one domain or a few keywords. Read the result, then scale up. Every result is billed.
2. Each tool takes arrays (`queries`, `domains`, `keywords`, `videos`, `companies`). Put several items in one call instead of making many calls.
3. Say which data is missing instead of guessing. For example, tell the user that AliExpress results have no seller name.
4. Report estimates as estimates (domain traffic and traffic value).
5. If a run returns nothing, say so, and check the input spelling before retrying. Retrying costs money.

## Links

- Store: https://apify.com/hirepulse
- Docs and live examples: https://edtool79-collab.github.io/hirepulse-tools/
