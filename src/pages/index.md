---
layout: ../layouts/Layout.astro
title: Astro Font Preload — Reproduction
---

# Astro Font Preload: Excessive Preloads Reproduction

This site is a minimal reproduction for what appears to be a performance issue with Astro v6's `<Font preload />` component.

## Setup

Noto Sans JP is configured via the Google Fonts provider:

```js
fonts: [
  {
    provider: fontProviders.google(),
    name: 'Noto Sans JP',
    cssVariable: '--font-noto-sans-jp',
    weights: [400, 700],
    styles: ['normal'],
    subsets: ['latin', 'japanese'],
  },
],
```

The layout uses `<Font cssVariable="--font-noto-sans-jp" preload />` in the `<head>`.

## What to look at

View the page source of any page — 121 `<link rel="preload">` tags appear in every `<head>`, one per unicode-range font file. There are also 245 `@font-face` rules inlined in `<style>`.

Two issues seem to be causing this:

1. All unicode-range blocks are preloaded regardless of page content

The [Latin-only page](en.html) has no Japanese content, but still gets all 121 preloads including every CJK block. `preload` is a high-priority fetch hint — the browser will eagerly fetch all of them.

2. Variable fonts are split into static weights

Noto Sans JP is a variable font on Google Fonts, but Astro downloads separate files for each weight. With weights `400` and `700`, that's roughly 2× the files a variable font request would need.

## Pages

- [en.html](en.html) — Latin-only content; demonstrates issue 1
- [ja.html](ja.html) — Latin + Japanese content; demonstrates both issues
