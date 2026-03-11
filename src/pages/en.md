---
layout: ../layouts/Layout.astro
title: Latin-only Page — Astro Font Preload Reproduction
---

# Latin-only Page

This page contains only Latin text. It uses `<Font cssVariable="--font-noto-sans-jp" preload />` in the layout, same as every other page in this site.

Despite having no Japanese content, inspecting the `<head>` of the built `en.html` shows **121 `<link rel="preload">` tags** — one for every unicode-range file in the downloaded font set, including all CJK blocks this page will never render.

## Expected

Preload hints for the Latin unicode-range block(s) only, since that's all this page uses.

## Actual

All 121 font files preloaded unconditionally. `preload` is a high-priority fetch directive, so the browser will eagerly fetch all of these before they're needed — or needed at all.

---

The quick brown fox jumps over the lazy dog.

Typography is the art and technique of arranging type to make written language legible, readable, and appealing when displayed. Good typography creates a visual hierarchy that guides the reader through the content.

