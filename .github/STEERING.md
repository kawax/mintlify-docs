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

## packages ページ案
- [x] Laravel Notification for Discord(Webhook)
- [x] Socialite for Discord
- [x] LINE SDK for Laravel
- [x] VOICEVOX Core for PHP https://github.com/invokable/voicevox-core-php
  - 日本語のテキスト音声合成、歌声合成ソフトウェア、VOICEVOXのCOREをFFIでラップしたPure PHP用パッケージ。
  - README.mdが英語、README_jp.mdが日本語。VOICEVOX COREの動的ライブラリのダウンロードからAPIリファレンスまで一通り説明しているのでこれでページを作れる。
  - Laravel版を先に別パッケージで作ってたけど技術的に実現不可能な箇所が多いのでまだ開発中。PHP版コアは完成しているので先にページを作成。
  - 「AI SDK」グループと「スターターキット」の間にVOICEVOXグループを追加。
  - FFIの解説は別ページ。
  - 日本語ページはOK
- [ ] VOICEVOX for Laravel https://github.com/invokable/laravel-voicevox
  - Laravel版も主要な機能はほぼ完成してきたのでページを作成していく。先に日本語ページから、というかそもそも日本語のTTSなので。
  - README_jp.mdとdocs/jp内が日本語のドキュメント。
  - まずはインストールと設定からモードごとのトークとソングの生成までを説明。
  - tap()を上手く使えている。使いどころが難しいtapだけどこういう場面ではバッチリ決まる。advanced/tapページからも活用例としてリンク。
  - docs/jp内は更新中なのでしばらくは新しいファイルが増えていたらこちらにも追加の対応。
  - 英語のREADME.mdを更新したのでこちらにも英語ページを作成。英語版なのでVOICEVOXが日本語のテキスト音声合成なことや日本で一番有名なずんだもんボイスはVOICEVOXで多く作られていることを追加している。
  - 英語ページはこちらで作るので不要だったのに`docs/en/`に1ファイルだけ作られている。ai-sdk.mdのエイリアス一覧はこちらにも追加。日英両方。
  - Mintlifyは`openapi.json`から自動でページが作られるのでこれは対応不要。
