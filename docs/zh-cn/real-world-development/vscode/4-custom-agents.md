---
title: "练习 4 - 自定义代理"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

[自定义代理][custom-agents-concept]是针对特定任务或领域的专用 AI 助手。它们由 `.github/agents` 中的 Markdown 文件定义。

自定义代理也可以全局定义在 `~/.copilot/agents` 中。每个代理文件至少需要包含 `name` 和 `description` YAML frontmatter，后面是定义行为、专业知识和指令的 Markdown 提示。代理是执行工作的角色，技能是它使用的工具。

## 场景

设计团队希望为 Tailspin Toys 添加可切换的高对比度模式。你将使用可访问性代理完成此工作。

1. 创建并切换分支：

   ```bash
   git checkout main
   git pull
   git checkout -b accessibility-vscode
   ```

2. 打开 `.github/agents/accessibility.md`，查看 `name` 和 `description` frontmatter 以及可访问性指导。
3. 在 Copilot Chat 的代理选择器中选择 **Accessibility agent**。
4. 发送：

   ```plaintext
   Add a high-contrast mode to the site. There should be a toggle for high contrast which the user can set, and the setting should persist across page reloads using local storage on the browser.
   ```

审查代理提出的每项编辑；你将在下一课中继续引导会话。

代理会探索代码库并以内联差异的形式提出编辑。审查每项编辑；**Files changed** 指示器会显示当前会话修改的文件。

## 总结与后续步骤

你了解了自定义代理，并在 Copilot Chat 的 Agent 模式中使用可访问性代理。接下来，继续[监控并引导代理工作][next-lesson]。

## 资源

- [关于自定义代理][custom-agents-concept]
- [在 IDE 中创建自定义代理](https://docs.github.com/copilot/how-tos/use-copilot-agents/cloud-agent/create-custom-agents-in-your-ide)
- [VS Code 中的自定义代理](https://code.visualstudio.com/docs/copilot/customization/custom-agents)

[custom-agents-concept]: https://docs.github.com/copilot/concepts/agents/cloud-agent/about-custom-agents
[previous-lesson]: ../3-mcp/
[next-lesson]: ../5-managing-agents/
