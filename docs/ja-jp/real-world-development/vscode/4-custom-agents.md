---
title: "演習 4 - カスタムエージェント"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

## カスタムエージェントとは

[カスタムエージェント][custom-agents-concept]は、特定のタスクやドメイン向けに調整された AI アシスタントです。`.github/agents` の Markdown ファイルで、専門知識、ベストプラクティス、指示を定義します。

各ファイルには少なくとも `name` と `description` を含む YAML フロントマターが必要です。アクセシビリティ、セキュリティ、テストなどの知識を再利用できます。

## シナリオ

Tailspin Toys では、コントラスト不足を解決するため、ユーザーが切り替えられるハイコントラストモードを追加します。

## アクセシビリティ用カスタムエージェントを確認する

`.github/agents/accessibility.md` を開き、`name` と `description` の YAML フロントマター、アクセシビリティの責務、例、よくある問題を確認します。

確認する内容には、アクセシブルなサイトの生成責務、HTML・CSS・JavaScript のコード例、アクセシビリティのベストプラクティスが含まれます。作業用に `main` から `accessibility-vscode` ブランチを作成します。

> [!CAUTION]
> カスタムエージェントには `name` と `description` のフロントマターが必須です。

## Copilot Chat でカスタムエージェントを使う

**Agent** を選択し、エージェントの一覧から **Accessibility agent** を選択して、次のプロンプトを送信します。

![Copilot Chat のエージェント選択](../../../_images/shared-chat-mode-selector.png)

```plaintext
Add a high-contrast mode to the site. There should be a toggle for high contrast which the user can set, and the setting should persist across page reloads using local storage on the browser.
```

変更を確認し、次の演習でセッションを監視します。

エージェントは `.github/agents` に定義されたすべてのカスタムエージェントとして VS Code の一覧に表示されます。チャット内の **Files changed** で編集されたファイルを確認し、必要なら各差分をレビューします。

Copilot はコードベースを調査し、Astro コンポーネント、CSS、関連テストを編集します。変更はチャット内の差分で確認できます。

## まとめと次のステップ

カスタムエージェントを Copilot Chat の Agent Mode で使い、アクセシビリティ機能を実装しました。次に [エージェントの作業を監視して誘導します][next-lesson]。

## リソース

- [カスタムエージェントについて][custom-agents]
- [IDE でカスタムエージェントを作成する][creating-custom-agents-ide]
- [VS Code のカスタムエージェント][custom-agents-vscode]
- [カスタムエージェントの設定][custom-agents-config]
- [awesome-copilot のカスタムエージェント][awesome-copilot-agents]

[previous-lesson]: ../3-mcp/
[next-lesson]: ../5-managing-agents/
[custom-agents]: https://docs.github.com/copilot/concepts/agents/cloud-agent/about-custom-agents
[custom-agents-concept]: https://docs.github.com/copilot/concepts/agents/cloud-agent/about-custom-agents
[creating-custom-agents-ide]: https://docs.github.com/copilot/how-tos/use-copilot-agents/cloud-agent/create-custom-agents-in-your-ide
[custom-agents-vscode]: https://code.visualstudio.com/docs/copilot/customization/custom-agents
[custom-agents-config]: https://docs.github.com/copilot/reference/custom-agents-configuration
[awesome-copilot-agents]: https://github.com/github/awesome-copilot/tree/main/agents
