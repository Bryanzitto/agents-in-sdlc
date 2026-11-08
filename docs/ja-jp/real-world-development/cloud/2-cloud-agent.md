---
title: "演習 2 - GitHub Copilot クラウドエージェント"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

技術的負債には、未解決のセキュリティ問題、更新が必要なレガシーコード、バックログに残った機能要求などがあります。GitHub Copilot のクラウドエージェントは、コード更新や機能追加を自律的に行い、完了するとレビュー用のドラフト PR を作成します。

## シナリオ

Tailspin Toys では、エクスポートされた関数に TSDoc コメントを追加し、ゲーム詳細ページに同じカテゴリの関連ゲームを表示します。どちらもクラウドエージェントに非同期で割り当てられる作業です。

クラウドエージェントは、作業完了後に人間がレビューできるドラフト PR を作成します。これにより、面倒な作業を委任し、開発者はより大きな課題に集中できます。

## GitHub Copilot クラウドエージェントを紹介する

[GitHub Copilot クラウドエージェント](https://docs.github.com/copilot/concepts/agents/cloud-agent/about-cloud-agent#overview-of-copilot-cloud-agent-formerly-copilot-coding-agent) はバックグラウンドで作業し、Issue を割り当てると環境を準備してドラフトプルリクエストを作成します。

セッション中または完了後に進行状況を確認でき、レビューの準備ができると PR で通知されます。

## 適切な範囲の手順の重要性

Copilot に思考を任せるだけでは不十分です。[クラウドエージェントのタスク範囲の決め方][cloud-agent-best-practices]を確認し、AI ペアプログラマーとして段階的に作業してください。

セキュリティ問題、レガシーコード、長期間バックログに残った機能要求など、優先順位が下がりやすい作業に適しています。

## このリポジトリのカスタム手順

`.github/copilot-instructions.md` の **Code standards** と、`**/*.test.ts` に適用される `.github/instructions/unit-tests.instructions.md` を確認します。

## クラウドエージェントの開発環境を設定する

クラウドエージェントは GitHub Actions の `.github/workflows/copilot-setup-steps.yml` を使って環境を準備します。

```yaml
name: "Copilot Setup Steps"
on: workflow_dispatch
```

このワークフローでは、依存関係、Playwright ブラウザー、ローカル SQLite データベースを準備します。

完全な設定には、`ubuntu-latest`、`contents: read`、Node.js のセットアップ、`npm ci`、`npx playwright install --with-deps chromium`、`npm run db:setup` が含まれます。`copilot-setup-steps` ジョブは Copilot が PR で作業を開始する前に実行され、`workflow_dispatch` により **Actions** タブから手動実行できます。

```yaml
name: "Copilot Setup Steps"

# Allows you to test the setup steps from your repository's "Actions" tab
on: workflow_dispatch

env:
  ASTRO_TELEMETRY_DISABLED: "1"

jobs:
  copilot-setup-steps:
    runs-on: ubuntu-latest
    permissions:
      contents: read
    steps:
      - name: Checkout code
        uses: actions/checkout@v5
      - name: Set up Node.js
        uses: actions/setup-node@v6
        with:
          node-version: "lts/*"
          cache: "npm"
          cache-dependency-path: "./package-lock.json"
      - name: Install JavaScript dependencies
        run: npm ci
      - name: Install Playwright browsers
        run: npx playwright install --with-deps chromium
      - name: Set up the database
        run: npm run db:setup
```

## ドキュメントを追加する

Issue の説明に次を入力します。

```plaintext
Our organization has a requirement that functions and methods include TSDoc doc comments where helpful. Unfortunately, recent updates haven't followed this standard. We need to update the existing code to ensure doc comments are included where they clarify behavior.
```

1. リポジトリの **Issues** タブで `Code lacks documentation` という Issue を作成します。
2. **Assign to Copilot** を選択し、生成された PR とセッションを確認します。
3. Copilot の TODO リストと作業の進行状況を確認します。

![Copilot を Issue に割り当てる画面](../../../_images/shared-assign-copilot.png)

![Copilot の割り当て詳細](../../../_images/ex4-assign-copilot-details.png)

![Copilot セッションビュー](../../../_images/ex4-view-session.png)

Issue の説明には、役立つ場所で関数とメソッドに TSDoc コメントを追加する要件を記述します。PR では TSDoc コメント、TypeScript 規約、コメントヘッダーを確認し、必要ならワークフローを承認して実行します。

## ゲーム詳細ページに関連ゲームを追加する

別の Issue で、同じカテゴリのゲームを返すデータアクセスヘルパー、詳細ページの **Related games** セクション、関連ゲームがない場合の処理、単体テストを依頼します。

Issue の説明には次を入力します。

```markdown
We want to help people discover more games by showing related games on each game's details page. The design team wants to explore the UX and do some acceptance testing. Our requirements are:

- Add a data-access helper in `src/lib/` that returns other games in the same category as a given game, excluding that game
- Show a "Related games" section on the game details page that uses the helper
- Handle the case where a game has no related games
- There should be unit tests created for the new helper
- Before creating the PR, ensure all tests pass
```

Issue の説明には次の要件を含めます。

- `src/lib/` に、指定したゲームを除外して同じカテゴリのゲームを返すデータアクセスヘルパーを追加する。
- ヘルパーを使う **Related games** セクションをゲーム詳細ページに表示する。
- 関連ゲームがない場合を処理する。
- 新しいヘルパーの単体テストを作成する。
- PR を作成する前にすべてのテストが成功することを確認する。

作成後、最初のコメントに Copilot が作業中であることを示す目の絵文字が表示されます。

![Copilot が Issue で作業中であることを示す目の絵文字](../../../_images/ex4-issue-eyes-emoji.png)

## まとめと次のステップ

クラウドエージェントを使って Issue を非同期に処理し、環境を設定し、明確な範囲のタスクを割り当てる方法を学びました。次に、[カスタムエージェント][next-lesson]を確認します。

## リソース

- [GitHub Copilot クラウドエージェントについて][copilot-agents]
- [GitHub Issue を Copilot に割り当てる][assign-issue]
- [クラウドエージェントのセットアップワークフローのベストプラクティス][cloud-agent-best-practices]

[previous-lesson]: ../1-custom-instructions/
[next-lesson]: ../3-custom-agents/
[cloud-agent-best-practices]: https://docs.github.com/copilot/how-tos/copilot-on-github/customize-copilot/customize-cloud-agent/customize-the-agent-environment
[copilot-agents]: https://docs.github.com/copilot/concepts/agents/cloud-agent/about-cloud-agent
[assign-issue]: https://docs.github.com/copilot/how-tos/use-copilot-agents/cloud-agent/start-copilot-sessions
