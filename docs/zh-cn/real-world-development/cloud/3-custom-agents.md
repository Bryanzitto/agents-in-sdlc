---
title: "练习 3 - 自定义代理"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

## 什么是自定义代理？

[GitHub Copilot 中的自定义代理][custom-agents]是针对特定任务或领域的专用 AI 助手。代理通过 `.github/agents` 中的 Markdown 文件定义，并可包含行为、专业知识和指令。

自定义代理是执行工作的角色，而技能是它可以使用的工具。代理可以编排技能和其他代理来完成任务。

自定义代理通常定义在项目的 `.github/agents` 文件夹中，也可以全局定义在 `~/.copilot/agents` 中。每个文件至少需要包含 `name` 和 `description` YAML frontmatter，后面是定义行为、专业知识和指令的 Markdown 提示。

自定义代理与[代理技能][agent-skills]有部分重叠：两者主要都使用 Markdown 文件告诉 AI 如何执行操作。最简单的区分方式是：**自定义代理**是执行工作的角色，**技能**是它使用的工具。

代理拥有自己的上下文窗口，并可编排技能甚至其他代理。没有唯一正确的代理编写方式，应在目标环境和场景中反复测试和迭代。

[agent-skills]: https://docs.github.com/copilot/concepts/agents/about-agent-skills
[wcag]: https://www.w3.org/WAI/standards-guidelines/wcag/

## 场景

Tailspin Toys 希望提高网站的可访问性。设计团队要求添加可切换的高对比度模式，因此你将使用可访问性自定义代理生成此功能。

## 审查并使用代理

1. 打开 `.github/agents/accessibility.md`。
2. 查看包含 `name` 和 `description` 的 YAML frontmatter。
3. 审查其中的可访问性职责、最佳实践、代码示例和常见错误。
4. 创建议题 `Add high contrast mode to website`，并将其分配给 **Accessibility agent**。

在议题描述中说明：需要可切换的高对比度模式，并将设置保存在浏览器的 local storage 中。创建议题后，在右侧选择 **Assign to Copilot**，再选择 **Accessibility agent** 和 **Assign**。

> [!CAUTION]
> 自定义代理必须包含 `name` 和 `description` frontmatter。

## 总结与后续步骤

你了解了自定义代理的定义和使用方式。接下来，继续[监控并管理代理][next-lesson]。

## 资源

- [关于自定义代理][custom-agents]
- [为组织准备自定义代理](https://docs.github.com/copilot/how-tos/administer-copilot/manage-for-organization/prepare-for-custom-agents)
- [为企业准备自定义代理](https://docs.github.com/copilot/how-tos/administer-copilot/manage-for-enterprise/manage-agents/prepare-for-custom-agents)

[custom-agents]: https://docs.github.com/copilot/concepts/agents/cloud-agent/about-custom-agents
[previous-lesson]: ../2-cloud-agent/
[next-lesson]: ../4-managing-agents/
