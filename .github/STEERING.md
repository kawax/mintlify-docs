# Steering

このファイルは人間が編集し、「今後はこういうページを増やす」や「このページが間違ってるので修正」の細かい指示を出すためのものです。
対応が終わったら`[x]`で完了。

- マイパッケージの解説ページ。下のpackages ページ案に追加されたら対応。
- [x] 重複ページを作り出してるのでここまでの完了したタスクを削除。公式ドキュメントを元にしたページは揃ってきた感じなので独自コンテンツを増やしていける段階。
  - 重複しても新しい情報があればプルリクの段階でページを統合して更新するように指示できるので「既存ページの再レビュー・改修」ができて問題ないかもしれない。

## 継続対応

- 新規ページ追加、翻訳ページ追加、既存ページの再レビュー・改修のタスクをバランスよくやっていく。`laravel/docs`はちょくちょく変更されてる。
- docs.jsonの`navigation`を全体を見て再配置。`config/`内に言語ごとに分割済み。ページを追加していくだけだと適切な分類ではなくなるのでたまに修正。
- ページ間リンクの追加。

## advanced ページ案

- パッケージ開発者向けのページを増やす。管理者は大量のパッケージを作ってきて知見があるのでいくらでもネタはある。パッケージを一度作って終わりではなくLaravel・PHPのバージョンアップに合わせてメンテナンスを年単位で継続できるようになるまでのガイドを提供する。
  - `package-versioning`が作られたけど今後もネタがあれば継続。

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
- [ ] Vueの紹介ページ。Laravel5.3(2016年)の頃からしばらくはVueが標準搭載だったのでLaravelユーザーには一番馴染みがある。blogタブ内に「フロントエンド」グループを追加して3ページを配置。全部InertiaなのでInertiaで使う時に必要な基礎知識な内容。
- [ ] Reactの紹介ページ。LaravelではBreezeの途中でInertia React版が追加(2021年)。JetstreamにはReact版は追加されなかったので歴史はやや浅め。現行のスターターキットでは最初からVueとReactが同時対応なので今は同列の扱い。
- [ ] Svelteの紹介ページ。Svelte版スターターキットの登場は2026年なので一番新しい。Laravelユーザーにはほとんど知られてない。

## packages ページ案
- [x] Amazon Bedrock driver for Laravel AI SDK https://github.com/invokable/laravel-amazon-bedrock
- [x] GitHub Copilot SDK for Laravel。https://github.com/invokable/laravel-copilot-sdk
  - [GitHub Copilot SDK](https://github.com/github/copilot-sdk) のLaravel版。
  - 英語・日本語の全ページ完成。今後も追加・変更はあるだろうけど管理者がIssueを作ってエージェントをアサインして対応していく。
- [x] Laravel Bluesky https://github.com/invokable/laravel-bluesky
- [x] Laravel Console Starter Kit https://github.com/invokable/laravel-console-starter
  - パッケージではなくスターターキット。元のパッケージ版は https://github.com/invokable/laravel-slim 
- [x] Laravel Nostr https://github.com/invokable/laravel-nostr
- [x] Laravel Notification for Discord(Webhook) https://github.com/invokable/laravel-notification-discord-webhook
  - Discordに通知する単機能パッケージのWebhook版。
  - いつもの投稿のためのBasic client＋通知機能ではなく、Webhookなのでいきなり通知が可能。
  - 本来のDiscord APIはWebSocketが必要で複雑だけどWebhook版は一切不要で簡単。
  - 仮で`SDK`グループに追加。
- [x] Socialite for Discord https://github.com/invokable/socialite-discord
  - Socialite用のDiscordドライバー。Socialiteドライバーを作るのは簡単なのでOAuth機能があり自分で使うことがあるサービスならすぐに作っている。
  - `jp/socialite.mdx`で公式ドキュメントにあるSocialite Providersの記述を全部消して`Socialite::extend()`で拡張する正規の方法を書いてるのは確実にこの方法が正しいから。Socialite Providersにすでに同じドライバーがあっても関係なく自分で作っている。
