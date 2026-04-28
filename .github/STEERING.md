# Steering

このファイルは人間が編集し、「今後はこういうページを増やす」や「このページが間違ってるので修正」の細かい指示を出すためのものです。
対応が終わったら`[x]`で完了。

- マイパッケージの解説ページ。下のpackages ページ案に追加されたら対応。
- [x] 重複ページを作り出してるのでここまでの完了したタスクを削除。公式ドキュメントを元にしたページは揃ってきた感じなので独自コンテンツを増やしていける段階。
  - 重複しても新しい情報があればプルリクの段階でページを統合して更新するように指示できるので「既存ページの再レビュー・改修」ができて問題ないかもしれない。
- [x] https://github.com/laravel/docs/pull/11172 MCP Apps対応で文量が多いのでmcp.mdxにも反映。

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
  - [x] pao-introduction ページ作成時点ではLaravel公式に移行直後でまだ`laravel/pao`でインストールできないけど初期調査なのでいいだろう。
- [x] Laravel Cloudも2025年からなので実際に使った人しか知らない情報が多い。一般的なLaravel専用PaaSって部分以上だと、Task SchedulerやバックグラウンドプロセスやNightwatch連携はForge同様に簡単、Octaneの使用が簡単、Inertia SSRの使用が簡単、WebSocketサーバーが簡単に導入可能。Laravelの高度な機能まで使い込んでる人が欲しい機能が全部揃っている。Forgeと比べて足りないのはroot権限がない。
  - 使っていくうちに新しい情報が入ったら後で追加。
  - [x] Hibernation 日本語だと休止かな。Laravel Cloudはサーバーが稼働中のみ課金されるので費用を抑えるには自動休止を有効にする。休止中はタスクスケジュールもキューも動かないので個人用途でタスクスケジュールで自動実行する用途では使いにくい。Httpリクエストがあれば休止から復帰するけど関係ないリクエストでも復帰する、最近追加された「Path Blocking」を有効にすれば`.php`へのリクエストなどをブロックして不要な復帰を防げる。
  - [x] Laravel Cloudはadvancedのページ案だったのに最初にblogで作られた後、Hibernationページがadvancedに作られて離れてしまった。blogに移動して統一。blogのProducts/プロダクトグループでLaravel公式の有料サービスを扱う。

## packages ページ案
- [x] Amazon Bedrock driver for Laravel AI SDK https://github.com/invokable/laravel-amazon-bedrock
- [x] GitHub Copilot SDK for Laravel。https://github.com/invokable/laravel-copilot-sdk
  - [GitHub Copilot SDK](https://github.com/github/copilot-sdk) のLaravel版。
  - 英語・日本語の全ページ完成。今後も追加・変更はあるだろうけど管理者がIssueを作ってエージェントをアサインして対応していく。
- [ ] Testbench `package-testing.mdx` が作られてたので次はLaravel Bluesky https://github.com/invokable/laravel-bluesky
  - `docs`内に英語のドキュメントがある。AI普及前なので最低限のドキュメントしかない。
  - [x] docs/workbench.md はBlueskyとは関係ないTestbench Workbenchのドキュメント。Workbenchの情報がなさすぎて調べた結果をとりあえずここに置いていた。こっちのサイトに移せばいいのでworkbench.mdを元に`package-testing.mdx`の続きのページを作成。
  - 残りのページは`{lang}/packages/laravel-bluesky/`内に複数ページで作成。
  - SNSのパッケージは色々作ってるけど基本的なクライアント機能が完成したらNotificationsやSocialiteのLaravelの機能を被せて実際に使うのは通知機能での投稿ばかりなことも多い。
  - [x] BlueskyのSocialiteは他と違うので若干難しい。詳しい説明が必要。
  - [x] Bluesky特有機能でLaravelユーザーが作りやすいのはFeed Generator。
  - [x] Labelerはサーバーとして動かし続ける必要があるのでLaravel Forgeを使っているか自力で構築できる人向け。Laravel Cloudは非対応だった。サンプルのlaralabelerをForgeからCloudに移行しようとしてできなかった。
  - [x] WebSocketはもっと難しいので意図的にドキュメントを作ってないけどこっちで作る。`JetstreamServeCommand` `FirehoseServeCommand`
  - [x] CryptoやCoreまで行くと本当の深淵。AIもない頃に他言語版と仕様を調べまくって作った。PHPでここまで実装してるパッケージが他にあるのかは知らない。Bluesky/AT Protocolの詳細な仕様まで知りたい人向け。
  - 詳細なドキュメントを作りたいけど一から調べると大変なのでDeepWikiを参照するのが良さそう。 https://deepwiki.com/invokable/laravel-bluesky
  - DeepWikiのページは再生成された時に変わるので個別ページへのリンクは貼らない。
  - docsにあるページは全部作れたけど元からユーザーが必要な情報が足りてないのでDeepWikiがコードまで見てまとめたページを元にもっとページを作る。
  - [x] App PasswordとOAuthの認証方法の違いと実装アーキテクチャの解説。LegacyAgent/LegacySession/Bluskey::login()とOAuthAgent/OAuthSession/Bluesky::withToken()。認証方法ごとに分けてるけどその先のAPI呼び出しは共通。App Passwordは最初にLegacyと名付けたけど終了予定はないし通知ではApp Passwordの方が使いやすいので両方使うことになる。
  - https://github.com/invokable/atproto-lexicon-contracts でAT Protocol公式のLexicon定義ファイルからPure PHP用のinterfaceやenumを自動生成している。これを元にさらにLaravel用のtraitを自動生成している設計。`src/Client/Concerns`
  - [x] Bluesky Facadeの実体はBlueskyManagerでよく使うだろうメソッドはHasShortHandトレイトですぐに使えるようにしている。ShortHandを用意は公式SDKと同じ仕組み。
  - [x] TextBuilderの詳細な使い方。
  - [x] AT Proto公式チュートリアルのLaravel版
- [ ] Laravel Console Starter Kit https://github.com/invokable/laravel-console-starter
  - パッケージではなくスターターキット。元のパッケージ版は https://github.com/invokable/laravel-slim 
  - READMEにはAIによってアプリケーションアイデアが色々書かれてるけど要するに上のBlueskyのボットチュートリアル packages/laravel-bluesky/bot-tutorial のような **artisanコマンドをGitHub Actionsで実行して最終出力は通知機能でメールやチャットに送る** 使い方を想定している。
  - Laravelを長く使いすぎた人がLaravelの一番便利な機能だけを追求していくとここに辿り着く。
  - artisanコマンドなのでLaravelのエコシステムが使える。
  - GitHub Actionsなのでサーバー不要。
  - 他者からの入力がないのでセキュリティ的に安全。

スターターキットグループを作って配置。
```json
        {
          "group": "Starter Kits",
          "pages": [
            "jp/packages/laravel-console-starter"
          ]
        }
```
