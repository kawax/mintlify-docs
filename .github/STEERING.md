# Steering

このファイルは人間が編集し、「今後はこういうページを増やす」や「このページが間違ってるので修正」の細かい指示を出すためのものです。
対応が終わったら`[x]`で完了にしてください。

- [x] チュートリアルを複数ページ構成で作成していく。
- [x] Laravelの現在のバージョンは13。初回の実行から12と誤認。毎年3月頃にバージョンアップするのでモデルの知識だけではどうしても遅れてしまう。copilot-instructions.md にGitHub MCPで調べる方法を書いた。影響は`jp/tutorial/installation.mdx`で`PHP 8.2以上`と書いてたくらいなので8.3に修正した。他は将来的な既存ページの更新時に対応。
- [x] `jp/tutorial/installation.mdx`は`スターターキット（Breeze、Jetstream）`もモデルの古い知識で書いて間違っていた。Laravel12リリースと同時にBreeze、Jetstreamではなく完全に新しいスターターキットが導入されている。詳細はdocsの`starter-kits.md`
- [x] Mintlifyのデフォルトページは削除済み
- [ ] 現在は月末でCopilotのプレミアムリクエストが余っているのでしばらく手動でCommanderを実行してページを増やしていく。同時に複数のissueを作ってもいいので積極的に稼働。
- [ ] Commanderにより中級ページの追加開始
