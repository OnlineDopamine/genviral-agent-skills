---
name: genviral-setup
description: "Install and authenticate the Genviral CLI (npm package genviral) for an agent that runs commands in its own environment, such as Hermes, OpenClaw, NanoClaw, Paperclip or a Grok bot, or any server, container or CI job. Use when Genviral MCP tools are not available and the agent needs to call Genviral from a shell, or when the user asks to set up, connect or verify Genviral."
homepage: "https://www.npmjs.com/package/genviral"
metadata:
  openclaw:
    requires:
      bins:
        - node
    install:
      - package: "genviral"
        manager: node
---

# Genviral setup

Install the `genviral` CLI, give it a Genviral API key without exposing the key,
and verify the connection with a read that costs no credits.

If the agent's runtime can connect to a remote MCP server with OAuth, prefer that:
`https://mcp.genviral.io/mcp`. The steps below cover the CLI.

## 1. Check Node.js

```bash
node --version
```

If Node is missing, tell the user; do not change the system Node installation
without their approval.

## 2. Install the CLI

```bash
npm install -g genviral
genviral --version
```

If global installs are not allowed, run every command through npx:
`npx genviral@latest <command>`.

## 3. Get an API key

Ask the user to create a key on the API keys page of the Genviral dashboard
(https://www.genviral.io/api-keys). The key looks like `public_id.secret` and acts
on their Genviral account.

Ask the user to store the key themselves as `GENVIRAL_API_KEY` in the runtime's
secret or environment settings (the bot's environment variables, a container
secret or a CI secret). This keeps the key out of the conversation and the
agent's logs. Restart or reload the agent if the runtime needs it to see new
variables.

The CLI reads the key in this order: `--api-key`, then `GENVIRAL_API_KEY`, then
`GENVIRAL_API_KEY` in `~/.config/env/global.env`. If the runtime has no secret
settings, the user can add the line `GENVIRAL_API_KEY=...` to that file
themselves and run `chmod 600 ~/.config/env/global.env`.

Rules for the key:

- Never `echo` the key, print it, write it into a command line, commit it or
  include it in a reply. Avoid `--api-key` on shared hosts; it can appear in
  shell history and process lists.
- If the user pastes a key into the chat anyway, tell them it is now in the chat
  history, suggest they revoke it and store a new one as an environment variable,
  and do not repeat it.

## 4. Verify

```bash
genviral accounts
```

This lists the connected social accounts and costs no credits. A JSON list means
the key works. HTTP 401 means the key is missing, invalid or revoked.

## 5. Use it

```bash
genviral help                  # every command
genviral help create-post      # options for one command
genviral search-viral-library --help
```

Each command makes one Partner API request and prints JSON. Follow the `genviral`
skill for credits and the approval rules for publishing: `create-post` and
`commit-post` publish or schedule, so run them only after the user approves the
exact posts.
