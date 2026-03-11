# Astro v6 Font Component: Excessive Preloads Reproduction

This repo is a minimal reproduction for what appears to be a performance issue with Astro v6's `<Font preload />` component.

## Setup

Noto Sans JP is configured via the Google Fonts provider with `subsets: ['latin', 'japanese']` and weights `400` and `700`:

```js
// astro.config.mjs
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

The layout adds `<Font cssVariable="--font-noto-sans-jp" preload />` in the `<head>`.

## The problem

Building this site produces **121 `<link rel="preload">` tags and 245 `@font-face` rules on every page** — including the Latin-only page. See the [built output](https://github.com/myakura/test--astro-v6-font-preloading/tree/main/dist) or the [live demo](https://myakura.github.io/test--astro-v6-font-preloading/).

Two issues compound each other:

1. **All unicode-range blocks are preloaded regardless of page content** — the Latin-only page (`en.html`) gets all 121 preloads including every CJK block it will never use.
2. **Variable fonts are downloaded as static weights** — Noto Sans JP is a variable font but Astro requests separate files per weight, roughly doubling the file count.

## Pages

- [index.html](index.html) — this page
- [en.html](en.html) — Latin-only content (but still gets 121 preloads)
- [ja.html](ja.html) — Latin + Japanese content (same 121 preloads; would benefit from variable font)

## Key files

```text
/
├── astro.config.mjs        ← Font configuration
├── src/layouts/Layout.astro ← <Font preload /> usage
└── dist/
    ├── en.html             ← 121 preloads on a Latin-only page
    └── ja.html             ← 121 preloads, 245 @font-face rules
```

