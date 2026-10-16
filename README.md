# HirePulse data tools for Claude Code

This plugin gives your agent eight pay-per-use data tools that run on the Apify Store, plus a skill that explains when to use each one. There is no subscription. You pay Apify per result, and the free Apify plan includes a small preview of several tools.

The tools:

- Google Jobs Scraper
- ATS Job Scraper (Greenhouse, Lever, Ashby, Workable, Recruitee, SmartRecruiters)
- Company Intent Radar
- Google Ads Transparency Scraper
- Keyword Search Volume
- Domain SEO Overview
- YouTube Transcript Scraper
- AliExpress Search Scraper

## Install

```bash
claude plugin marketplace add edtool79-collab/hirepulse-plugin
claude plugin install hirepulse@hirepulse-tools
```

The first time a tool is used, Claude Code opens a browser window to sign in to Apify. A free Apify account is enough to connect. The plugin never asks for, stores or sends a token itself.

## What it connects to

The plugin points at Apify's hosted MCP endpoint, filtered to the eight HirePulse tools: `https://mcp.apify.com/?tools=hirepulse/...`. Nothing else runs on your machine. The tools and their input fields are described in `skills/hirepulse-data-tools/SKILL.md`.

## Links

- Store: https://apify.com/hirepulse
- Docs and live examples: https://edtool79-collab.github.io/hirepulse-tools/

I am the maker of these tools.

License: MIT.
