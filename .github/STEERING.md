# Steering

このファイルは人間が編集し、「今後はこういうページを増やす」や「このページが間違ってるので修正」の細かい指示を出すためのものです。
対応が終わったら`[x]`で完了。

- [x] 重複ページを作り出してるのでここまでの完了したタスクを削除。公式ドキュメントを元にしたページは揃ってきた感じなので独自コンテンツを増やしていける段階。
  - 重複しても新しい情報があればプルリクの段階でページを統合して更新するように指示できるので「既存ページの再レビュー・改修」ができて問題ないかもしれない。

## 継続対応

- 新規ページ追加、翻訳ページ追加、既存ページの再レビュー・改修のタスクをバランスよくやっていく。`laravel/docs`はちょくちょく変更されてる。
- docs.jsonの`navigation`を全体を見て再配置。`config/`内に言語ごとに分割済み。ページを追加していくだけだと適切な分類ではなくなるのでたまに修正。
- ページ間リンクの追加。

## advanced ページ案

- パッケージ開発者向けのページを増やす。管理者は大量のパッケージを作ってきて知見があるのでいくらでもネタはある。パッケージを一度作って終わりではなくLaravel・PHPのバージョンアップに合わせてメンテナンスを年単位で継続できるようになるまでのガイドを提供する。
  - `package-versioning`が作られたけど今後もネタがあれば継続。
- [x] app-structureの下に旧構造から新構造への移行ガイドを追加
- [x] Laravel11以降の新構造のFAQページ

## blog ページ案

- https://github.com/laravel で公開された新しいリポジトリの調査。private状態で開発されてどこかのタイミングで公開される。大々的に発表されることもあるけどほとんどはドキュメントもなくリポジトリ内を見ないと何も分からない。バージョンは0.xで開発段階なことが多いのでblogで書くのは初期調査結果の情報。公式ドキュメントが公開されたら他で正式版のページを作成。
  - [x] maestro-introduction
  - [x] agent-skills-introduction
  - [x] laravel-ecosystem-analysis: surveyor, ranger, roster
  - [x] sentinel-introduction
  - [x] passkeys-introduction
  - [x] agent-detector PAOで使っているからこれも一緒に公式に移行されたのかも。
  - [x] pao-introduction
- [x] Laravel Cloud
  - 使っていくうちに新しい情報が入ったら後で追加。
  - [x] Hibernation
  - [x] Laravel Cloudはadvancedのページ案だったのに最初にblogで作られた後、Hibernationページがadvancedに作られて離れてしまった。blogに移動して統一。blogのProducts/プロダクトグループでLaravel公式の有料サービスを扱う。
- [x] Vueの紹介ページ
- [x] Reactの紹介ページ
- [x] Svelteの紹介ページ

## packages ページ案
- [x] Laravel Notification for Discord(Webhook)
- [x] Socialite for Discord
- [x] LINE SDK for Laravel
