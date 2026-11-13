---
name: clicloud
description: Deploy and operate apps, databases, static sites and functions on CLI (clicloud.app) with the clicloud tools. Use when the user wants something deployed, hosted, scaled, monitored or debugged on CLI.
---

The clicloud tools manage the user's CLI account: projects, services (apps, workers, databases, static sites, functions), deploys, variables, domains, logs, metrics, backups and alerts.

How the tools are organised:

- Tools that only read are marked read-only. Tools that change something end in `_change` when the same area also has a read-only tool, and are marked destructive so Claude asks before running them.
- Every tool that changes something takes `why`: one sentence the user sees beside the change in CLI's flight recorder.
- Errors carry `error.code` and `remediation` steps. Follow the remediation, then retry.
- Some changes need a person's approval (the project's rules). The tool returns APPROVAL_REQUIRED; cli_wait_for_approval waits for the answer.
- Long jobs (deploys, backups, restores) answer within about 25 seconds. If the result says `stillRunning`, check again later with the tool it names in `next` (usually cli_deploy_status) instead of starting the job again.
- Domains on a service are one tool, `cli_service_domains` (list) and `cli_service_domains_change` (add, generate, rename, verify, remove); cron jobs are `cli_cron` and `cli_cron_change`.
- Credit, withdrawals, domain purchases and selling APIs are done in the CLI dashboard. This connector has no tools for them.
- Each connection has a daily spending limit and may be limited to some projects, both chosen by the user. SPEND_CAP_EXCEEDED or a FORBIDDEN that names the connection means the user can change the limits under Account → Connected apps in the CLI dashboard.

A typical deploy: cli_list_projects → cli_create_service (from a GitHub repo) → cli_set_env → cli_deploy → cli_deploy_status / cli_logs until it's healthy → reply with the URL.

To check an app is ready for real traffic, use cli_go_live.
