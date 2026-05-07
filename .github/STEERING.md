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
- [x] Fortifyページ https://github.com/laravel/docs/blob/13.x/fortify.md
  - Fortifyは単体で使うよりスターターキットの一部なので公式ドキュメントそのままではなくadvanced用のページを作る。スターターキットで使われている機能だけ解説。
  - 歴史。Laravel8(2020年)のJetstreamスターターキットと同時に登場。当時はJetstreamをインストールしたら一緒にインストールされる裏方扱いだった。「フロントエンドに依存しない認証バックエンド」なので結局JetstreamやBreezeから現行スターターキットに変わっても使われていてFortifyが一番長生きしている。
  - https://github.com/laravel/react-starter-kit/blob/main/app/Providers/FortifyServiceProvider.php, https://github.com/laravel/react-starter-kit/blob/main/config/fortify.php 現行スターターキットでもFortifyが使われている。実は最初はFortifyを使ってなかったけど二要素認証に対応するためにFortifyを使うようになったので認証機能などもFortifyに置き換わった。
  - blog/passkeys-introduction.mdx で初期調査したパスキーはFortifyの機能として追加。公式ドキュメントはさっき更新されたばかり。スターターキットもパスキーに対応しそうだけどまだなのでドキュメント通りの説明を書いておいて後で更新する。passkeys-introduction.mdx は初期調査なので中身は変更せず「その後パスキーはFortifyの機能として追加されました」とFortifyページへリンク。
  - 日本語ページはOK。
- [ ] スターターキットの作り方ページ。「パッケージ開発」グループに追加。
  - 公式ドキュメントでは短い説明しかない。
  - スターターキットを作るならパッケージと同様にLaravelのバージョンアップに追従する作業が必要になる。
  - 特殊なことはなく、テンプレートとなるLaravelプロジェクトを作成、composer.jsonの`name`にユニークな名前を付けて [Packagist](https://packagist.org/) に登録。`laravel new my-app --using=example/starter-kit`コマンドではこの`name`を使う。
  - composer.jsonの`scripts`はLaravel公式スターターキットを参考に`post-root-package-install`や`post-create-project-cmd`を記述。データベースを使うならそのまま同じ内容になる。
  - `.gitattributes`でスターターキットのリポジトリには含めるけどユーザーが作成したプロジェクトからは除くファイルを指定できる。`LICENSE export-ignore`や`composer.lock export-ignore`など。
  - `laravel new`実行時のフローを [NewCommand](https://github.com/laravel/installer/blob/master/src/NewCommand.php) を元に説明。
  - 参考リンク。packages/laravel-console-starter

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
- [ ] `laravel/ui`からFortifyへの移行ガイド
  - 古くからのプロジェクト、もしくはよく分からず`laravel/ui`で作り始めてしまったプロジェクト用。`laravel/ui`はLaravel13でも動くようにメンテナンスは続いているけどいつまでも古いパッケージに依存してるのは不安、かといって新しいスターターキットへのリニューアルも難しい場合はFortifyに移行すると少しだけ現行スターターキットと近くなる。
  - bootstrapベースのまま認証バックエンドだけFortifyに変更できる。
  - 現行スターターキットと同様にFortifyServiceProviderで`Fortify::loginView()`などを設定するのがポイント。`Fortify::viewPrefix('auth.');`
  - PC内にLaravel8当時の記事ファイルが残ってるので日本語ページを作成→管理者が修正→英語ページを作成の流れ。

## packages ページ案
- [x] Laravel Notification for Discord(Webhook)
- [x] Socialite for Discord
- [x] LINE SDK for Laravel
