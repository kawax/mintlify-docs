# GitHub Agentic Workflows

## awがバージョンアップした時の作業

PhpStormなら「>>」で直接実行。

```shell
# プロジェクトルートで実行
cd ../
# awを更新
gh extension upgrade github/gh-aw
# workflowを更新
gh aw upgrade
# upgradeで更新されないファイルを更新
gh aw compile
```

```shell
cd ../ && gh extension upgrade github/gh-aw && gh aw upgrade && gh aw compile
```

AWからissueを作ってCopilotをアサインしてクラウドエージェントを起動、はまれに失敗する。
GitHub側が原因なので直るまで待つ。
手動でCopilotのアサインを解除して再度アサインすればクラウドエージェントが起動する。
