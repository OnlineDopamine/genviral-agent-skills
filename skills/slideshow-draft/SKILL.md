---
name: slideshow-draft
description: "Draft a TikTok or Instagram slideshow in Genviral, modelled on a proven Viral Library slideshow or built from the user's own copy and images, and leave it as an editable draft. Use when the user asks to make, write or generate a slideshow or carousel, recreate a viral slideshow, or turn a format into a post."
---

# Slideshow draft

Turn a proven format or the user's own content into an editable slideshow draft.
AI generation uses credits; publishing needs separate approval. Follow the `genviral`
skill for connecting and the approval rules.

## Prompt

> Use Genviral to draft a [6]-slide TikTok slideshow about [TOPIC], modelled on one high-performing Viral Library slideshow. Show me the reference post and the slide text first and wait for my go-ahead. Tell me the credit cost before anything that uses credits, and never publish or schedule without my approval.

## Choose the path

- **The user supplies the copy, images or brand rules:** build from them as given
  with `manage_slideshow` (create). Find extra photos with `search_images`, which
  is free, and write slide text that matches what each image shows. Do not search
  the Viral Library.
- **The user asks Genviral to write it:** pick one slideshow reference with
  `search_viral_library` (`content_type: "slideshow"`), show it, and generate with
  `generate_slideshow`. Say first that AI generation uses credits.

## Steps

1. Show the reference post (or the user's material) and the slide text. Wait for
   the user's go-ahead.
2. Run `manage_slideshow` validate with the same body and fix any text overflow it
   reports.
3. Create the deck with an `idempotency_key`. If the result is unclear, repeat with
   the same key or read the deck back.
4. Render the deck and share the contact sheet so the user can check every slide
   at once.
5. Stop at the draft. Create a post or schedule it only when the user asks for the
   exact accounts and time.

Defaults: TikTok decks are 9:16, others 4:5. Pick fonts from `get_context`.
