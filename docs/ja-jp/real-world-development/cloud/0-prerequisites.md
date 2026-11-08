---
title: "演習 0：前提条件"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

Copilot クラウドエージェントの演習を始める前に準備を整えます。Tailspin Toys リポジトリのコピーを作成し、手順ファイルの編集とクラウドエージェントの成果物の確認に使う [Codespace][codespaces] を起動します。

## ラボ用リポジトリを設定する

作成するコードのリポジトリのコピーを作るため、[テンプレート][template-repository]からインスタンスを作成します。新しいインスタンスにはラボに必要なファイルがすべて含まれます。

1. 新しいブラウザーウィンドウで [Tailspin Toys テンプレート][tailspin-template] に移動します。
2. ラボリポジトリで **Use this template** を選択し、**Create a new repository** を選択します。

    ![Use this template ボタン](../../../_images/ex0-use-template.png)

3. GitHub または Microsoft のイベントで参加している場合はメンターの指示に従います。それ以外の場合は、GitHub Copilot にアクセスできる組織に新しいリポジトリを作成します。

    ![リポジトリテンプレートの設定を入力](../../../_images/ex0-repository-settings.png)

4. 作成したリポジトリのパス（**organization-or-user-name/repository-name**）を控えてください。

> [!NOTE]
> **バックログの準備**
>
> テンプレートからリポジトリを作成すると、GitHub Issue のバックログが自動的に作成されます。ワークショップではこの Issue を使うため、自分で作成する必要はありません。

## Codespace を作成する

次に、ラボの演習を完了するために Codespace を使います。

 [GitHub Codespaces][codespaces] は、ブラウザーから直接コードの記述、実行、デバッグができるクラウド開発環境です。複数のプログラミング言語、拡張機能、ツールをサポートする IDE が用意されています。

1. 作成したリポジトリに移動します。
2. 緑色の **Code** ボタンを選択します。

    ![Code ボタンを選択](../../../_images/ex0-code-button.png)

3. **Codespaces** タブを選択し、**+** ボタンを選択して Codespace を作成します。

    ![新しい Codespace を作成](../../../_images/ex0-create-codespace.png)

作成には数分かかります。その間に GitHub Copilot の他の機能を確認できます。

> [!CAUTION]
> 今後の演習で Codespace に戻ります。それまではブラウザーのタブを開いたままにしてください。

> [!NOTE]
> このワークショップは Codespace またはローカルの [dev container][dev-containers] で実行できます。ローカルで実行する場合は、VS Code でクローンしたリポジトリを開き、表示されたら **Reopen in Container** を選択してください。

[codespaces]: https://github.com/features/codespaces
[dev-containers]: https://code.visualstudio.com/docs/devcontainers/containers

## GitHub Copilot Chat とエージェントモードを使う

GitHub Copilot Chat の拡張機能は Codespace にあらかじめインストールされています。ない場合は [Visual Studio Code Marketplace][copilot-chat-extension] からインストールします。インストール後、GitHub アカウントでの認証が必要になる場合があります。

1. Codespace に戻ります。
2. エディターの右側に Copilot Chat が表示されていない場合は、上部の **Copilot Chat** アイコンを選択します。
3. Copilot Chat ウィンドウに `Hello world` のようなメッセージを入力して送信します。
4. 認証されていない場合は GitHub アカウントへのサインインを求められます。手順に従って認証します。

    ![Copilot Chat の認証プロンプトの例](../../../_images/ex1-copilot-authentication.png)

5. 認証後、Copilot Chat ウィンドウが表示されます。

## まとめ

ラボリポジトリのコピーを作成し、Codespace の作成を開始しました。

## 次のステップ

[演習 1 - カスタム手順][next-lesson]に進み、クラウドエージェントが従う手順を追加します。

## リソース

- [GitHub Codespaces の概要][codespaces]
- [テンプレートからリポジトリを作成する][template-repository]
- [Codespaces のクイックスタート][codespaces-quickstart]

[tailspin-template]: https://github.com/github-samples/tailspin-toys
[template-repository]: https://docs.github.com/repositories/creating-and-managing-repositories/creating-a-template-repository
[codespaces-quickstart]: https://docs.github.com/codespaces/getting-started/quickstart
[copilot-chat-extension]: https://marketplace.visualstudio.com/items?itemName=GitHub.copilot-chat
[next-lesson]: ../1-custom-instructions/
