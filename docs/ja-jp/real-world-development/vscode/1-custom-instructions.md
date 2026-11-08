---
title: "演習 1 - カスタム手順（VS Code）"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

[← 前のレッスン：前提条件][previous-lesson] · [次のレッスン：エージェントモード →][next-lesson]

コンテキストは生成 AI の作業に重要です。[手順ファイル][instruction-files]を使って、コード生成の方針を Copilot に伝えます。

この演習では、現在の手順で出版社ヘルパーを生成し、リポジトリ標準を追加して同じプロンプトを再実行し、変更を `main` にコミットします。

## 手順ファイル

Tailspin Toys の規約には、単体テスト、ダークモード、TSDoc コメント、ファイルヘッダーが含まれます。`.github/copilot-instructions.md` は全リクエストに適用され、`.github/instructions/*.instructions.md` はファイル種別やタスクに適用されます。

## カスタム手順を確認する

`.github/copilot-instructions.md` と `.github/instructions` を開き、`applyTo`、TypeScript、Astro、Drizzle、テスト用の指示を確認します。

## ブランチを作成する

```bash
git checkout -b custom-instructions
```

## Copilot Chat を使う

Copilot Chat で **Agent** を選択し、次のプロンプトを送信します。

```plaintext
Create or update src/lib/publishers.ts with a data-access helper that returns a list of all publishers with the name and id for each. Apply the file changes.
```

生成されたヘルパーを確認した後、`.github/copilot-instructions.md` に次を追加します。

まず `.github/instructions/drizzle.instructions.md` のデータ層規約により、`db` クライアントを最初の引数に取り、型付き出版社配列を返すことを確認します。最初の生成では通常、TSDoc とファイルヘッダーがありません。

```markdown
- Every exported function should have a TSDoc comment describing its purpose, parameters, and return value.
- Before imports or any code, add a comment block to the file that explains its purpose.
```

同じプロンプトを再実行し、ファイルヘッダーと TSDoc コメントが追加されることを確認します。

2 回目には、ファイルの目的を説明するコメントブロックと、関数の目的、`db` パラメーター、戻り値を説明する TSDoc コメントが追加されます。

## コミットしてプッシュする

```bash
git add .github/copilot-instructions.md src/lib/publishers.ts
git commit -m "Add doc comment standards and publishers helper foundation"
git push -u origin custom-instructions
```

その後、`main` への PR を作成してマージします。

PR の説明には手順更新と出版社ヘルパーの基盤を含め、必要な GitHub 操作の確認を求められたら内容を確認して **Allow** を選択します。マージ後、`main` に戻って最新コードを pull します。

## まとめと次のステップ

既存の手順を確認し、新しい標準を追加して、生成コードの変化を確認しました。次に [Agent Mode][next-lesson]を使います。

## リソース

- [GitHub Copilot のカスタマイズ用手順ファイル][instruction-files]
- [カスタム手順作成のベストプラクティス][instructions-best-practices]
- [個人用のカスタム手順][personal-instructions]
- [Awesome Copilot][awesome-copilot]

[previous-lesson]: ../0-prerequisites/
[next-lesson]: ../2-agent-mode/
[instruction-files]: https://code.visualstudio.com/docs/copilot/copilot-customization
[instructions-best-practices]: https://docs.github.com/enterprise-cloud@latest/copilot/using-github-copilot/coding-agent/best-practices-for-using-copilot-to-work-on-tasks#adding-custom-instructions-to-your-repository
[personal-instructions]: https://docs.github.com/copilot/customizing-copilot/adding-personal-custom-instructions-for-github-copilot
[copilot-instructions-five-tips]: https://github.blog/ai-and-ml/github-copilot/5-tips-for-writing-better-custom-instructions-for-copilot/
[awesome-copilot]: https://github.com/github/awesome-copilot
