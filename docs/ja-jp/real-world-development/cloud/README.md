---
slug: ja-jp/real-world-development/cloud
title: "GitHub Copilot クラウドエージェント"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

**[GitHub Copilot クラウドエージェント](https://docs.github.com/copilot/concepts/agents/cloud-agent/about-cloud-agent)** を使うと、GitHub Copilot をクラウドで非同期に動作させられます。GitHub で作業を割り当てると、クラウドエージェントがバックグラウンドでリポジトリを調査し、変更を行い、プルリクエストを作成します。

これらの演習では、クラウドエージェントが従うカスタム手順を追加し、GitHub Issue を割り当てて実装させます。カスタムエージェントを使って方針を定め、エージェントダッシュボードからセッションを監視・誘導し、最後にプルリクエストを確認して結果を反復改善します。

## 演習

| 演習 | トピック | 説明 |
|----------|-------|-------------|
| [0. 前提条件][ex0] | セットアップ | リポジトリと Codespace を作成する |
| [1. カスタム手順][ex1] | コンテキスト | クラウドエージェントが従うカスタム手順を追加する |
| [2. クラウドエージェント][ex2] | 非同期エージェント | Issue を Copilot クラウドエージェントに割り当てる |
| [3. カスタムエージェント][ex3] | 専門エージェント | カスタムエージェントを確認して使う |
| [4. エージェントの管理][ex4] | 監視 | エージェントセッションを監視して誘導する |
| [5. 反復][ex5] | レビュー | PR を確認し、Copilot の作業を反復して次の手順を選ぶ |

## 前提条件

このワークショップを始める前に、次を確認してください。

- [ ] 有効な **Copilot Student、Pro、Pro+、Business、Enterprise** プランの GitHub アカウント
- [ ] アカウントまたは組織で Copilot クラウドエージェントが有効になっていること

> [!TIP]
> 有料プランを利用していない場合でも、認証済みの学生は [GitHub Education][callout-student-plan-education] から GitHub Copilot を無料で利用できます。
> **Copilot Student** プランには、このワークショップで使うエージェント、MCP、コードレビュー、Copilot CLI の機能が含まれるため、すべてのハーネスを完了できます。

[callout-student-plan-education]: https://github.com/education/students

> [!NOTE]
> クラウドエージェントは Copilot Free を除く **Copilot Student、Pro、Pro+、Business、Enterprise** で利用できます。Business または Enterprise では管理者が組織で有効にする必要があります。

> [!NOTE]
> このハーネスでは MCP を扱いません。Copilot で MCP サーバーを使う方法については、[CLI ハーネス](../cli/)または [VS Code ハーネス](../vscode/)を参照してください。

## 開始する

**[演習 0：前提条件から始める →][ex0]**

[ex0]: 0-prerequisites/
[ex1]: 1-custom-instructions/
[ex2]: 2-cloud-agent/
[ex3]: 3-custom-agents/
[ex4]: 4-managing-agents/
[ex5]: 5-iterating/
