# Steering

このファイルは人間が編集し、「今後はこういうページを増やす」や「このページが間違ってるので修正」の細かい指示を出すためのものです。
対応が終わったら`[x]`で完了にしてください。

- [x] チュートリアルを複数ページ構成で作成していく。
- [x] Laravelの現在のバージョンは13。初回の実行から12と誤認。毎年3月頃にバージョンアップするのでモデルの知識だけではどうしても遅れてしまう。copilot-instructions.md にGitHub MCPで調べる方法を書いた。影響は`jp/tutorial/installation.mdx`で`PHP 8.2以上`と書いてたくらいなので8.3に修正した。他は将来的な既存ページの更新時に対応。
- [x] `jp/tutorial/installation.mdx`は`スターターキット（Breeze、Jetstream）`もモデルの古い知識で書いて間違っていた。Laravel12リリースと同時にBreeze、Jetstreamではなく完全に新しいスターターキットが導入されている。詳細はdocsの`starter-kits.md`
- [x] Mintlifyのデフォルトページは削除済み
- [x] 現在は月末でCopilotのプレミアムリクエストが余っているのでしばらく手動でCommanderを実行してページを増やしていく。同時に複数のissueを作ってもいいので積極的に稼働。
- [x] Commanderにより中級ページの追加開始
- [x] Commanderにより上級ページの追加開始
- [x] Commanderによりブログページの追加開始
- [x] Commanderにより英語ページの追加開始。
- [x] Laravel12期間の途中からLaravelでもAI対応が進んでいるので重要。`ai.md`は初級。`boost.md` `mcp.md` `ai-sdk.md`の個別パッケージの詳細は中級。「Boostのカスタムエージェントを作る」「LaravelでMCPサーバーを作る」「AI SDKのカスタムプロバイダーを作る（公式ドキュメントにもまだない）」などの内容は上級で扱う。
- [x] tabのメニューが揃ったのでこの辺りで一旦構造を整理。ディレクトリ構造は言語別ディレクトリ直下を基本にする。ドキュメント構造の初級・中級・上級はサイト制作側の分類でユーザーには意識させない。→tabの名前変更は完了、後でまた変えるかもしれない。ファイルの移動は規模が大きくなるので後でローカルで行う。
- [x] docs.json: navigation.languages内で言語別にページを定義する形式に変更。Mintlifyではドロップダウンメニューで言語を切り替えられるようになっている。
- [x] `helpers.md` `strings.md`のヘルパーはLaravelを便利に使うためにチュートリアル段階で知った方がいい機能だけどドキュメントとしてはcollectionsと同じ場所に配置がいいので中級で作成。
- [x] ページが増えてきたのでそろそろドメイン設定する準備。`index.mdx`はtabsの各カテゴリーに誘導する内容。日本語→英語の順で両方記載。トップの`/`を表示した時のデフォルト言語はnavigation.languagesの順番で決まる。どちらをデフォルトにするかは後で変えればいいので今は日本語で進める。
- [x] URLとして最適化するためファイルを移動する。tutorialとintermediateは言語別ディレクトリ直下に移動。advancedとblogは変更なし。docs.jsonや各ファイルのリンクを修正。`mint broken-links`コマンドでリンク切れを確認できるので実行しながら修正。
- [x] ドメイン設定して公開まで完了。引き続きページを増やしていく。
- [x] 手動実行でかなりページが増えたので元のデイリー実行に戻す。プレミアムリクエストは毎月余っているので、commander.mdの設定に従い必要と判断したら複数のissueを作る。
- [x] `lifecycle.md`のページを中級/ガイドに作成。docs.jsonではアーキテクチャグループをガイドの一番上に移動、lifecycleをアーキテクチャの一番上に配置。つまりlifecycleが中級のデフォルトページ。Laravelへの入門時はいきなりルーティングやコントローラーを触ってリクエストのライフサイクルを理解しなくても使えるけど、本格的に学ぶならライフサイクルの理解が一番重要。Laravelの入口は2つあって、`public/index.php`からのHttpと`artisan`からのConsole。MintlifyのMermaidも使って図解。
- [x] advancedにLaravel11以降のアプリケーション構造のページを追加。11.xブランチのreleases.mdにしか情報がないので現在は参照しにくくなっている。基本的な解説＋`Application::configure()`の先の`Illuminate\Foundation\Configuration\ApplicationBuilder`クラスまで深掘り。
- [x] blogにMac用の「HomebrewでPHPとcomposerとnode.jsをインストールする方法」とWindows用の「WSLでPHPとcomposerとnode.jsをインストールする方法」のページを追加。node.jsは今のCLIでのAIエージェント環境を想定してnvmを使う（rootでのインストールはたまに困ることがある）。
- [x] 既存ページにMermaidによる図解を追加。数ページずつ追加してるので継続。→細かいページまで追加するようになってきたので十分。今後は既存ページの改修時に必要に応じて追加していく。
- [ ] advanced デザインパターングループに`Illuminate\Support\Manager`の解説ページ。Laravel4.0の頃からあるLaravelのドライバーシステムを支えるクラス、だけどフレームワーク内部では〇〇Managerの名前だけど`Illuminate\Support\Manager`は使ってないことが徐々に増えた。CacheManagerやQueueManagerは使ってない、SessionManagerやSocialiteは使っている。継承して使ってなくても`extend()`で拡張などの基本機能は同じなのでフレームワーク内部動作の理解には大事。`Illuminate\Support\MultipleInstanceManager`はLaravel10で追加されたけど情報が少ない。自作パッケージで複数のドライバーに対応したい時に使える。

## 継続対応

- 新規ページ追加、翻訳ページ追加、既存ページの再レビュー・改修のタスクをバランスよくやっていく。AI SDKのような新しい機能のページはハルシネーションが発生していて管理者が発見して修正しているのでたまに再レビューが必要。
- docs.jsonの`navigation`を全体を見て再配置。ページを追加していくだけだと適切な分類ではなくなるのでたまに修正。
- ページ間リンクの追加。

## advanced ページ案

優先度は低い

- パッケージ開発者向けのページを増やす。管理者は大量のパッケージを作ってきて知見があるのでいくらでもネタはある。パッケージを一度作って終わりではなくLaravel・PHPのバージョンアップに合わせてメンテナンスを年単位で継続できるようになるまでのガイドを提供する。
- Laravelのバージョンアップへの対応：毎年2月から3月のQ1の時期にメジャーバージョンアップするのでパッケージでも対応する。リリース前の時期になれば公式パッケージや他のサードパーティパッケージが対応し出すのでそれを見て対応すればよい。安定したパッケージではこの作業が主なメンテナンスになる。`composer.json`で`"illuminate/support": "^11.0||^12.0",`→`"illuminate/support": "^12.0||^13.0",`に変更。年に一回ここを変えてるだけのパッケージも多い。
- PHPのバージョンアップへの対応：Laravelの変更と同時に変更する。`"php": "^8.2",`。Laravel12に合わせて8.2以上にするか、Laravel13に合わせて8.3以上にするか、新機能を使ってるので8.4にするか、などは各パッケージ次第。
- 良かれと思っていつまでも旧バージョンのサポートを続けない。Laravelエコシステム全体でバージョンアップしていくべきなのでパッケージ開発者としても貢献していく。
- 逆に新バージョンへの対応が遅いのも困る現象。10数年で大量のパッケージを乗り換えてきたし結局自ら作るようになった原因。リリースと同時にアップグレードしたい人も多いのでリリース前に対応が終わっているのがベスト。`composer.json`を変更してインストールさえ可能なら十分。不具合があってもリリース後に修正すればよい。新バージョンへの対応が遅い小規模パッケージは今ならAIでサッと代替手段を作ってしまうこともできる。
- [x] https://github.com/laravel/nightwatch Laravel Nightwatchはホスト型アプリケーション監視プラットフォーム。このリポジトリはNightwatchで監視するためのパッケージ。TelescopeとかPulseとか微妙に似たパッケージを公開してきたけどこれは有料サービス。 https://nightwatch.laravel.com/docs/start-guide 。2025年はLaravel CloudとLaravel Nightwatchに注力していた印象。一応無料プランでも使えるけど何も設定しないとすぐにイベントログがいっぱいになる。サンプリングレートを低くしたり `NIGHTWATCH_REQUEST_SAMPLE_RATE=0.1`、クエリーの収集を全て無効にする工夫が必要。 `NIGHTWATCH_IGNORE_QUERIES=true`
- Laravel Cloudも2025年からなので実際に使った人しか知らない情報が多い。一般的なLaravel専用PaaSって部分以上だと、Task SchedulerやバックグラウンドプロセスやNightwatch連携はForge同様に簡単、Octaneの使用が簡単、Inertia SSRの使用が簡単、WebSocketサーバーが簡単に導入可能。Laravelの高度な機能まで使い込んでる人が欲しい機能が全部揃っている。Forgeと比べて足りないのはroot権限がない。

## blog ページ案

優先度は低い

- https://github.com/laravel で公開された新しいリポジトリの調査。private状態で開発されてどこかのタイミングで公開される。大々的に発表されることもあるけどほとんどはドキュメントもなくリポジトリ内を見ないと何も分からない。バージョンは0.xで開発段階なことが多いのでblogで書くのは初期調査結果の情報。公式ドキュメントが公開されたら他で正式版のページを作成。
- [x] Maestro https://github.com/laravel/maestro スターターキット開発のオーケストレーター。一番新しく公開された。ユーザー向けパッケージではない。
- https://github.com/laravel/agent-skills AI用のエージェントスキル。最初はClaude Code用のスキルを置いてるリポジトリだったけどリポジトリ名を変えてリニューアル。「Laravel公式のmarketplace」としてこれから整備されていくんだろう。
- [x] Wayfinder https://github.com/laravel/wayfinder v0.1だけど既にInertiaを使うスターターキットでは導入されている。元々使っていたZiggyからの置き換え。mainブランチが0.1、nextブランチの次期バージョンで色々変わることも確定しているので0.1でページを作ってもすぐに古くなってしまう。
- https://github.com/laravel/roster https://github.com/laravel/ranger https://github.com/laravel/surveyor https://github.com/laravel/sentinel この辺りになるとほとんど分からなくなる。rosterはboostで使われている。
