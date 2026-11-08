---
title: "练习 0：先决条件"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

开始 VS Code 练习前，创建 Tailspin Toys 存储库副本，启动 [codespace][codespaces]，并确认编辑器中的 GitHub Copilot Chat 可用。

## 设置存储库和 codespace

要创建用于本实验的代码副本，请从[模板存储库][template-repository]创建实例。新实例包含实验所需的全部文件。

1. 打开 [Tailspin Toys 模板][tailspin-template]。
2. 选择 **Use this template**，再选择 **Create a new repository**。
   
   ![Use this template 按钮](../../../_images/ex0-use-template.png)

3. 打开新存储库，选择 **Code**、**Codespaces** 和 **+**。

   ![创建新的 codespace](../../../_images/ex0-create-codespace.png)

如果是在 GitHub 或 Microsoft 主办的活动中参加工作坊，请按照导师的说明操作；否则，请在可以使用 GitHub Copilot 的组织中创建存储库，并记下存储库路径。

## 使用 Copilot Chat

GitHub Codespaces 是基于云的开发环境，可在浏览器中编写、运行和调试代码。创建 codespace 可能需要几分钟。

如果未安装 GitHub Copilot Chat，请从 [Visual Studio Code Marketplace][copilot-chat-extension] 安装。返回 codespace，打开 **Copilot Chat**，输入 `Hello world` 并按 Enter；如有提示，请登录 GitHub。

选择编辑器右上方的 **Copilot Chat** 图标即可打开聊天窗口。完成身份验证后，Copilot Chat 应显示在编辑器中。

> [!NOTE]
> 本工作坊也支持本地 [dev container][dev-containers]。

## 下一步

继续[练习 1：自定义指令][next-lesson]。

## 总结

你已创建实验存储库副本和 codespace，并确认编辑器中的 Copilot Chat 可用。

## 资源

- [GitHub Codespaces 概述][codespaces]
- [从模板创建存储库][template-repository]
- [Codespaces 快速入门][codespaces-quickstart]

[codespaces]: https://github.com/features/codespaces
[dev-containers]: https://code.visualstudio.com/docs/devcontainers/containers
[tailspin-template]: https://github.com/github-samples/tailspin-toys
[template-repository]: https://docs.github.com/repositories/creating-and-managing-repositories/creating-a-template-repository
[copilot-chat-extension]: https://marketplace.visualstudio.com/items?itemName=GitHub.copilot-chat
[codespaces-quickstart]: https://docs.github.com/codespaces/getting-started/quickstart
[next-lesson]: ../1-custom-instructions/
