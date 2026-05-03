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
- [ ] app-structureの下に旧構造から新構造への移行ガイドを追加。公式は推奨してないとはいえドキュメントが新構造前提の内容しかないので移行しないとドキュメントが読みにくい。
  - Laravel11リリース当時に記事を書いてたけどもう消えてるので再生成。今調べても正確な記事は書けないので日本語版だけ作成して管理者が修正→その後に英語版を作る。PC内には当時の記事ファイルが残ってたので修正できる。
  - Laravel10+Breeze bladeスタックで新規プロジェクトを作ってからBreezeのままLaravel11にアップグレードする例。
  - 最初に警告として公式ドキュメントでは全く推奨してないこと、フレームワーク内部まで詳しい人以外はやめたほうがいいこと、旧構造のままでもLaravel13までアップグレードできていて今後もサポート終了予定はないことを書いておく。
- [ ] Laravel11以降の新構造のFAQページ。Laravel11以降に新しく使い始めた人向けの質問と回答集。旧構造のままLaravel12や13を使ってることも多いだろうから既存プロジェクトに途中参加した人は戸惑う。逆に古い本で勉強した人が新構造を見ても戸惑う。Laravel11リリースから時間が経ってるけど今も新旧構造が混在してるなら必要な情報。これも当時の記事ファイルがあり修正できるので日本語ページから作成。
  - configファイルが少ない：変更することが少ないconfigファイルが削除された。新構造しか知らない人には非常に分かりにくい部分だけど「ファイルはないけどフレームワーク内のconfigファイルが使われる」「プロジェクトのconfigファイルとフレームワーク内のconfigファイルとマージされて使われる。プロジェクト側が優先。」
  - コントローラーで`$this->validate()`や`$this->authorize()`が使えない：ベースコントローラー(`Illuminate\Routing\Controller`)を継承せず`ValidatesRequests`や`AuthorizesRequests`もない空のコントローラーになったので代わりに`$request->validate()`や`Gate::authorize()`を使う。[Laravel10のApp\Http\Controllers\Controller](https://github.com/laravel/laravel/blob/10.x/app/Http/Controllers/Controller.php)、[Laravel11のApp\Http\Controllers\Controller](https://github.com/laravel/laravel/blob/11.x/app/Http/Controllers/Controller.php)
  - 途中参加したプロジェクトでの判別方法。`bootstrap/app.php`を見て`return Application::configure(...`ならLaravel11以降に作られたプロジェクト、もしくは新構造に移行したプロジェクト。違うなら旧構造のままアップグレードしたプロジェクト、ドキュメントはLaravel10と使用中バージョンの両方を参考する。

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
- [x] Vueの紹介ページ。Laravel5.3(2016年)の頃からしばらくはVueが標準搭載だったのでLaravelユーザーには一番馴染みがある。blogタブ内に「フロントエンド」グループを追加して3ページを配置。全部InertiaなのでInertiaで使う時に必要な基礎知識な内容。
- [x] Reactの紹介ページ。Laravelでは`laravel/ui`が分離された時にReact版も登場(2019年)、Breezeの途中でInertia React版が追加(2021年)。JetstreamにはReact版は追加されなかったので歴史はやや浅め。`laravel/ui`で対応してたのを忘れるくらい影が薄かった。現行のスターターキットでは最初からVueとReactが同時対応なので今は同列もしくはReactが優先の扱い。
- [x] Svelteの紹介ページ。Svelte版スターターキットの登場は2026年なので一番新しい。Laravelユーザーにはほとんど知られてない。スターターキットから使うならVue/React/Svelteどれを使ってもshadcnベースのコンポーネントライブラリを使うだけなので基礎知識さえあれば使っていけるはず。

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
