---
name: deploy
description: Deploy the current project to CLI, watch it go live, and fix it if it fails
---

Deploy the project in the current folder to CLI with the cli MCP tools. Give every call a one-line "why".

1. Call cli_whoami to see which project the key belongs to, then cli_get_project to see what's already there.
2. Find the code's git remote (git remote get-url origin). If there's no app service for it yet, create one from that repo with cli_create_service; if the folder has no remote, ask the user to push it somewhere CLI can reach, or to run `cli up` from the folder.
3. Set the variables the code reads with cli_set_env. If it expects a database, add one with cli_create_database and connect it with cli_link_database.
4. Deploy with cli_deploy. If it fails, follow the error's remediation, read cli_logs, fix the cause, and deploy again. Stop after three failed tries and explain what's wrong.
5. When it's live, reply with the URL and what you set up. Never raise a spending limit or approve your own request.
