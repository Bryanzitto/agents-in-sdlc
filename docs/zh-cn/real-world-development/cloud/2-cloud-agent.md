---
title: "练习 2 - GitHub Copilot 云端代理"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

Copilot 云端代理可以像开发人员一样在后台处理任务。你可以将 GitHub 议题分配给它，它会创建草稿 PR、设置环境并执行任务。

## 了解 GitHub Copilot 云端代理

技术债务可能包括未解决的安全问题、需要更新的旧代码，或长期留在积压列表中的功能请求。云端代理可以在后台更新代码和添加功能，完成后生成供人工审查的草稿 PR。

本练习将介绍如何：

- 自定义生成代码的环境；
- 确保操作安全；
- 编写范围明确的议题；
- 将议题分配给 Copilot。

## 场景

Tailspin Toys 需要为导出的函数添加 TSDoc 注释，并在游戏详情页显示同类别的相关游戏。这些工作适合异步交给云端代理。

## 设置代理环境

在分配任务前，先查看 `.github/copilot-instructions.md` 的 **Code standards**（尤其是 TypeScript 和 TSDoc 要求）以及 `.github/instructions/unit-tests.instructions.md` 的 `applyTo` frontmatter。这些指令会影响云端代理生成的代码。

云端代理使用 [GitHub Actions][github-actions]。`.github/workflows/copilot-setup-steps.yml` 可安装 Node.js、项目依赖、Playwright 浏览器并设置数据库：

```yaml
name: "Copilot Setup Steps"
on: workflow_dispatch
```

工作流包含名为 `copilot-setup-steps` 的作业，并可从 **Actions** 选项卡手动运行。它会在代理开始处理 PR 前运行。

## 分配议题

1. 打开存储库的 **Issues** 选项卡。
2. 创建议题 `Code lacks documentation`，描述需要添加有助于说明行为的 TSDoc 注释。
3. 选择 **Assign to Copilot**，再选择 **Assign**。
4. 在 **Pull Requests** 中打开生成的 PR，并通过 **View session** 查看会话。

   ![将 Copilot 分配给议题](../../../_images/shared-assign-copilot.png)

> [!NOTE]
> Copilot 创建环境、分析项目并制定计划时，PR 中的待办列表可能需要几分钟才会出现。

查看待办列表和实时会话，观察代理如何探索代码、思考并创建代码。等待期间，可以继续其他开发工作。

## 添加相关游戏区域

再次创建议题 `Show related games on the game details page`，描述以下要求：

- 在 `src/lib/` 中添加数据访问辅助函数，返回给定游戏所属类别中的其他游戏，但排除该游戏；
- 在游戏详情页使用该辅助函数显示 **Related games** 区域；
- 处理没有相关游戏的情况；
- 为新辅助函数创建单元测试；
- 创建 PR 前确保所有测试通过。

创建议题后，选择 **Assign to Copilot** 和 **Assign**。议题中的 👀 表示 Copilot 已开始处理。云端代理会异步完成任务，你可以在稍后审查生成的 PR。

随后创建 `Show related games on the game details page` 议题，要求添加数据访问辅助函数、相关游戏区域、空结果处理和单元测试，再将其分配给 Copilot。

## 总结与后续步骤

你学习了如何自定义环境、编写范围明确的议题并将任务异步分配给云端代理。接下来，继续学习[自定义代理][next-lesson]。

[previous-lesson]: ../1-custom-instructions/
[next-lesson]: ../3-custom-agents/
[cloud-agent-mcp]: https://docs.github.com/copilot/how-tos/copilot-on-github/customize-copilot/customize-cloud-agent/extend-cloud-agent-with-mcp
[assign-issue]: https://docs.github.com/copilot/how-tos/use-copilot-agents/cloud-agent/start-copilot-sessions
[setup-workflow]: https://docs.github.com/copilot/how-tos/copilot-on-github/customize-copilot/customize-cloud-agent/customize-the-agent-environment
[copilot-agents]: https://docs.github.com/copilot/concepts/agents/cloud-agent/about-cloud-agent
[cloud-agent-best-practices]: https://docs.github.com/copilot/how-tos/copilot-on-github/customize-copilot/customize-cloud-agent/customize-the-agent-environment
[github-actions]: https://docs.github.com/actions
