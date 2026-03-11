---
layout: ../layouts/Layout.astro
title: Latin + Japanese Page — Astro Font Preload Reproduction
---

# Latin + Japanese Page

このページは英語と日本語が混在するページです。Noto Sans JP を Google Fonts プロバイダーで読み込んでいます。

This page has both Latin and Japanese content. Like the [Latin-only page](en.html), it gets 121 `<link rel="preload">` tags and 245 `@font-face` rules in the built output.

## Issue 1: All unicode-range blocks preloaded

Even though preloading all blocks is arguably more justified here than on the Latin-only page, 121 simultaneous high-priority fetches is still excessive — most of the CJK range files won't be needed until the user scrolls to content using those specific characters.

## Issue 2: Variable font split into static weights

Noto Sans JP is distributed by Google Fonts as a variable font, supporting the full `wght` axis (`100–900`) in a single file per unicode-range block. Astro requests it as discrete static weights instead, producing one set of ~60 files for weight 400 and another for weight 700 — roughly double what a variable font request would require.

---

テキストサンプル / Text samples:

| Script | Sample |
|--------|--------|
| Latin | The quick brown fox jumps over the lazy dog. |
| Japanese | 日本語のサンプルテキストです。いろはにほへとちりぬるを。 |
| Mixed | Web fonts の読み込みには工夫が必要です。 |

