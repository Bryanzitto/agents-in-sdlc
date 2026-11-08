---
title: "演習 3 - カスタムエージェント"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

## カスタムエージェントとは

[カスタムエージェント][custom-agents-concept]は、特定のタスクやドメイン向けに調整した AI アシスタントです。リポジトリの `.github/agents` に Markdown ファイルを置き、専門知識、ベストプラクティス、コーディングパターンを定義します。

カスタムエージェントはプロジェクトの `.github/agents`、または `~/.copilot/agents` に Markdown ファイルとして定義します。各ファイルには少なくとも `name` と `description` を含む YAML フロントマターが必要です。

アクセシビリティ、セキュリティ、テストなどの専門知識を再利用可能なエージェントとしてチームでコード化できます。カスタムエージェントは作業者、スキルはツールです。エージェントには独自のコンテキストウィンドウがあり、スキルや他のエージェントを調整できます。

### カスタムエージェントとエージェントスキルの比較

カスタムエージェントは作業者、[スキル][agent-skills-concept]はツールと考えると分かりやすいでしょう。カスタムエージェントは独自のコンテキストウィンドウを持ち、スキルや他のエージェントを組み合わせて作業できます。

> [!NOTE]
> カスタムエージェントの作成方法に唯一の正解はありません。環境とシナリオに合わせてテストと反復を行ってください。

## この演習で行うこと

- カスタムエージェントの定義方法を確認します。
- カスタムエージェントにタスクを割り当てます。

## シナリオ

Tailspin Toys は、視覚能力や好みに関係なく誰もが使えるクラウドファンディングプラットフォームを目指しています。現在のダークテーマは文字と背景のコントラストが不足して読みにくいというフィードバックがありました。そこで、オン・オフを切り替えられるハイコントラストモードを追加します。

## アクセシビリティ用カスタムエージェントを確認する

Codespace に戻り、`.github/agents/accessibility.md` を開きます。

1. `name` と `description` の YAML フロントマターを確認します。
2. アクセシブルなサイトの生成責務、ベストプラクティス、HTML・CSS・JavaScript の例、よくある問題を確認します。

> [!CAUTION]
> カスタムエージェントには `name` と `description` のフロントマターが必須です。

## Issue を作成して割り当てる

1. リポジトリの **Issues** タブを開き、**New issue**、**Blank issue** の順に選択します。
2. タイトルに `Add high contrast mode to website` と入力します。
3. 説明に次を入力します。

   ```plaintext
   We need a high contrast mode for the site. There should be a toggle for high contrast which the user can set. It should store the setting in local storage on the browser.
   ```

4. **Create**、**Assign to Copilot**、**Accessibility agent**、**Assign** の順に選択します。

![カスタムエージェントを選択する Copilot の割り当て画面](../../../_images/ex5-select-custom-agent.png)

## まとめと次のステップ

カスタムエージェントが専門的な作業を導く方法を確認しました。次に、[エージェントセッションを監視して誘導します][next-lesson]。

## リソース

- [カスタムエージェントについて][custom-agents]
- [組織でカスタムエージェントを準備する][org-custom-agents]
- [エンタープライズでカスタムエージェントを準備する][enterprise-custom-agents]

[previous-lesson]: ../2-cloud-agent/
[next-lesson]: ../4-managing-agents/
[custom-agents-concept]: https://docs.github.com/copilot/concepts/agents/cloud-agent/about-custom-agents
[agent-skills-concept]: https://docs.github.com/copilot/concepts/agents/about-agent-skills
[wcag]: https://www.w3.org/WAI/standards-guidelines/wcag/
[custom-agents]: https://docs.github.com/copilot/concepts/agents/cloud-agent/about-custom-agents
[org-custom-agents]: https://docs.github.com/copilot/how-tos/administer-copilot/manage-for-organization/prepare-for-custom-agents
[enterprise-custom-agents]: https://docs.github.com/copilot/how-tos/administer-copilot/manage-for-enterprise/manage-agents/prepare-for-custom-agents
