# Astro v6 Font Component Sample

A sample project demonstrating [Astro v6's Font component](https://docs.astro.build/en/guides/fonts/). It shows how to load web fonts via the `<Font />` component with automatic preload links, optimized fallbacks, and local font caching.

**Demo:** https://myakura.github.io/test--astro-v6-font-preloading/

## What's in this repo

- **Font configuration** — Noto Sans JP loaded from Google Fonts via `fontProviders.google()`, covering both Latin and Japanese character sets
- **Single layout** — `src/layouts/Layout.astro` includes `<Font cssVariable="--font-noto-sans-jp" preload />` in the `<head>`
- **Three Markdown pages:**
  - `/` — Top page explaining the Font API with code examples
  - `/en` — English-only content
  - `/ja` — English and Japanese mixed content

## Key files

```text
/
├── astro.config.mjs        ← Font configuration (Google Fonts, Noto Sans JP)
├── src/
│   ├── layouts/
│   │   └── Layout.astro    ← <Font /> component usage
│   └── pages/
│       ├── index.md
│       ├── en.md
│       └── ja.md
└── .github/workflows/
    └── deploy.yml          ← GitHub Pages deployment (Node.js 24)
```

## Commands

| Command           | Action                                      |
| :---------------- | :------------------------------------------ |
| `npm install`     | Install dependencies                        |
| `npm run dev`     | Start local dev server at `localhost:4321`  |
| `npm run build`   | Build production site to `./dist/`          |
| `npm run preview` | Preview build locally before deploying      |
