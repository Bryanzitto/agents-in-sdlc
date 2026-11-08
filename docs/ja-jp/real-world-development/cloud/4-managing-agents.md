---
title: "演習 4 - エージェントの監視と管理"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

クラウドエージェントは非同期かつ自律的に動作しますが、タスクを監視することも重要です。GitHub の [エージェントページ][agents-page]では、実行中のタスク、PR、操作内容を確認し、セッションを誘導できます。

## シナリオ

ハイコントラストモードの作業中に、デザインチームからライトモードも追加したいという要望がありました。既存のセッションを誘導して、両方のモードを追加します。

## Copilot クラウドエージェントのタスクを確認する

1. [Copilot エージェントページ](https://github.com/copilot/agents)を開きます。
2. ドキュメント更新、ゲーム API、ハイコントラストモードなどのタスクを確認します。
3. 実行中のタスクを選択し、コードのチェックアウト、環境の作成、MCP サーバーの設定などの操作を確認します。

正確な手順は Copilot の作業状態と採用した方法によって異なります。右側の PR ペインでは、PR と変更されたファイルも確認できます。

## クラウドエージェントを誘導する

1. ハイコントラストモードのセッションを選択します。
   
   ![ミッションコントロールのアクセシビリティセッション](../../../_images/ex6-accessibility-session.png)
2. **Steer active session while Copilot is working** ダイアログに次のプロンプトを入力します。

   ```plaintext
   While we are working on a high contrast mode, let's also add a light mode. There should be a switch for this mode as well where users can select their desired display mode.
   ```

3. <kbd>Enter</kbd> を押して送信します。

4. Copilot がプロンプトを確認し、作業の流れに追加することを確認します。

![Copilot のアクティブセッションを誘導するダイアログ](../../../_images/ex6-steer-cloud-agent-task.png)

## Copilot に作業を任せる

Copilot は現在のステップが終わった後に新しい要求を作業へ反映します。完了するまで数分待ちます。

## まとめと次のステップ

エージェントページでタスクを監視し、実行中のセッションへ機能追加を依頼する方法を学びました。次に、[Copilot が作成した PR を反復します][next-lesson]。

## リソース

- [Copilot エージェントページ][agents-page]
- [カスタムエージェントについて][custom-agents]

[previous-lesson]: ../3-custom-agents/
[next-lesson]: ../5-iterating/
[agents-page]: https://github.blog/changelog/2025-07-03-agents-page-for-copilot-coding-agent-in-public-preview
[custom-agents]: https://docs.github.com/copilot/concepts/agents/cloud-agent/about-custom-agents
