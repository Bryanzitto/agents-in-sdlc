---
title: "练习 0：先决条件"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

开始云端代理练习前，需要准备好环境。你将创建 Tailspin Toys 存储库的副本，并启动用于编辑指令文件和审查代理工作的 [codespace][codespaces]。

## 设置实验存储库

要创建用于本实验的代码副本，请从[模板存储库][template-repository]创建实例。新实例包含实验所需的全部文件，后续练习都将在其中进行。

1. 在新浏览器窗口中打开 [Tailspin Toys 模板][tailspin-template]。
2. 选择 **Use this template**，再选择 **Create a new repository**。
   
   ![Use this template 按钮](../../../_images/ex0-use-template.png)

3. 如果是在 GitHub 或 Microsoft 主办的活动中参加工作坊，请按照导师的说明操作。否则，请在可以使用 GitHub Copilot 的组织中创建存储库。

   ![输入存储库模板设置](../../../_images/ex0-repository-settings.png)

4. 记下创建的存储库路径（**organization-or-user-name/repository-name**）。

## 创建 codespace

[GitHub Codespaces][codespaces] 是基于云的开发环境，可在浏览器中编写、运行和调试代码。

1. 打开新建的存储库。
2. 选择绿色的 **Code** 按钮。

   ![选择 Code 按钮](../../../_images/ex0-code-button.png)

3. 选择 **Codespaces** 选项卡，再选择 **+** 创建 codespace。

   ![创建新的 codespace](../../../_images/ex0-create-codespace.png)

创建 codespace 需要几分钟，但仍比手动安装所有服务快得多。等待期间，可以了解 GitHub Copilot 的其他功能。

> [!CAUTION]
> 你将在后续练习中返回此 codespace。暂时请将其保持在浏览器选项卡中打开。

> [!NOTE]
> 本工作坊支持在 codespace 或本地 [dev container][dev-containers] 中运行。两者都会安装顺利完成实验所需的先决条件。如果想在本地运行，请在 VS Code 中打开克隆的存储库，并在提示时选择 **Reopen in Container**；VS Code 会构建 codespace 使用的同一个 dev container。

[codespaces]: https://github.com/features/codespaces
[dev-containers]: https://code.visualstudio.com/docs/devcontainers/containers
[template-repository]: https://docs.github.com/repositories/creating-and-managing-repositories/creating-a-template-repository
[codespaces-quickstart]: https://docs.github.com/codespaces/getting-started/quickstart
[tailspin-template]: https://github.com/github-samples/tailspin-toys
[next-lesson]: ../1-custom-instructions/

## 总结

恭喜你已创建实验存储库的副本，并开始创建后续练习中要使用的 codespace。

## 下一步

接下来，为云端代理添加自定义指令。继续学习[练习 1：自定义指令][next-lesson]。

## 资源

- [GitHub Codespaces 概述][codespaces]
- [从模板创建存储库][template-repository]
- [Codespaces 快速入门][codespaces-quickstart]
