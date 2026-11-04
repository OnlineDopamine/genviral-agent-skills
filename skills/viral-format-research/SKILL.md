---
name: viral-format-research
description: "Find proven TikTok and Instagram formats for a niche in the Genviral Viral Library: search slideshows or videos about a topic, rank them by views, and explain the hooks, structure and visuals they share. Use when the user asks what works in their niche, wants hook ideas, viral examples, a format to copy, or inspiration before drafting content."
---

# Viral format research

Search the Viral Library for a topic and explain what the winners have in common.
This only reads; it generates nothing and costs no credits. Follow the `genviral`
skill for connecting.

## Prompt

> Use Genviral to search the Viral Library for [slideshow | video] posts about [TOPIC]. List the five with the most views in a table with hook, views, likes, creator and link, then explain what their hooks have in common. Only read; do not generate anything.

## Steps

1. Call `search_viral_library` (CLI: `genviral search-viral-library`) with the
   topic. Pass `content_type: "slideshow"` when the user wants a slideshow to
   copy; only slideshow posts can be recreated as slideshows.
2. Rank the results by views. Read one or two with `analyze_content` or the
   transcript only if the user wants the structure in detail.
3. Group what repeats: hook pattern, slide count, text placement, image style,
   call to action.

## Output

- A table of the top posts with hook, views, likes, creator and link.
- Three to five shared patterns, each tied to the posts that show it.
- One suggested format to model, with the reference post.

In clients that show widgets, the search shows the posts as cards. Do not repeat
them as a second table; add a short note on what stands out.
