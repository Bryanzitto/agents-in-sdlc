---
title: "演習 5：GitHub Copilot の作業を反復する"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

## 作業を確認する

Copilot にドキュメント、関連ゲーム機能、アクセシビリティ機能を実装させました。生成されたコードを通常の DevOps プロセスで確認し、必要ならフィードバックを送ります。

### シナリオ

生成 AI を使っても、設計と DevOps の基本は変わりません。コードを確認し、テストを実行し、チームのレビュー手順を守ります。

## セキュリティと GitHub Copilot クラウドエージェント

- Copilot はリポジトリへの読み取りアクセスと、作業ブランチへの書き込みアクセスだけを持ちます。
- クラウドエージェントは GitHub Actions の一時環境で動作します。
- GitHub Actions ワークフローは、人間の承認後に実行されます。
- MCP サーバーを含む外部リソースへのアクセスは既定で制限されます。

外部 MCP サーバーへのアクセスがファイアウォールでブロックされたという警告は想定された動作です。必要なら[クラウドエージェントのファイアウォールをカスタマイズまたは無効化][agent-firewall]できます。

## 生成されたドキュメントを確認する

1. リポジトリの **Pull Requests** タブを開きます。
2. ドキュメント追加の PR を開きます。
3. **Files changed** タブで TSDoc コメント、TypeScript 規約、コメントヘッダーを確認します。
4. ワークフローの承認が必要な場合は **Approve and run workflows** を選択します。

![ワークフローを承認して実行](../../../_images/shared-approve-workflows.png)

Copilot がまだ作業中なら PR タイトルに **[WIP]** が付きます。完了するまで待ち、**Files changed** タブで変更を確認します。

変更には TSDoc コメント、TypeScript 規約、コメントヘッダーが含まれます。**Conversation** タブに戻り、保留中のワークフローがあれば **Approve and run workflows** を選択します。チェックが成功するまで数分待ちます。

## GitHub Copilot に変更を依頼する

PR のコメントで **@copilot** をメンションし、コメントヘッダーや TSDoc コメントの追加などを依頼できます。**View Session** を選択して作業を確認し、完了後に差分を再確認します。

たとえば、各コードファイルへのコメントヘッダー、TypeScript と Astro ファイルへの TSDoc コメント、Astro アプリ構造を説明する README の追加を依頼できます。Copilot はコメントを確認して新しいセッションを開始します。満足したらドラフト PR をレビュー可能な状態に変更してマージします。

![プルリクエストに戻る](../../../_images/ex7-back-to-pr.png)

![PR をレビュー可能な状態に変更](../../../_images/ex7-ready-for-review.png)

## 関連ゲーム機能を確認する

関連ゲームの PR を開き、**Files changed** とワークフローを確認します。必要に応じて Codespace でブランチをチェックアウトし、次のコマンドを実行します。

```bash
git fetch origin
git checkout <branch-name>
```

![プルリクエストの Files changed タブ](../../../_images/shared-pr-files-changed.png)

## アクセシビリティ機能を確認する

ハイコントラストとライトモードの PR で、トグル UI、ローカルストレージ、CSS、ARIA 属性、キーボード操作を確認します。

この PR には、演習 3 で依頼したハイコントラストモードと、ミッションコントロールで依頼したライトモードの両方が含まれている必要があります。必要なら **Conversation** タブでワークフローを承認し、チェックが成功するまで待ちます。

必要なら Codespace で Copilot が作成したブランチをチェックアウトし、ページを再読み込みして設定が保持されることを手動で確認します。

## まとめ

クラウドエージェントの PR を確認し、コメントで変更を依頼し、ワークフローを承認して結果を反復する方法を学びました。

### 任意の演習 — 委任を続ける

ゲーム詳細ページに支援者向けフォームを追加する、ゲーム一覧にページネーションを追加する、データアクセスヘルパーに入力検証とエラー処理を追加する Issue を作成して Copilot に割り当ててみてください。

## レビューと次のステップ

他のハーネスでは VS Code の Agent Mode と MCP、CLI の Plan と Autopilot、エージェントスキル、QA エージェント、Playwright MCP、Agent Merge を扱います。

## リソース

- [GitHub Copilot][github-copilot]
- [Copilot エージェントについて][copilot-agents]
- [GitHub Issue を Copilot に割り当てる][assign-issue]
- [クラウドエージェントのセットアップワークフローのベストプラクティス][cloud-agent-best-practices]
- [クラウドエージェントのファイアウォールを設定する][agent-firewall]

[previous-lesson]: ../4-managing-agents/
[github-copilot]: https://github.com/features/copilot
[copilot-agents]: https://docs.github.com/copilot/concepts/agents/cloud-agent/about-cloud-agent
[assign-issue]: https://docs.github.com/copilot/how-tos/use-copilot-agents/cloud-agent/start-copilot-sessions
[agent-firewall]: https://docs.github.com/copilot/how-tos/copilot-on-github/customize-copilot/customize-cloud-agent/customize-the-agent-firewall
[cloud-agent-best-practices]: https://docs.github.com/copilot/how-tos/copilot-on-github/customize-copilot/customize-cloud-agent/customize-the-agent-environment
