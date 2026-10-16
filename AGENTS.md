# HirePulse data tools: notes for coding agents

This repository holds a Claude Code plugin and a skill for eight pay-per-use data tools on the Apify Store (https://apify.com/hirepulse).

- Connect through Apify's hosted MCP endpoint: `https://mcp.apify.com/?tools=hirepulse/<tool>`. Several tools can be listed, separated by commas.
- Tool names: `aliexpress-search-scraper`, `google-ads-transparency-scraper`, `company-intent-radar`, `google-jobs-scraper`, `ats-job-pulse`, `keyword-search-volume`, `domain-seo-overview`, `youtube-transcript-scraper`.
- Which tool fits which task, the input fields and the limits: `skills/hirepulse-data-tools/SKILL.md`.
- Every result is billed. Start with one query, one domain or a few keywords, read the result, then scale up.
- Never write an Apify token into a file or a command line. Sign in through the client, or use the `APIFY_TOKEN` environment variable.
