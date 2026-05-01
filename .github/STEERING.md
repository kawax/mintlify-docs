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
- [ ] Reactの紹介ページ。Laravelでは`laravel/ui`が分離された時にReact版も登場(2019年)、Breezeの途中でInertia React版が追加(2021年)。JetstreamにはReact版は追加されなかったので歴史はやや浅め。`laravel/ui`で対応してたのを忘れるくらい影が薄かった。現行のスターターキットでは最初からVueとReactが同時対応なので今は同列もしくはReactが優先の扱い。
- [ ] Svelteの紹介ページ。Svelte版スターターキットの登場は2026年なので一番新しい。Laravelユーザーにはほとんど知られてない。スターターキットから使うならVue/React/Svelteどれを使ってもshadcnベースのコンポーネントライブラリを使うだけなので基礎知識さえあれば使っていけるはず。

## packages ページ案
- [x] Laravel Notification for Discord(Webhook) https://github.com/invokable/laravel-notification-discord-webhook
  - Discordに通知する単機能パッケージのWebhook版。
  - いつもの投稿のためのBasic client＋通知機能ではなく、Webhookなのでいきなり通知が可能。
  - 本来のDiscord APIはWebSocketが必要で複雑だけどWebhook版は一切不要で簡単。
  - 仮で`SDK`グループに追加。
- [x] Socialite for Discord https://github.com/invokable/socialite-discord
  - Socialite用のDiscordドライバー。Socialiteドライバーを作るのは簡単なのでOAuth機能があり自分で使うことがあるサービスならすぐに作っている。
  - `jp/socialite.mdx`で公式ドキュメントにあるSocialite Providersの記述を全部消して`Socialite::extend()`で拡張する正規の方法を書いてるのは確実にこの方法が正しいから。Socialite Providersにすでに同じドライバーがあっても関係なく自分で作っている。
- [ ] LINE SDK for Laravel https://github.com/invokable/laravel-line-sdk
  - LINE公式SDKはOpenAPIから自動生成して作られてるのかとんでもなく使いにくい。Laravel用に使いやすくしたパッケージ。
  - READMEとdocs内に英語のドキュメントがある。
  - いつもの通知とSocialite。以前はLINE Notifyがあって無料で便利に通知が送れたけどサービス終了したのでLINE Notify対応は削除済み。
  - 基本はBot Facadeから公式SDKのクラスに委譲してる形式。`Bot::reply()`辺りが独自設計。LINEは一方的にメッセージを送るのは制限されてるけど返信なら自由なのでreplyを便利にすると効率がいい。
  - LINEからのメッセージはWebhookで受信。ルートもコントローラーも検証ミドルウェアもパッケージで用意している。Webhookで受信したらLaravelのイベントが発行されるのでユーザー側はイベントリスナーで処理を行えばいい。リスナーのstubも用意してるので `MessageListener.php` を書き換えるだけですぐに使える。
  - WebhookControllerの引数をWebhookHandler interfaceにしてサービスコンテナで実際の処理をWebhookEventDispatcher、WebhookLogHandler、WebhookNullHandlerから選んだり自由に変更できるようにしているのはLaravelらしい設計。
  - 使いやすさに全振りしてたので今見ても分かりやすい。
