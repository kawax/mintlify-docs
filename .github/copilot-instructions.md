# Copilot instructions

Mintlifyを使ったLaravelのチュートリアルから高度な情報まで提供するドキュメントサイト。GitHub Agentic Workflowsを使って自動で更新し続ける。

This is a Mintlify documentation site. Pages are MDX files with YAML frontmatter. Site configuration lives in `docs.json`.

## 大事な制限

必ず公式の一次情報のみを参照する。

- https://github.com/laravel
- https://laravel.com/
- Laravelの最新バージョンのみを対象にする。モデルが持ってる知識は古いので必ず最新のドキュメントを参考にする。
- `.github/STEERING.md`の管理者からの指示には従う。

## 現在の最新バージョン

- Laravel 13
- Livewire 4
- Inertia 3

### バージョン取得方法

GitHub MCPでGitHubリポジトリのリリース情報を取得して調べる。

- https://github.com/laravel/framework
- https://github.com/livewire/livewire
- https://github.com/inertiajs/inertia

## 公式ドキュメント

- 公式ドキュメントは https://github.com/laravel/docs のMarkdownを直接参照する。デフォルトブランチが最新バージョン。`master`ブランチは次期バージョン用だけどリリース直前にならないと更新されないので参照しない。各ブランチにバージョン4.0以降のすべてのドキュメントが残っている。例外は https://laravel.com/docs/changelog のChangelog、Markdownはなく、月に一度程度更新されて重要な変更点がまとめられている。
- Laravel Cloudのドキュメント https://cloud.laravel.com/docs/intro ここもMintlifyなのでURL末尾に`.md`を付ければMarkdownで取得できるなど同じ機能が使える。
- 公式ブログ https://laravel.com/blog 最近は以前よりも頻繁に更新されている。
- https://github.com/livewire/livewire Livewireはリポジトリ内の`docs`に最新ドキュメント。
- https://fluxui.dev/docs/installation
- https://github.com/inertiajs/docs Inertiaは個別のdocsリポジトリ。ここもMintlify。v1,v2,v3ディレクトリがありデフォルトブランチに全バージョンのドキュメントが残っている。

## 機能

- [Mintlify](https://www.mintlify.com/) によるドキュメントホスティング
- 多言語対応
- GitHub Agentic Workflowsによる自動更新

## ドキュメント構造

- 初級（チュートリアル/Tutorial）：基本的なチュートリアルとガイド。https://laravel.com/docs のGetting StartedやThe Basics、Eloquent: Getting Started辺りが初級。残りは中級の範囲。
- 中級（ガイド/Guide）：[公式ドキュメント](https://github.com/laravel/docs) の範囲のガイド
- 上級（応用トピック/Advanced Topics）：[GitHub](https://github.com/laravel) のコードまで見ないと分からない機能のガイド。フレームワーク本体だけでなく公式パッケージも対象。
- ブログ：機能ごとに分けられない記事。
  - `laravel/docs`に過去のアップグレード情報が残っているので古いバージョンのアップグレードガイドも作成できる。5.0->5.1、5.1->5.2など。
  - Laravelを長く使っているシニアエンジニアはチュートリアルのような素朴な使い方はしなくなってるのでドキュメント以上の内容を扱う。
- マイパッケージ/My packages：管理者が開発してるパッケージの解説ページ。専用のドキュメントサイトは作ってないのでここで一緒に入れる。ファイルは`jp/packages/`に作る。Mintlifyのテーマを変更してカテゴリーを増やしても見やすくなったので独立したカテゴリーにする。ブログの後ろに配置。

## ディレクトリ構造

- 最初に言語別にディレクトリを分け（`jp/`、`en/`など）、その中に同じ構成でmdxファイルを作成。ここで具体的な構成は決めずエージェントに任せる。
- とはいえディレクトリ構造はURLとして永続するので最低限のルールは必要。ドキュメントを元にした初級・中級は言語別ディレクトリ直下(`jp/introduction`)、上級は`jp/advanced/`、ブログは`jp/blog/`、パッケージは`jp/packages/`。
- 言語別に完全に分かれているのでドキュメントを元にしたページは同じページを作るけど、ブログは同じ内容にしなくていいしページ自体がなくてもいい。
- プロジェクトルートの`index.mdx`は言語別に主なページへのリンク
- `index.mdx`は他のサブディレクトリでも有効。`jp/packages/laravel-copilot-sdk`のURLを表示した時は`jp/packages/laravel-copilot-sdk/index.mdx`が使われるので別途`jp/packages/laravel-copilot-sdk.mdx`を作る必要はない。

## Languages

管理者がレビューできる日本語をプライマリーにする。英語はセカンダリー。その他の言語は可能なら追加。

Mintlifyの対応言語：https://www.mintlify.com/docs/organize/navigation#languages

## Commands

- `mint dev` — local preview at `http://localhost:3000`
- `mint broken-links` — validate internal links
- `mint validate` — validate MDX syntax and docs.json configuration
- `mint update` — update the CLI to latest version

`mint broken-links`での`/llms.txt`エラーは無視していい。
index.mdxへの`warning - "jp/packages/laravel-copilot-sdk" is referenced in the docs.json navigation but the file does not exist.`エラーは無視していい。

Playwright MCPでスクリーンショットを撮ってプルリクに添付。

## Architecture

- `docs.json` — central config: navigation structure, theme, logos, navbar, footer, and anchors. Every new page must be added to the `navigation` section here or it won't appear in the site.
- `snippets/` — reusable MDX fragments imported into other pages with `<Snippet file="snippet-intro.mdx" />`.
- `images/` and `logo/` — static assets referenced from MDX pages and `docs.json`.
- `.mintignore` — files excluded from the Mintlify build (similar to `.gitignore` syntax). `drafts/`[copilot-instructions.md](copilot-instructions.md) and `*.draft.mdx` are ignored.

## docs.json

ページが増えてきたので`$ref`を使って`navigation`を分割。言語ごとのページはそれぞれのファイルに記載。もっとページが増えたらここからさらに分割。

- config/navigation-jp.json
- config/navigation-en.json

新しいページは基本的にはグループの一番下に追加。

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
- `<Tree>`、`<Tree.Folder>`、`<Tree.File>` — file tree display
- `<Snippet>` — include reusable content from `snippets/`

https://www.mintlify.com/docs/components/index

Do not use raw HTML for layout when a Mintlify component exists.

## Mermaid

公式ドキュメントではフローチャートなどは使われていないので公式よりも理解しやすくなる要素として使うと効果的な箇所ではMermaidでの図解を積極的に入れていく。

- Mermaid内での改行は`\n`ではなく`<br>`で行う。`\n`では改行されない。日本語の場合はダブルクォーテーションで囲むとより確実。`["ここで<br>改行"]`
- ただし`erDiagram`では`<br>`でも`\n`でも改行できてない。GitHub上では改行される。Mintlifyでは改行されない。表示方法の違いなのか動作に違いがあるので`erDiagram`では改行を避ける。
- `sequenceDiagram`では`participant App as Laravel<br>アプリ`としてダブルクォーテーションで囲まない。`<br>`で改行される。

## Adding a new page

1. Create an MDX file with frontmatter (`title`, `description`).
2. Add the page path (without `.mdx` extension) to the appropriate group in `docs.json` under `navigation.tabs[].groups[].pages`.
3. Verify with `mint dev` and `mint broken-links`.

## デプロイ

mainブランチへのマージ後にMintlifyダッシュボードで管理者が手動デプロイする。
