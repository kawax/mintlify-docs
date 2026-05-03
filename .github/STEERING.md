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
- [ ] app-structureの下に旧構造から新構造への移行ガイドを追加。公式は推奨してないとはいえドキュメントが新構造前提の内容しかないので移行しないとドキュメントが読みにくい。
  - Laravel11リリース当時に記事を書いてたけどもう消えてるので再生成。今調べても正確な記事は書けないので日本語版だけ作成して管理者が修正→その後に英語版を作る。PC内には当時の記事ファイルが残ってたので修正できる。
  - Laravel10+Breeze bladeスタックで新規プロジェクトを作ってからBreezeのままLaravel11にアップグレードする例。
  - 最初に警告として公式ドキュメントでは全く推奨してないこと、フレームワーク内部まで詳しい人以外はやめたほうがいいこと、旧構造のままでもLaravel13までアップグレードできていて今後もサポート終了予定はないことを書いておく。
  - 日本語版はOKなので英語ページを作成。advanced/app-structure-migration.mdx
- [ ] Laravel11以降の新構造のFAQページ。Laravel11以降に新しく使い始めた人向けの質問と回答集。旧構造のままLaravel12や13を使ってることも多いだろうから既存プロジェクトに途中参加した人は戸惑う。逆に古い本で勉強した人が新構造を見ても戸惑う。Laravel11リリースから時間が経ってるけど今も新旧構造が混在してるなら必要な情報。これも当時の記事ファイルがあり修正できるので日本語ページから作成。
  - configファイルが少ない：変更することが少ないconfigファイルが削除された。新構造しか知らない人には非常に分かりにくい部分だけど「ファイルはないけどフレームワーク内のconfigファイルが使われる」「プロジェクトのconfigファイルとフレームワーク内のconfigファイルがマージされて使われる。プロジェクト側が優先。」
  - コントローラーで`$this->validate()`や`$this->authorize()`が使えない：ベースコントローラー(`Illuminate\Routing\Controller`)を継承せず`ValidatesRequests`や`AuthorizesRequests`もない空のコントローラーになったので代わりに`$request->validate()`や`Gate::authorize()`を使う。[Laravel10のApp\Http\Controllers\Controller](https://github.com/laravel/laravel/blob/10.x/app/Http/Controllers/Controller.php)、[Laravel11のApp\Http\Controllers\Controller](https://github.com/laravel/laravel/blob/11.x/app/Http/Controllers/Controller.php)。よく使うなら`App\Http\Controllers\Controller`をLaravel10と同様に戻してもいい。
  - app/Http/Middlewareがなくてミドルウェアの設定を変更できない：bootstrap/app.phpでの設定に変更。
  - app/Http/Kernel.phpがなくてミドルウェアを追加できない：bootstrap/app.phpでの設定に変更。
  - `$this->middleware()`がないのでコントローラー内でのミドルウェアの指定ができない：リリースノート・アップグレードガイドには書いてないけど使い方が変わっている。`HasMiddleware`を指定して`middleware()`メソッドで指定、もしくはLaravel13なら`Attributes`での指定もできる。 https://laravel.com/docs/13.x/controllers#controller-middleware 。コントローラー内で指定よりルーティングで指定するほうがおすすめ。
  - コントローラーに`$this->authorizeResource()`がない：実はこれだけ簡単な代替手段がない。公式ドキュメントからも完全に削除されている。ベースコントローラー(`Illuminate\Routing\Controller`)と`AuthorizesRequests`に依存しているので`App\Http\Controllers\Controller`をLaravel10仕様に戻すしかない。Laravel13なら`Authorize`Attributesを使ってメソッドごとに設定するのがベストなはず。
```php
use Illuminate\Routing\Attributes\Controllers\Authorize;
 
#[Authorize('update', 'post')]
public function update(Post $post)
{
    // The current user may update the post...
}
```
  - app/Console/Kernel.phpがなくてScheduleの設定ができない：routes/console.phpもしくはbootstrap/app.phpでの設定に変わった。
  - イベントとリスナーの登録方法が分からない：イベントクラスとhandle()にイベントを指定したリスナーを作るだけで自動で登録されるので手動登録は不要。
  - config/app.phpへのサービスプロバイダー追加方法が分からない：bootstrap/providers.phpへの追加に変わった。
  - app/Exceptions/Handler.phpがない：bootstrap/app.phpでの設定に変わった。
  - ルーティングをもっとカスタマイズしたい：Laravel10ではRouteServiceProviderでルートファイルを増やして追加できた。Laravel11では`withRouting(then: fn()=>{})`でルートファイルを追加できる。`withRouting(using: fn()=>{})`ならLaravel10と同様に完全に制御できる。
  - LaravelデフォルトのServiceProviderを置き換えたい：一部のサードパーティパッケージはデフォルトのServiceProviderをパッケージのServiceProviderに置き換えて使うように指示してくる。config/app.phpからprovidersは消えているけどフレームワーク内のconfig/app.phpには残っている。「configはマージして使われる」のでプロジェクト側のconfig/app.phpにprovidersを追加すればいい。
```php
'providers' => ServiceProvider::defaultProviders()->replace([
Illuminate\Foo\FooServiceProvider::class => Bar\BarServiceProvider::class,
])->toArray(),
```
  - routes/api.phpがない：API関連の機能は必要な人だけ追加するように変わったので個別にインストールする。php artisan install:api
  - routes/channels.phpがない：ブロードキャストも同じく個別にインストールする。php artisan install:broadcasting
  - 途中参加したプロジェクトでの判別方法。`bootstrap/app.php`を見て`return Application::configure(...`ならLaravel11以降に作られたプロジェクト、もしくは新構造に移行したプロジェクト。違うなら旧構造のままアップグレードしたプロジェクト。
  - 日本語版はOKなので英語ページを作成。 advanced/app-structure-faq.mdx

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

## packages ページ案
- [x] Laravel Notification for Discord(Webhook) https://github.com/invokable/laravel-notification-discord-webhook
  - Discordに通知する単機能パッケージのWebhook版。
  - いつもの投稿のためのBasic client＋通知機能ではなく、Webhookなのでいきなり通知が可能。
  - 本来のDiscord APIはWebSocketが必要で複雑だけどWebhook版は一切不要で簡単。
  - 仮で`SDK`グループに追加。
- [x] Socialite for Discord https://github.com/invokable/socialite-discord
  - Socialite用のDiscordドライバー。Socialiteドライバーを作るのは簡単なのでOAuth機能があり自分で使うことがあるサービスならすぐに作っている。
  - `jp/socialite.mdx`で公式ドキュメントにあるSocialite Providersの記述を全部消して`Socialite::extend()`で拡張する正規の方法を書いてるのは確実にこの方法が正しいから。Socialite Providersにすでに同じドライバーがあっても関係なく自分で作っている。
- [x] LINE SDK for Laravel https://github.com/invokable/laravel-line-sdk
