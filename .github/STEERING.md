# Steering

このファイルは人間が編集し、「今後はこういうページを増やす」や「このページが間違ってるので修正」の細かい指示を出すためのものです。
対応が終わったら`[x]`で完了。

- マイパッケージの解説ページ。下のpackages ページ案に追加されたら対応。
- [x] 重複ページを作り出してるのでここまでの完了したタスクを削除。公式ドキュメントを元にしたページは揃ってきた感じなので独自コンテンツを増やしていける段階。

## 継続対応

- 新規ページ追加、翻訳ページ追加、既存ページの再レビュー・改修のタスクをバランスよくやっていく。AI SDKのような新しい機能のページはハルシネーションが発生していて管理者が発見して修正しているのでたまに再レビューが必要。
- docs.jsonの`navigation`を全体を見て再配置。`config/`内に言語ごとに分割済み。ページを追加していくだけだと適切な分類ではなくなるのでたまに修正。
- ページ間リンクの追加。

## advanced ページ案

- パッケージ開発者向けのページを増やす。管理者は大量のパッケージを作ってきて知見があるのでいくらでもネタはある。パッケージを一度作って終わりではなくLaravel・PHPのバージョンアップに合わせてメンテナンスを年単位で継続できるようになるまでのガイドを提供する。
 - `package-versioning`が作られたけど今後もネタがあれば継続。
- [x] Laravel Cloudも2025年からなので実際に使った人しか知らない情報が多い。一般的なLaravel専用PaaSって部分以上だと、Task SchedulerやバックグラウンドプロセスやNightwatch連携はForge同様に簡単、Octaneの使用が簡単、Inertia SSRの使用が簡単、WebSocketサーバーが簡単に導入可能。Laravelの高度な機能まで使い込んでる人が欲しい機能が全部揃っている。Forgeと比べて足りないのはroot権限がない。
 - 使っていくうちに新しい情報が入ったら後で追加。
- [x] `Illuminate\Support\Traits\InteractsWithData`トレイトの解説。プロジェクトで直接使うことは少ないのでパッケージ開発者向け。
- [x] `tap()`ヘルパー、`Illuminate\Support\Traits\Tappable`トレイトの解説。存在は知ってるけど使い所が分からないと言われることが多い機能第一位。これもトレイトはパッケージ開発者向け。すでにページのあるMacroableやConditionableと合わせてLaravel風の使い方を提供できる。
- [ ] Collection Deep Dive。使うだけならドキュメントで十分だけど実装コードまで理解しようとすると複雑。個別のメソッドまで追うと長すぎるのでコードを読んでいきたい人向けのCollectionクラスの全体構造の解説にする。Laravel5.8までは`Illuminate\Support\Collection`と継承先の`Illuminate\Database\Eloquent\Collection`だったけどLaravel6で`LazyCollection`が追加された時に`Enumerable`インターフェースと`EnumeratesValues`トレイトで共通化する構造になった。その後はPHPDoc部分がPHPStanスタイルになる更新が何度も入っている。むしろ一番解説が必要なのはこのPHPDoc部分かも。GenericsはPHPにはまだないのにPHPDocでだけ使われていて馴染みのない人も多い。

## blog ページ案

- https://github.com/laravel で公開された新しいリポジトリの調査。private状態で開発されてどこかのタイミングで公開される。大々的に発表されることもあるけどほとんどはドキュメントもなくリポジトリ内を見ないと何も分からない。バージョンは0.xで開発段階なことが多いのでblogで書くのは初期調査結果の情報。公式ドキュメントが公開されたら他で正式版のページを作成。
 - [x] maestro-introduction
 - [x] agent-skills-introduction
 - [x] laravel-ecosystem-analysis: surveyor, ranger, roster
 - [x] sentinel-introduction

## packages ページ案
- [x] Amazon Bedrock driver for Laravel AI SDK。https://github.com/invokable/laravel-amazon-bedrock
 - AI SDK公式ドキュメントには全く情報がないのに`ai-sdk-custom-provider`のページを作れたのは実際にカスタムプロバイダーを作っていたから。
 - 実装できるAI SDKの機能はほぼ実装し終わったのでドキュメントページを作る。
 - README.mdの情報でページは作れるはず。他のページのスタイルと合わせる。
 - 他のカスタムプロバイダーの事例は知らないので初かも。
 - BedrockでストリーミングはAWS公式のPHP用SDKでもPrismでも対応できてない。このパッケージが唯一。
- [ ] GitHub Copilot SDK for Laravel。https://github.com/invokable/laravel-copilot-sdk
 - [GitHub Copilot SDK](https://github.com/github/copilot-sdk) のLaravel版。
 - 公式SDKの機能を再現したレイヤーの上にLaravelらしいFacadeを中心にした使い方を提供している。
 - ドキュメントはREADME.mdとdocs/getting-started.mdが英語。docs/jp/内に日本語のドキュメントが大量。公式SDKに英語のドキュメントがしっかりあるので日本語中心にしか用意してない。こっちのマイパッケージで英語ドキュメントを作る。
 - 1ページでは収まらないので`{lang}/packages/laravel-copilot-sdk/`ディレクトリを作ってその中に複数ページに分けて入れる。
 - 一度では終わらないので少しずつ実行する。
 - docs/jp/内のドキュメントの英語版を先に作成。細かいドキュメントは不要かもしれないけど英語版では全部翻訳。
 - SDK側のgetting-started.mdを上で作った英語ドキュメントにリンクするように変更するのでその後に`getting-started.mdx`を作成。
 - `index.mdx` 基本的な説明とLaravel版特有機能の説明。ここまで作った各ページへのリンク。
 - 最後に日本語ページを作成。日本語はSDK側が最新なのでページの最後にGitHubへのリンクを入れる。
 - docs.jsonのnavigationはネストしてindex以外の各ページを配置。
