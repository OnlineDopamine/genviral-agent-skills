# Genviral Agent Skills

Agent skills for [Genviral](https://www.genviral.io), the social media workspace
that finds proven formats, drafts slideshows and videos, schedules posts and reads
analytics. The skills teach an AI agent to connect to Genviral through its hosted
MCP server or CLI, pick the right tool, keep track of credits and ask before it
publishes anything.

They work with Claude Code, Cursor, Codex, OpenCode, Gemini CLI and other agents
that load `SKILL.md` files.

## Installation

### Option 1: npx

```bash
# Install all skills
npx skills add OnlineDopamine/genviral-agent-skills

# Install one skill
npx skills add OnlineDopamine/genviral-agent-skills --skill genviral

# List available skills
npx skills add OnlineDopamine/genviral-agent-skills --list
```

The skills do not connect your agent to Genviral on their own. Connect the
[MCP server](https://www.genviral.io/mcp) in your client, or install the CLI with
the `genviral-setup` skill.

### Option 2: Claude Code plugin

The plugin installs every skill and adds the hosted Genviral MCP server
(`https://mcp.genviral.io/anthropic/mcp`).

```bash
/plugin marketplace add OnlineDopamine/genviral-agent-skills
/plugin install genviral@genviral
```

Then open `/mcp`, select the Genviral server and sign in to your Genviral account
in the browser.

### Option 3: Direct link

Give any agent the raw URL of a skill:

```
Load and follow the instructions from:
https://raw.githubusercontent.com/OnlineDopamine/genviral-agent-skills/main/skills/genviral/SKILL.md
```

## Available skills

| Skill | What it does |
| --- | --- |
| `genviral` | Connect through MCP or the CLI, find the right tool, track credits and follow the approval rules for publishing |
| `genviral-setup` | Install the `genviral` CLI and authenticate it with an API key in agents that run in their own environment (Hermes, OpenClaw, NanoClaw, Paperclip, Grok bots, servers, CI) |
| `viral-format-research` | Find the most-viewed Viral Library posts for a topic and explain the hooks and formats they share |
| `performance-review` | Rank your best and worst posts for a period and name what separates them |
| `slideshow-draft` | Draft a slideshow from a proven format or your own content and stop at an editable draft |

Example prompts:

```
"What slideshow hooks work best for skincare on TikTok?"
"Which of my posts did best last month, and why?"
"Draft a 6-slide slideshow about morning routines, but don't post it."
```

## Requirements

- A Genviral account with connected social accounts. MCP clients sign in in the
  browser; the CLI needs an API key from https://www.genviral.io/api-keys.
- Reading accounts, posts, the Viral Library and analytics is free. AI generation
  (AI-written slideshows, AI slide images, Studio images and videos) uses credits
  from your plan.
- For the CLI: Node.js.

Genviral never needs your social media passwords. The skills tell agents never to
ask for them, never to put an API key in a prompt or tool argument, and never to
publish or schedule without your approval.

## Repository structure

```
genviral-agent-skills/
├── .claude-plugin/
│   ├── marketplace.json      # Claude Code marketplace
│   └── plugin.json           # Claude Code plugin manifest
├── .mcp.json                 # Hosted Genviral MCP server (HTTP)
└── skills/
    ├── genviral/                 # Main skill
    ├── genviral-setup/           # CLI install and authentication
    ├── viral-format-research/    # Recipe
    ├── performance-review/       # Recipe
    └── slideshow-draft/          # Recipe
```

## Documentation

- MCP server: https://www.genviral.io/mcp
- Docs and Partner API: https://docs.genviral.io
- CLI: https://www.npmjs.com/package/genviral

## License

[MIT](./LICENSE)
