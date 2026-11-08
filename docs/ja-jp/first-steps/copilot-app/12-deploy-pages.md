---
title: "レッスン 12 - GitHub Pages でサイトをデプロイする"
description: "GitHub Copilot アプリで Pages ワークフローを設定し、プルリクエストを確認して、公開された Space Quiz を検証します。"
authors:
  - jamesmontemagno
lastUpdated: 2026-10-12
---

GitHub Pages にデプロイして、Space Quiz を公開します。Copilot はワークフローを準備してデプロイを案内できますが、変更を確認し、サイトが公開されたことを確認する責任は利用者にあります。

このレッスンでは、次の操作を行います。

- Copilot に GitHub Pages のデプロイを設定させます。
- マージ前にワークフローとプルリクエストを確認します。
- デプロイを追跡し、公開されたサイトを検証します。

## シナリオ

Space Quiz はすでに GitHub リポジトリにありますが、簡単に試す方法が必要です。単一ファイルのサイトを GitHub Pages で公開すれば、サーバーやランタイム依存関係を追加せずに公開 URL から利用できます。

## Copilot にサイトのデプロイを依頼する

`space-quiz` の Copilot アプリセッションで、次のプロンプトを送信します。

```plaintext
Enable GitHub Pages for this repository. Create a GitHub Actions workflow that builds the website if needed and deploys it to GitHub Pages. Add a README describing the app and how to run it locally if one does not already exist. Create a pull request with these changes and merge it after required checks pass. Monitor the deployment until it succeeds, then report the final URL of the live website. If you lack permission to enable Pages or merge, tell me exactly what I need to approve or do; do not report success until the site is live.
```

![3 段階の図：マージ済みの space-quiz プルリクエスト、Build website・Upload artifact・Deploy to Pages の各ステップが成功した GitHub Actions のデプロイ実行、yourname.github.io/space-quiz/ に表示された Space Quiz。](../../../_images/first-steps-app-pages-deploy.svg)

> [!WARNING]
> このプロンプトは、エージェントにプルリクエストの作成とマージ、およびリポジトリの Pages 設定の変更を依頼します。続行する前に、差分、デプロイ権限、GitHub の承認プロンプトを確認してください。

## ワークフローを確認してデプロイを検証する

1. リポジトリに README がまだない場合にだけ、README が追加されていることを確認します。
2. ワークフローのビルド手順とデプロイ手順を含め、プルリクエストの変更を確認します。
3. 必須のプルリクエストチェックが成功してからマージします。
4. GitHub Actions のデプロイ実行が成功するまで追跡します。
5. 報告された URL を開き、Space Quiz が読み込まれることを確認します。

エージェントが Pages を有効にできない場合やプルリクエストをマージできない場合は、エージェントが示す具体的な手順に従います。デプロイが成功し、公開サイトが読み込まれるまで、作業完了とはみなさないでください。

## まとめと次のステップ

Space Quiz が公開サイトとして利用できるようになり、エージェントの報告だけに頼らずデプロイを検証できました。次に、[レッスン 13：レビューと次のステップ][next-lesson]に進みます。

[next-lesson]: ../13-review/
