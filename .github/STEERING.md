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
- [x] VOICEVOX Core for PHP
- [x] VOICEVOX for Laravel
- [x] Fetch metadata middleware for Laravel https://github.com/invokable/laravel-fetch-metadata
  - csrfのページが追加されたのでこのパッケージのページを作成。
  - Laravel13のcsrfで`Sec-Fetch-Site`が使われるようになる前に作っていたけどほとんど使ってない。Laravelが`Sec-Fetch-Site`しか使ってないように使い所は限られる。下手に使うと検索エンジンや今ならAIエージェントが読めなくなる。
  - README.mdが英語、src内も少ないシンプルなパッケージなので1ページ。
  - navigation-packages.json はスターターキットよりも下の最後に「ミドルウェア」グループを作って追加。
- [x] Laravel FullFeed https://github.com/invokable/laravel-fullfeed
  - フィードリーダー向けの「URLからコンテンツを抽出する」パッケージ。
  - Pipelineパターンの実例になる。 advanced/pipeline
  - README.mdとresources/fullfeed/README.mdは英語、resources/fullfeed/README_jp.mdは日本語。
  - 日本では定番だったLDRFullFeedのjsonデータを使っている。LDRとはLivedoor Readerのことだけど10年以上前にサービス終了していてもはや何も残ってないけど非公式だったFullFeedのデータだけ現代まで残っている。とはいえ古すぎるのでこのパッケージではCSSセレクタの新形式がメイン。LDRFullFeedから新形式に移植してたけど多すぎるので途中で終了している。
  - フィード関連パッケージはもう少しあるので navigation-packages.json はスターターキットとミドルウェアの間に「フィード・RSS」グループを作成。
- [ ] Feedable
  - スターターキット https://github.com/invokable/feedable と更新しやすいように分離したコアパッケージ https://github.com/invokable/feedable-core
  - RSSのないウェブサイトからRSSを生成するサービス
  - [RSSHub](https://github.com/DIYgod/RSSHub) を見つけて各サイトをルーティングで定義してるような作りだったのでLaravelでも同じものが作れそうなので作ったパッケージ。RSSHubに日本語サイトは少なそうなので日本語中心。
  - RSSHubはルート(lib/router.js)とhandler(lib/routes/*/index.tsx)を別で登録してるけどLaravelならServiceProviderでルートも登録できるのでサイト毎に完全に分離できるし、サードパーティパッケージとして自由に拡張もできる。ServiceProviderは自動で読み込まれるので`routes/web.php`を変更するような作業は不要。スターターキットから見たコアも同じで特殊なことは何もしてなくて対応サイトを表示してるだけのスターターキット。
  - 各サイトは「ドライバー」と呼んでるけど実態はルーティングとコントローラーと同じ。スターターキットに直接追加してもいい。ページでのサンプルにちょうど良さそうなのは英語のLaravel公式ブログ。 [LaravelServiceProvider](https://github.com/invokable/feedable-core/blob/main/src/Drivers/Laravel/LaravelServiceProvider.php)、[LaravelBlogDriver](https://github.com/invokable/feedable-core/blob/main/src/Drivers/Laravel/LaravelBlogDriver.php)
  - リクエストがあればドライバーを増やしていくけどJsonFeedドライバーであらゆるRSS、AtomをLaravel製フィードリーダーで読みやすくなったので追加ペースは落ち着いている。 [JsonFeedServiceProvider](https://github.com/invokable/feedable-core/blob/main/src/Drivers/JsonFeed/JsonFeedServiceProvider.php)、[JsonFeedDriver](https://github.com/invokable/feedable-core/blob/main/src/Drivers/JsonFeed/JsonFeedDriver.php)、[JsonFeed](https://github.com/invokable/feedable-core/blob/main/src/Core/JsonFeed/JsonFeed.php)
  - データベース不要で使えるのでスターターキットをVercelにデプロイするだけで使える。
  - ドキュメントはほとんどない。[README.md](https://github.com/invokable/feedable/blob/main/README.md) が英語、[README_jp.md](https://github.com/invokable/feedable/blob/main/README_jp.md) が日本語。[copilot-instructions.md)](https://github.com/invokable/feedable-core/blob/main/.github/copilot-instructions.md) や[create-driver/SKILL.md](https://github.com/invokable/feedable-core/blob/main/.github/skills/create-driver/SKILL.md) もあった。
  - index.mdx:README相当の概要。core.mdx:コアの[src/Core](https://github.com/invokable/feedable-core/tree/main/src/Core)の説明と独自ドライバーの作り方。drivers.mdx:対応サイトリスト。元のドキュメントが少ないので先に日本語ページから作って管理者が修正を入れる。
  - 独自ドライバーの作り方：スターターキットで普通の`routes/web.php`とコントローラーとして作る。パッケージ化は任意。`Driver::about()`はドライバーの登録だけどスターターキットの対応サイトに表示されるだけなので登録しなくても動作はする。Httpクライアントでhtml取得→Dom\HTMLDocumentでパース→FeedItemの配列として返す→最終的にResponseFactoryを返せば出力フォーマットをrssとjsonで切り替えられる。
