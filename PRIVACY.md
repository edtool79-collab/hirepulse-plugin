# Privacy

Last updated: 2026-10-16.

This plugin is a skill (text instructions) and a configuration file that points your client at Apify's hosted MCP endpoint, `https://mcp.apify.com`. It contains no program that runs on your computer, and it does not store anything.

## What happens when you use a tool

- Your client connects to Apify with your own Apify account (browser sign-in, or your Apify API token). The plugin does not ask for, store or send your token.
- The inputs you give a tool (for example a domain, a keyword, a search phrase or a video link) are sent to the HirePulse Actor on Apify. The Actor runs on Apify's platform, under your Apify account. Apify stores the run and its results in your account, under Apify's own privacy policy (https://apify.com/privacy-policy).
- Some tools get their data from a commercial data provider. For those tools, the input you give (such as a keyword or a domain) is passed on to that provider to produce the result.
- HirePulse, the maker of the Actors, receives the usage statistics that Apify shows to Actor developers, such as the number of runs and users. The Actors are not built to send your inputs or results to HirePulse.

## What this repository does not do

It does not collect analytics, set cookies or contact any server by itself.

## Questions

Open an issue at https://github.com/edtool79-collab/hirepulse-plugin/issues.
