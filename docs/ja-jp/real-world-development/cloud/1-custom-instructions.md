---
title: "演習 1 - カスタム手順（クラウドエージェント）"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

[← 前のレッスン：前提条件][previous-lesson] · [次のレッスン：Copilot クラウドエージェント →][next-lesson]

生成 AI を使うときはコンテキストが重要です。[手順ファイル][instruction-files]を使うと、Copilot に何をするかだけでなく、どのように行うかも伝えられます。

この演習では、次の操作を行います。

- リポジトリのカスタム手順とパス単位の手順ファイルによって、プロジェクト固有のコンテキスト、コーディングガイドライン、ドキュメント標準が Copilot に伝わる方法を確認します。
- `.github/copilot-instructions.md` にリポジトリ全体の標準を追加します。

> [!NOTE]
> VS Code や CLI のハーネスとは異なり、ここでは *before/after* プロンプトを実行しません。クラウドエージェントは GitHub Issue 上で非同期に動作するため、影響をリアルタイムで並べて示すのが難しいためです。

## 手順ファイル

### シナリオ

Tailspin Toys には開発のガイドラインがあります。

- データ層には常に単体テストを追加する。
- UI はダークモードで現代的にする。
- コードに TSDoc ドキュメントコメントを追加する。
- 各ファイルの先頭に、そのファイルの目的を説明するコメントブロックを追加する。

手順ファイルを使って、Copilot がこれらの方針に沿って作業できるようにします。

### カスタム手順

カスタム手順は、コーディングスタイルや要件を Copilot に伝える方法です。リポジトリ全体用の手順と、特定のファイル種別用の手順を作成できます。

推奨する規約、ライブラリ、コードコメントの形式などを指定でき、より適切な提案やコードスニペットを得られます。

2 種類の手順ファイルがあります。

- `.github/copilot-instructions.md` は、リポジトリへの**すべての**リクエストで Copilot に送信されます。技術スタック、プロジェクト概要、ベストプラクティスなどを記述します。
- `.github/instructions/*.instructions.md` は、特定のタスクやファイル種別に適用できます。TypeScript や Astro などの言語、UI コンポーネントや単体テストの作成などに使用します。

> [!NOTE]
> IDE では、手順ファイルは Copilot Chat のコード生成にのみ使われ、コード補完や次の編集候補には使われません。
>
> Copilot Chat、Copilot CLI、Copilot クラウドエージェントは、リポジトリレベルのファイルと `applyTo` フロントマターを持つ `*.instructions.md` ファイルの両方を使います。
>
> Copilot は AGENTS.md や CLAUDE.md など、他の標準の手順ファイルもサポートしています。[手順ファイルのサポート][custom-instructions-support]を参照してください。

### 手順ファイルを管理するためのベストプラクティス

- `copilot-instructions.md` にはプロジェクト全体のガイダンスを記述します。
- `*.instructions.md` にはファイル種別や具体的なタスクの手順を記述します。
- 自然言語で明確に書き、良い例と悪い例を示します。

手順ファイルの作成方法は 1 つではありません。AI の使い方と同様に、実験を通してプロジェクトに合った方法を見つけます。

> [!TIP]
> GitHub Copilot を使うすべてのプロジェクトには、十分な手順ファイルを用意することをお勧めします。このプロジェクトには [UI の更新][ui-instructions]や [Astro][astro-instructions] などのファイルがあります。
>
> Copilot に手順ファイルを生成させることもできます。VS Code では **Configure Chat → Generate Agent Instructions**、Copilot CLI では `/init` など、利用するサーフェスごとに方法が異なります。
>
> テンプレートを探している場合は [awesome-copilot][awesome-copilot] を確認してください。

## このプロジェクトのカスタム手順ファイルを確認する

次のファイルをエディターまたは GitHub Web UI で開きます。

1. `.github/copilot-instructions.md` を開き、プロジェクトの説明、**Agent notes**、**Code standards**、**Scripts**、**Repository Structure** を確認します。**Code standards** 内の **GitHub Actions Workflows** の指示も確認します。
2. `.github/instructions` フォルダーを確認します。Astro、Drizzle、テストなどの指示があります。
3. `.github/instructions/unit-tests.instructions.md` を開き、`applyTo` が `**/*.test.ts` に一致するファイルへ適用されることを確認します。
4. 単体テスト作成に関する指示を確認します。
5. `.github/instructions/drizzle.instructions.md` の末尾で、他の手順ファイルや既存ファイルへのリンクを確認します。

> [!NOTE]
> **Code formatting requirements** にはコードコメントのルールがまだありません。次の手順で追加します。

## 新しいリポジトリ標準を追加する

1. ブランチを作成します。

   ```bash
   git checkout -b custom-instructions-cloud
   ```

2. `.github/copilot-instructions.md` の **Code formatting requirements** の下に次の行を追加します。

   ```markdown
   - Every exported function should have a TSDoc comment describing its purpose, parameters, and return value.
   - Before imports or any code, add a comment block to the file that explains its purpose.
   ```

3. ファイルを保存します。

> [!TIP]
> リポジトリレベルのファイルはプロジェクト全体の標準に適しています。ファイル種別ごとのルールには `*.instructions.md` を使います。

## 手順の更新をコミット、プッシュ、マージする

1. 変更をステージしてコミットします。

   ```bash
   git add .github/copilot-instructions.md
   git commit -m "Add doc comment and file-header standards to copilot instructions"
   ```

2. ブランチをプッシュします。

   ```bash
   git push -u origin custom-instructions-cloud
   ```

3. `custom-instructions-cloud` から `main` へのプルリクエストを作成してマージします。

## まとめと次のステップ

Copilot が手順ファイルからコンテキストを取得する方法を確認し、リポジトリ全体の標準を追加しました。[最初の Issue を Copilot クラウドエージェントに割り当てる][next-lesson]準備ができました。

## リソース

- [GitHub Copilot のカスタマイズ用手順ファイル][instruction-files]
- [カスタム手順作成のベストプラクティス][instructions-best-practices]
- [Awesome Copilot][awesome-copilot]

[previous-lesson]: ../0-prerequisites/
[next-lesson]: ../2-cloud-agent/
[instruction-files]: https://docs.github.com/copilot/customizing-copilot/about-customizing-github-copilot-chat-responses
[instructions-best-practices]: https://docs.github.com/enterprise-cloud@latest/copilot/using-github-copilot/coding-agent/best-practices-for-using-copilot-to-work-on-tasks#adding-custom-instructions-to-your-repository
[awesome-copilot]: https://github.com/github/awesome-copilot
[ui-instructions]: https://github.com/github-samples/tailspin-toys/blob/main/.github/instructions/ui.instructions.md
[astro-instructions]: https://github.com/github-samples/tailspin-toys/blob/main/.github/instructions/astro.instructions.md
[custom-instructions-support]: https://docs.github.com/copilot/reference/custom-instructions-support
