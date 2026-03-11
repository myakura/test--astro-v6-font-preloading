---
layout: ../layouts/Layout.astro
title: English + Japanese Page — Astro Font Sample
---

# English + Japanese Page

このページは **Noto Sans JP**（Google Fonts）を `<Font />` コンポーネントで読み込んでいます。英語と日本語の両方をカバーするフォントなので、1つの設定で済みます。

The layout uses a single font for both scripts:

```astro
<Font cssVariable="--font-noto-sans-jp" preload />
```

CSSでは CSS変数を `font-family` に指定します:

```css
body {
  font-family: var(--font-noto-sans-jp), sans-serif;
}
```

## フォントについて / About the fonts

**Noto Sans JP** は Google が開発したフォントファミリーで、すべての言語で一貫した視覚的な品質を提供することを目的としています。名前の "Noto" は "no tofu"（豆腐なし）に由来し、文字が表示できない際に表示される □（通称「豆腐」）をなくすことを目指しています。

**Inter** is a typeface designed by Rasmus Andersson, optimized for screen reading. It pairs well with Japanese fonts due to its clean geometric forms and balanced proportions.

## Astro の Font API の利点 / Benefits of Astro's Font API

- **プライバシー**: フォントファイルを自サイトからホスト。Google Fonts 等の第三者サーバーへのリクエストが不要
- **パフォーマンス**: `preload` により重要フォントの優先読み込みが可能
- **型安全**: TypeScript による設定補完サポート
- **Caching**: Build time に fonts をダウンロード・キャッシュし、`_astro/fonts/` に配置

---

テキストの比較 / Text comparison:

| 言語 | サンプルテキスト |
|------|------------------|
| English | The quick brown fox jumps over the lazy dog. |
| 日本語 | 日本語のフォントサンプルです。いろはにほへとちりぬるを。 |
| Mixed | Web fonts make your site look great. Astro は高速です。 |
