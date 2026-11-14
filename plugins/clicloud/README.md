# CLI for Claude

CLI lets Claude deploy and run your apps, workers, databases, static sites and functions on
[CLI](https://clicloud.app). Claude can create services from a GitHub repository, set variables,
deploy, read logs and metrics, roll back, manage domains and backups, and check whether an app is
ready for real traffic. Changes are marked so Claude asks you before making them, and every change
is recorded in CLI with the reason Claude gave.

## Install

```
/plugin marketplace add clicloud-app/claude-plugins
/plugin install clicloud@clicloud
```

The first time Claude uses a tool, you sign in to CLI in your browser and approve the connection.
You can disconnect it any time under Settings → Connected apps in the CLI dashboard.

## What it runs, sends and fetches

- It runs nothing on your computer. It connects to CLI's MCP server at `https://api.clicloud.app/mcp` over HTTPS.
- Sign-in uses OAuth 2.1 with PKCE. CLI stores a hashed access token (one hour) and refresh token (30 days).
- It sends CLI only the tool arguments Claude passes (for example a service name, variables to set,
  or a SQL query you asked for), plus the one-sentence reason for each change. It never reads your
  conversation, Claude's memory or your files.
- It can't add credit, withdraw, buy domains, or move money or crypto. Do those in the dashboard.
- Data is kept as described in CLI's privacy policy: https://clicloud.app/privacy. CLI isn't meant for people under 18.

## Skills

- `clicloud`: how the tools fit together.
- `/clicloud:deploy`: deploy the current folder and fix it if it fails.

Support: support@clicloud.app · Docs: https://clicloud.app/docs/claude
