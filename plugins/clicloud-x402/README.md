# CLI Cloud (self-hosted, x402)

The full CLI toolset for Claude Code, run on your own machine. Besides deploying and running apps,
databases and paid APIs on [CLI](https://clicloud.app), it can pay over x402 in USDC: add credit to a
project, call paid APIs, and sell your own. Payments come from an agent wallet you fund, and never
exceed the spending limit you set when you install it.

## Install

```
/plugin marketplace add clicloud/claude-plugins
/plugin install clicloud-x402@clicloud
```

Claude Code asks for:

- **CLI API key** (required): make one in the dashboard under Connect an agent. It has its own role and spending cap.
- **Agent wallet private key** (optional): an EVM wallet holding only what you're willing for the agent to spend.
- **x402 spending limit** in USDC: 0 never pays.

The key and wallet are stored in your system's secure credential store, not in settings files.

## What it runs, sends and fetches

- It runs `npx -y @clicloud/mcp@<version>` (pinned in .mcp.json), which downloads that exact package from npm.
- The server talks to `https://api.clicloud.app` with your API key, and fetches the usage guide from `https://api.clicloud.app/skill.md`.
- With a wallet set, it signs x402 payments (USDC on Base or Solana) and sends them to CLI or to the
  paid API being called, up to your limit. The private key never leaves your machine.
- It never reads your conversation, Claude's memory or your files beyond what you ask Claude to deploy.

Support: support@clicloud.app · Docs: https://clicloud.app/docs/claude
