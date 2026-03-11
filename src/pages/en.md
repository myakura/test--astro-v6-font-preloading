---
layout: ../layouts/Layout.astro
title: English Page — Astro Font Sample
---

# English Page

This page uses the **Noto Sans JP** font loaded via Astro's `<Font />` component with the Google Fonts provider.

The layout includes `<Font cssVariable="--font-noto-sans-jp" preload />` in the `<head>`. Astro downloads and caches the font file at build time, then serves it from your own origin — no requests to third-party servers at runtime.

## The quick brown fox

Typography is the art and technique of arranging type to make written language legible, readable, and appealing when displayed. The arrangement of type involves selecting typefaces, point sizes, line lengths, line spacing, and letter spacing.

Good typography creates a visual hierarchy that guides the reader through the content. It sets the tone and personality of a piece, communicates mood, and affects how easily text can be read.

## Why Noto Sans JP for English too?

Noto Sans JP includes Latin character coverage alongside Japanese glyphs, making it a great single-font choice for multilingual sites. Using one font family keeps the configuration simple and ensures visual consistency across languages.

- Designed by Google
- Open source (SIL Open Font License)
- Available via [Google Fonts](https://fonts.google.com/noto/specimen/Noto+Sans+JP)
