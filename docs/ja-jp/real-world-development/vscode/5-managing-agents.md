---
title: "演習 5 - エージェントの監視と管理"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

Copilot Chat の Agent Mode では、ツール呼び出しやファイル編集をリアルタイムで確認し、変更を受け入れたり取り消したりできます。

エージェントが調査したファイル、実行したコマンド、提案した編集を確認し、必要なターミナル操作には **Allow** を選択します。

## シナリオ

ハイコントラストモードの作業中に、ライトモードも追加します。同じセッションを誘導して、両方を独立して切り替えられるようにします。

## Copilot の進行状況を監視する

1. Copilot Chat ビューに戻ります。
2. ツール呼び出し、ファイル読み取り、編集、ターミナルコマンドを確認します。
3. 変更を受け入れるには **Keep**、取り消すには **Undo** を選択します。
4. **Files changed** で変更されたファイルを確認します。

5. 高コントラストモードの実装が完了するまで待ち、最終メッセージの概要を確認します。

## エージェントを誘導してライトモードを追加する

次のフォローアッププロンプトを送信します。

```plaintext
Nice work! Now add a light-mode toggle alongside the high-contrast toggle. Light mode should follow the same pattern — persist via local storage and be accessible from the same area of the UI. The user should be able to enable high-contrast and light mode independently.
```

各差分を確認し、必要なら **Stop** を選択して方針を説明する追加メッセージを送信します。

同じセッションでは、既存のコンポーネント、スタイル、ローカルストレージのパターンをエージェントが把握しています。ライトモードと高コントラストモードは独立して有効化できる必要があります。

> [!TIP]
> 実行中のセッションを誘導すると、コンテキストを保ったまま調整や追加ができます。

## 変更セットを確認する

Source Control ビューで変更されたファイルを確認し、ARIA 属性、キーボード操作、セマンティック HTML、ローカルストレージによる永続化が実装されていることを確認します。

満足したら変更をステージしてコミットします。次のレッスンでブランチを公開し、PR を作成します。

## まとめと次のステップ

Agent Mode のセッションを監視し、変更を受け入れたり取り消したりしながら、フォローアッププロンプトでライトモードを追加しました。次に [Copilot の作業を公開して確認します][next-lesson]。

## リソース

- [VS Code の Copilot Chat][copilot-chat-vscode]
- [Agent Mode の使用][agent-mode]

[previous-lesson]: ../4-custom-agents/
[next-lesson]: ../6-iterating/
[copilot-chat-vscode]: https://code.visualstudio.com/docs/copilot/chat/copilot-chat
[agent-mode]: https://code.visualstudio.com/docs/copilot/chat/chat-agent-mode
