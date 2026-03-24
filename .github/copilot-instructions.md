# Copilot instructions

Mintlifyを使ったLaravelのチュートリアルから高度な情報まで提供するドキュメントサイト。GitHub Agentic Workflowsを使って自動で更新し続ける。

This is a Mintlify documentation site. Pages are MDX files with YAML frontmatter. Site configuration lives in `docs.json`.

## 大事な制限

必ず公式の一次情報のみを参照する。

- https://github.com/laravel
- https://laravel.com/
- Laravelの最新バージョンのみを対象にする。モデルが持ってる知識は古いので必ず最新のドキュメントを参考にする。
- `.github/STEERING.md`の管理者からの指示には従う。

## 機能

- [Mintlify](https://www.mintlify.com/) によるドキュメントホスティング
- 多言語対応
- GitHub Agentic Workflowsによる自動更新

## ドキュメント構造

- 初級：基本的なチュートリアルとガイド
- 中級：[公式ドキュメント](https://github.com/laravel/docs) の範囲のガイド
- 上級：[GitHub](https://github.com/laravel) のコードまで見ないと分からない機能のガイド

## ディレクトリ構造

最初に言語別にディレクトリを分け（`jp/`、`en/`）、その中に同じ構成でmdxファイルを作成。ここで具体的な構成は決めずエージェントに任せる。

## Commands

- `mint dev` — local preview at `http://localhost:3000`
- `mint broken-links` — validate internal links
- `mint update` — update the CLI to latest version

There are no build, test, or lint commands beyond the above.

## Architecture

- `docs.json` — central config: navigation structure, theme, logos, navbar, footer, and anchors. Every new page must be added to the `navigation` section here or it won't appear in the site.
- `snippets/` — reusable MDX fragments imported into other pages with `<Snippet file="snippet-intro.mdx" />`.
- `api-reference/openapi.json` — OpenAPI 3.1 spec that auto-generates the API reference pages.
- `images/` and `logo/` — static assets referenced from MDX pages and `docs.json`.
- `.mintignore` — files excluded from the Mintlify build (similar to `.gitignore` syntax). `drafts/`[copilot-instructions.md](copilot-instructions.md) and `*.draft.mdx` are ignored.

## Writing conventions

- Use active voice and second person ("you").
- One idea per sentence.
- Sentence case for headings.
- Bold for UI elements: Click **Settings**.
- Inline code for file names, commands, paths, and code references.
- Lead with the goal in instructions — start with what the user wants to accomplish.

## Page structure

Every MDX page starts with YAML frontmatter containing at least `title` and `description`:

```mdx
---
title: "Page title"
description: "Brief description for SEO and navigation"
---
```

## Mintlify components

Pages use Mintlify's built-in MDX components. Common ones in this repo:

- `<Card>`, `<Columns>` — layout and navigation cards
- `<Steps>`, `<Step>` — numbered step sequences
- `<Info>`, `<Warning>`, `<Tip>` — callout boxes
- `<Frame>` — image wrapper with styling
- `<Accordion>`, `<AccordionGroup>` — collapsible sections
- `<Snippet>` — include reusable content from `snippets/`

Do not use raw HTML for layout when a Mintlify component exists.

## Adding a new page

1. Create an MDX file with frontmatter (`title`, `description`).
2. Add the page path (without `.mdx` extension) to the appropriate group in `docs.json` under `navigation.tabs[].groups[].pages`.
3. Verify with `mint dev` and `mint broken-links`.
