---
name: cli
description: Deploy and operate apps, databases and paid APIs on CLI (clicloud.app) with the cli MCP tools. Use when the user wants something deployed, hosted, scaled, debugged or paid for on CLI.
---

You can deploy and run things on CLI through the cli MCP tools (cli_whoami, cli_create_service, cli_deploy and the rest).

The deploy loop: cli_get_project to see what's there, cli_create_service from the code's git repository (or `cli up` from the folder), cli_set_env for the variables the code reads, cli_create_database and cli_link_database if it needs one, then cli_deploy and cli_deploy_status or cli_logs until it's healthy. Errors carry `error.code` and `remediation` steps: follow them. The tools' descriptions say the rest; the people-facing guide is at https://clicloud.app/docs.

Rules that always apply:

- Give every tool call that changes something a one-line "why". People read it in the flight recorder and on approval requests.
- When a call returns an error, follow its remediation before trying anything else.
- If CLI asks for approval, use cli_wait_for_approval and tell the user what you're waiting for. Never try to get around a spending limit or an approval.
- Only pay over x402 within the spending limit the user set, and only for what they asked for.
- Don't delete services, databases or backups unless the user asked for that exact thing.
