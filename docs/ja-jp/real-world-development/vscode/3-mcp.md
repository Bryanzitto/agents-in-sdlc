---
title: "演習 3 - Playwright MCP サーバーで機能をテストする"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

[← 前のレッスン：Agent Mode][previous-lesson] · [次のレッスン：カスタムエージェント →][next-lesson]

## Model Context Protocol (MCP) とは

MCP は、Copilot が外部ツールやサービスと通信するための標準です。MCP サーバーは AI エージェントとツールの橋渡しをします。

![コンテキスト、LLM、ツールと MCP サーバーの関係を示す図](../../../_images/ex1-mcp-diagram.png)

GitHub MCP Server はリポジトリ、Issue、PR を操作し、Playwright MCP Server はページ移動、フォーム入力、ボタン選択などのブラウザー操作を提供します。MCP サーバーは依存関係と同様にソース、発行者、権限を確認して信頼できるものだけを使います。

## MCP の設定を確認する

`.vscode/mcp.json` に既存の `github` サーバーがあります。

```json
{
  "servers": {
    "github": {
      "type": "http",
      "url": "https://api.githubcopilot.com/mcp/"
    }
  }
}
```

## Playwright MCP サーバーを追加する

`playwright` エントリを追加します。

```json
{
  "servers": {
    "github": {
      "type": "http",
      "url": "https://api.githubcopilot.com/mcp/"
    },
    "playwright": {
      "command": "npx",
      "args": ["@playwright/mcp@latest", "--headless"]
    }
  }
}
```

## サーバーを起動して信頼する

`playwright` の上に表示される **Start** を選択し、設定を確認してサーバーを信頼します。

## フィルタリング機能をテストする

[Playwright MCP サーバー][playwright-mcp-server]を使い、`http://localhost:4321` でカテゴリ、パブリッシャー、両方のフィルターを確認します。

Playwright MCP はスクリーンショットではなくページのアクセシビリティツリーを使うため、構造化されたラベル付き要素を通じて機能とアクセシビリティを簡単に確認できます。アプリが `http://localhost:4321` で実行されていることを確認し、ブラウザーがない場合は `npx playwright install chromium` を実行します。

```text
Using the Playwright MCP server, open a browser to the running app at http://localhost:4321 and verify the new game filtering feature:

1. Go to the games page and note how many games are listed.
2. Apply a category filter and confirm the list updates to only show games in that category.
3. Clear it, then apply a publisher filter and confirm the list updates to that publisher.
4. Combine a category and a publisher filter and confirm the results respect both.
```

## ブランチを公開して PR を作成する

Source Control で変更を確認し、ステージ、コミット、**Publish** の順に操作します。その後 Copilot に次を依頼します。

![Source Control パネルで変更を確認する画面](../../../_images/ex3-source-control-changes.png)

```plaintext
Find the issue in the repo related to filtering by category and publisher. Create a new pull request for the current branch, and associate it with the correct issue.
```

## まとめと次のステップ

MCP と Playwright MCP サーバーを使ってブラウザーで機能をテストし、ブランチを公開して PR を作成しました。次に [カスタムエージェント][next-lesson]を作成します。

## リソース

- [MCP とは何か][mcp-blog-post]
- [Microsoft Playwright MCP Server][playwright-mcp-server]
- [GitHub MCP Server][github-mcp-server]
- [GitHub MCP Registry][mcp-registry]
- [VS Code の MCP サーバー設定][vscode-mcp-config]

[previous-lesson]: ../2-agent-mode/
[next-lesson]: ../4-custom-agents/
[playwright-mcp-server]: https://github.com/microsoft/playwright-mcp
[mcp-blog-post]: https://github.blog/ai-and-ml/llms/what-the-heck-is-mcp-and-why-is-everyone-talking-about-it/
[github-mcp-server]: https://github.com/github/github-mcp-server
[mcp-registry]: https://github.com/mcp
[remote-github-mcp-server]: https://github.blog/changelog/2025-06-12-remote-github-mcp-server-is-now-available-in-public-preview/
[vscode-mcp-config]: https://code.visualstudio.com/docs/agents/reference/mcp-configuration
