---
layout: ../layouts/Layout.astro
title: Astro v6 Font Component Sample
---

# Astro v6 Font Component Sample

This project demonstrates the **Font component** introduced in Astro v6. The `<Font />` component makes it easy to load web fonts with automatic performance optimizations — including preload links, optimized fallbacks, and local font caching.

## How it works

Fonts are configured in `astro.config.mjs` using the `fonts` option:

```js
import { defineConfig, fontProviders } from 'astro/config';

export default defineConfig({
  fonts: [
    {
      provider: fontProviders.google(),
      name: 'Noto Sans JP',
      cssVariable: '--font-noto-sans-jp',
      subsets: ['latin', 'japanese'],
    },
  ],
});
```

Then, in your layout's `<head>`, add the `<Font />` component:

```astro
---
import { Font } from 'astro:assets';
---
<head>
  <Font cssVariable="--font-noto-sans-jp" preload />
</head>
```

Finally, use the CSS variable in your styles:

```css
body {
  font-family: var(--font-noto-sans-jp), sans-serif;
}
```

## Pages in this sample

- [English page](en.html) — English-only content with Noto Sans JP
- [English + Japanese page](ja.html) — English and Japanese mixed content with Noto Sans JP
