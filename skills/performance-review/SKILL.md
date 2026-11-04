---
name: performance-review
description: "Review the user's own post performance in Genviral analytics: rank their best and worst posts over a period, compare platforms and formats, and name the patterns that separate winners from the rest. Use when the user asks how their posts did, what worked last week or month, which account or format performs best, or what to post next based on results."
---

# Performance review

Read the user's analytics for a period and explain what separates their best posts
from the rest. This only reads and costs no credits. Follow the `genviral` skill
for connecting.

## Prompt

> Use Genviral to read my post analytics for the last [30] days. Rank my five best and five worst posts by views in a table with platform, posting date, views, likes and link, then name the patterns that separate them. Use only numbers Genviral returned.

## Steps

1. `get_context` to confirm the workspace and accounts (CLI: `genviral accounts`).
2. `get_analytics` for the period (CLI: `genviral analytics-summary`, then
   `genviral analytics-posts`).
3. Rank by views, then compare format, hook, posting time and platform between
   the top and bottom groups.

## Output

- Totals for the period by platform.
- Best five and worst five posts with platform, date, views, likes and link.
- Two to four patterns, each with the posts that support it.
- One or two concrete next posts to try.

Posts from the last day or two may not have full numbers yet. Say which posts are
too new to judge instead of ranking them as poor performers.
