---
name: cli
description: Deploy and operate apps, databases and paid APIs on CLI (clicloud.app) with the cli MCP tools. Use when the user wants something deployed, hosted, scaled, debugged or paid for on CLI.
---

You can deploy and run things on CLI through the cli MCP tools (cli_whoami, cli_create_service, cli_deploy and the rest).

Before your first change in a session, read the full guide your CLI server serves at /skill.md (CLI_API_URL, by default https://api.clicloud.app/skill.md). It covers the deploy loop, funding, guardrails, and what to do for every error code.

Rules that always apply:

- Give every tool call that changes something a one-line "why". People read it in the flight recorder and on approval requests.
- When a call returns an error, follow its remediation before trying anything else.
- If CLI asks for approval, use cli_wait_for_approval and tell the user what you're waiting for. Never try to get around a spending limit or an approval.
- Only pay over x402 within the spending limit the user set, and only for what they asked for.
- Don't delete services, databases or backups unless the user asked for that exact thing.
