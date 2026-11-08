---
title: "演習 0：前提条件"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

VS Code の演習を始める前に、Tailspin Toys リポジトリのコピーと Codespace を作成し、エディターで GitHub Copilot Chat が動作することを確認します。

## ラボ用リポジトリを設定する

1. [Tailspin Toys テンプレート][tailspin-template]を開きます。
2. **Use this template**、**Create a new repository** の順に選択します。
3. 作成したリポジトリのパスを控えます。

![Use this template ボタン](../../../_images/ex0-use-template.png)

![リポジトリテンプレートの設定を入力](../../../_images/ex0-repository-settings.png)

## Codespace を作成する

1. リポジトリで **Code**、**Codespaces**、**+** の順に選択します。
2. Codespace の作成が完了するまで待ちます。

![Code ボタンを選択](../../../_images/ex0-code-button.png)

![新しい Codespace を作成](../../../_images/ex0-create-codespace.png)

GitHub または Microsoft のイベントで参加している場合はメンターの指示に従います。それ以外の場合は、GitHub Copilot にアクセスできる組織にリポジトリを作成します。Codespace の作成には数分かかりますが、サービスを手動でインストールするより短時間です。

> [!NOTE]
> Codespace またはローカルの [dev container][dev-containers]で実行できます。
> どちらも必要な前提条件を備えています。ローカルで実行する場合は、VS Code でクローンしたリポジトリを開き、表示されたら **Reopen in Container** を選択します。

## GitHub Copilot Chat とエージェントモードを使う

Copilot Chat 拡張機能がない場合は [Visual Studio Code Marketplace][copilot-chat-extension]からインストールし、GitHub アカウントで認証します。

1. Codespace に戻ります。
2. **Copilot Chat** アイコンを選択します。
3. `Hello world` と入力して送信します。

![Copilot Chat の認証プロンプトの例](../../../_images/ex1-copilot-authentication.png)

## まとめ

リポジトリのコピーと Codespace を作成し、Copilot Chat を有効にしました。

## 次のステップ

[演習 1 - カスタム手順][next-lesson]に進みます。

## リソース

- [GitHub Codespaces の概要][codespaces]
- [テンプレートからリポジトリを作成する][template-repository]
- [Codespaces のクイックスタート][codespaces-quickstart]

[tailspin-template]: https://github.com/github-samples/tailspin-toys
[dev-containers]: https://code.visualstudio.com/docs/devcontainers/containers
[copilot-chat-extension]: https://marketplace.visualstudio.com/items?itemName=GitHub.copilot-chat
[codespaces]: https://github.com/features/codespaces
[template-repository]: https://docs.github.com/repositories/creating-and-managing-repositories/creating-a-template-repository
[codespaces-quickstart]: https://docs.github.com/codespaces/getting-started/quickstart
[next-lesson]: ../1-custom-instructions/
