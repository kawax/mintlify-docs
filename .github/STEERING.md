# Steering

このファイルは人間が編集し、「今後はこういうページを増やす」や「このページが間違ってるので修正」の細かい指示を出すためのものです。
対応が終わったら`[x]`で完了。
完了したタスクは削除。

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
- [x] Laravel CloudにManaged QueuesとScale to Zeroな新しいFlex コンピュートが追加 https://cloud.laravel.com/docs/changelog.md
  - これまでLaravel Cloudで若干不便だった休止中はタスクスケジュールやキューが動かない問題がScale to Zeroで解決したのでページを更新。blog/laravel-cloud、blog/laravel-cloud-hibernation
  - Managed Queuesはキューの実行頻度が低いなら得、5分ごとに実行するならAppコンピュートで動かす方が得、なはずだけどScale to Zeroと組み合わせるなら常にManaged Queuesを使うのが公式には推奨。
  - 料金プランも少し変わってスターターでも月5ドルで5ドル分のクレジット付き。5ドル以上使ってるなら変化はない。
  - 小規模なLaravelプロジェクトに多い、タスクスケジュールとキューで何らかの処理を自動実行している用途で使いやすくなった。
  - https://laravel.com/blog/your-laravel-cloud-stack-now-scales-to-zero
  - https://cloud.laravel.com/docs/scheduled-tasks.md
  - https://cloud.laravel.com/docs/queues.md

## packages ページ案
- [x] VOICEVOX Core for PHP
- [x] VOICEVOX for Laravel
- [x] Fetch metadata middleware for Laravel
- [x] Laravel FullFeed
- [x] Feedable
