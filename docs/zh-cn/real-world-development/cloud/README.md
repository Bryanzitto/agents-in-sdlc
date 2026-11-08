---
slug: zh-cn/real-world-development/cloud
title: "GitHub Copilot 云端代理"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

[GitHub Copilot 云端代理](https://docs.github.com/copilot/concepts/agents/cloud-agent/about-cloud-agent) 可在云端异步工作。你可以在 GitHub 上分配任务，云端代理会在后台探索存储库、进行更改并创建拉取请求。

本系列练习将介绍自定义指令、分配议题、使用自定义代理、监控代理会话，以及审查和迭代拉取请求。

## 练习

| 练习 | 主题 | 说明 |
|----------|-------|-------------|
| [0. 先决条件][ex0] | 设置 | 创建存储库和 codespace |
| [1. 自定义指令][ex1] | 上下文 | 添加云端代理要遵循的指令 |
| [2. 云端代理][ex2] | 异步代理 | 将议题分配给 Copilot 云端代理 |
| [3. 自定义代理][ex3] | 专用代理 | 审查并使用自定义代理 |
| [4. 管理代理][ex4] | 监控 | 监控并引导代理会话 |
| [5. 迭代][ex5] | 审查 | 审查 PR、迭代 Copilot 的工作并选择后续步骤 |

## 先决条件

开始前，请确保具备：

- [ ] 拥有有效的 **Copilot Student、Pro、Pro+、Business 或 Enterprise** 计划的 GitHub 帐户
- [ ] 已为帐户或组织启用 Copilot 云端代理

> [!NOTE]
> 云端代理适用于 **Copilot Student、Pro、Pro+、Business 和 Enterprise**，不包括 Copilot Free。Business 或 Enterprise 组织还需要管理员启用该功能。

> [!TIP]
> 没有付费计划？通过 [GitHub Education][callout-student-plan-education] 验证学生身份后，可以免费获得 GitHub Copilot。**Copilot Student** 计划包含本工作坊使用的代理、MCP、代码审查和 Copilot CLI 功能，因此可以完成全部学习路径。

[callout-student-plan-education]: https://github.com/education/students

> [!NOTE]
> 本学习路径不介绍 MCP。要了解如何将 MCP 服务器与 Copilot 配合使用，请参阅 [CLI 学习路径](../cli/)或 [VS Code 学习路径](../vscode/)。

## 开始

**[从练习 0：先决条件开始 →][ex0]**

[ex0]: 0-prerequisites/
[ex1]: 1-custom-instructions/
[ex2]: 2-cloud-agent/
[ex3]: 3-custom-agents/
[ex4]: 4-managing-agents/
[ex5]: 5-iterating/
