---
title: "演習 2 - Copilot Agent Mode で新機能を追加する"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

Copilot Agent Mode は、プロジェクトを調査し、複数ファイルを更新し、テストを実行して問題を修正します。クラウドエージェントが非同期に動作するのに対し、Agent Mode は IDE 内で対話的に動作します。

## シナリオ

ゲームが増えたため、カテゴリとパブリッシャーで絞り込めるようにします。

Agent Mode は関連ファイルを探し、UI とデータ層を更新し、テストを実行して必要なら修正します。クラウドエージェントとは異なり IDE 内で動作するため、短いフィードバックサイクルで確認できます。

## Tailspin Toys サイトを実行する

```bash
git checkout main
git pull
git checkout -b filtering-vscode
npm run dev
```

ブラウザーで `http://localhost:4321` を開き、ホームページとゲーム詳細ページを確認します。

サイトは静的 HTML をビルド時に生成する単一の Astro アプリです。ページは frontmatter から Drizzle ORM 経由でローカル SQLite データベースを直接参照し、再利用可能なデータアクセスヘルパーは `src/lib/` にあります。

## Copilot でバックログを確認する

**Agent** を選択し、次のプロンプトを送信します。

![Copilot Chat のエージェント選択](../../../_images/shared-chat-mode-selector.png)

```plaintext
Please show me the backlog of items from my GitHub repository. Help me prioritize them based on those which will be most useful to the user.
```

## フィルタリング機能を実装する

必要な変更は、`src/lib/` のデータ層ロジック、フィルター動作のテスト、ゲーム一覧ページの UI の 3 つです。マージ前にテストを成功させます。

`.github/instructions/ui.instructions.md` をコンテキストに追加し、次のプロンプトを送信します。

```plaintext
Please update the site to include filtering by publisher and category based on the requirements from the related GitHub issue in the backlog. A publishers helper already exists from the previous exercise, so preserve and refine that work as needed while completing the remaining data-layer, UI, and tests. Ensure all tests are passing before completion. The server is already running, so you do not need to start it up.
```

生成されたコードを確認し、テストが成功したら **Keep** を選択します。

![Copilot がプロジェクトを調査する様子](../../../_images/ex3-agent-mode-explores.png)

![Copilot Chat でテスト実行を確認するダイアログ](../../../_images/ex3-agent-mode-run-tests.png)

![Copilot Agent Mode の完了したチャットセッション](../../../_images/ex3-agent-mode-proposed-changes.png)

途中でテストが失敗しても、Copilot はコード生成とテストを繰り返して問題を修正します。生成コードを確認してから **Keep** を選択してください。

## まとめと次のステップ

Agent Mode で UI、データ層、テストをまたいだ機能を実装しました。次に [Playwright MCP サーバー][next-lesson]で機能をテストします。

## リソース

- [Copilot の ask、edit、agent モード][choose-mode]
- [VS Code の Agent Mode][vs-code-agent-mode]

[previous-lesson]: ../1-custom-instructions/
[next-lesson]: ../3-mcp/
[choose-mode]: https://github.blog/ai-and-ml/github-copilot/copilot-ask-edit-and-agent-modes-what-they-do-and-when-to-use-them/
[vs-code-agent-mode]: https://code.visualstudio.com/docs/copilot/chat/chat-agent-mode
