# Steering

このファイルは人間が編集し、「今後はこういうページを増やす」や「このページが間違ってるので修正」の細かい指示を出すためのものです。
対応が終わったら`[x]`で完了。
完了したタスクは削除。

このファイルはAWからは変更できないのでプルリクには含めない。

公式ドキュメントを元にしたページは揃ってきた感じなので独自コンテンツを増やしていける段階。

## 継続対応

- 新規ページ追加、翻訳ページ追加、既存ページの再レビュー・改修のタスクをバランスよくやっていく。`laravel/docs`はちょくちょく変更されてる。
- docs.jsonの`navigation`を全体を見て再配置。`config/`内に言語ごとに分割済み。ページを追加していくだけだと適切な分類ではなくなるのでたまに修正。
- ページ間リンクの追加。

## チュートリアル・ガイド ページ案

STEERING.mdのタスクがない時はまだページが増えてるのでここにも案を追加。

- 公式ドキュメントベースではない独自ページをチュートリアル・ガイドレベルでも追加。ドキュメントの一セクションで説明されてるけど個別ページで分かりやすい解説があるといい内容が対象。
- 絶対に扱う気がないのはMVCやDDD(ドメイン駆動開発)。
- チュートリアルとガイドのページの分類を調整。「パスワードリセット」はガイドに移動、「ヘルパーとコレクションやHTTPクライアント」はよく使うのでチュートリアルに移動、などチュートリアルは最初から必ず知っておきたいこと。

## advanced ページ案

- パッケージ開発者向けのページを増やす。管理者は大量のパッケージを作ってきて知見があるのでいくらでもネタはある。パッケージを一度作って終わりではなくLaravel・PHPのバージョンアップに合わせてメンテナンスを年単位で継続できるようになるまでのガイドを提供する。
  - `package-versioning`が作られたけど今後もネタがあれば継続。
- [x] Fortifyページ
- [x] スターターキットの作り方ページ
- [x] Reflectionの解説
- [x] Laravel Chiselページで少し出てきたのでPHP AST（抽象構文木）の解説
- [x] FFIの解説
- [ ] パッケージ開発グループにGitHub Actionsのピン留めページを追加
  - サプライチェーン攻撃対策
  - 最近、Laravel公式でも行っているのでパッケージ開発者も追従すべきだろう。
  - 1、プロジェクトにdependabot.ymlを追加。Laravelと同じファイルをそのままコピーでいい。 https://github.com/laravel/laravel/blob/13.x/.github/dependabot.yml
  - 2、初回のピン留めはpinactなどのツールを使用する。 https://github.com/suzuki-shunsuke/pinact
  - dependabotはピン留めしてなければバージョンで更新、ピン留めしていればSHAで更新する。最初に設定さえ済ませば自動で更新のPRが作られる。

## blog ページ案

- https://github.com/laravel で公開された新しいリポジトリの調査。「新リポジトリ調査」グループ。private状態で開発されてどこかのタイミングで公開される。大々的に発表されることもあるけどほとんどはドキュメントもなくリポジトリ内を見ないと何も分からない。バージョンは0.xで開発段階なことが多いのでblogで書くのは初期調査結果の情報。公式ドキュメントが公開されたら他で正式版のページを作成。
  - [x] maestro-introduction
  - [x] agent-skills-introduction
  - [x] laravel-ecosystem-analysis: surveyor, ranger, roster
  - [x] sentinel-introduction
  - [x] passkeys-introduction
  - [x] agent-detector PAOで使っているからこれも一緒に公式に移行されたのかも。
  - [x] pao-introduction
  - [x] chisel-introduction。moatはLaravelとは直接関係ないのでページは不要。
  - [x] Laravel LSP

## packages ページ案
- [x] VOICEVOX Core for PHP
- [x] VOICEVOX for Laravel
- [x] Fetch metadata middleware for Laravel
- [x] Laravel FullFeed
- [x] Feedable
