---
title: "练习 3 - 使用 Playwright MCP 服务器测试功能"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

[← 上一课：代理模式][previous-lesson] · [下一课：自定义代理 →][next-lesson]

使用代理模式构建筛选功能后，将连接 **Playwright MCP 服务器**，让 Copilot 在真实浏览器中验证它。

本练习还会发布 `filtering-vscode` 分支，并打开关联的拉取请求。

## 什么是 MCP？

[Model Context Protocol (MCP)](https://github.blog/ai-and-ml/llms/what-the-heck-is-mcp-and-why-is-everyone-talking-about-it/) 让 AI 代理与外部工具和服务通信。使用 MCP 服务器前，请审查其代码、发布者和安全影响。

MCP 服务器充当代理与外部工具之间的桥梁。GitHub MCP Server 可管理存储库、议题和 PR；Playwright MCP Server 可控制浏览器。GitHub 还维护 [MCP 注册表](https://github.com/mcp)。

## 添加 Playwright MCP 服务器

在 `.vscode/mcp.json` 中加入：

```json
{
  "servers": {
    "github": {
      "type": "http",
      "url": "https://api.githubcopilot.com/mcp/"
    },
    "playwright": {
      "command": "npx",
      "args": ["@playwright/mcp@latest", "--headless"]
    }
  }
}
```

选择 **Start** 启动服务器并确认信任。然后让 Copilot 使用 Playwright 打开 `http://localhost:4321`，依次测试类别、发行商以及组合筛选。

可以使用以下提示：

```text
Using the Playwright MCP server, open a browser to the running app at http://localhost:4321 and verify the new game filtering feature:

1. Go to the games page and note how many games are listed.
2. Apply a category filter and confirm the list updates to only show games in that category.
3. Clear it, then apply a publisher filter and confirm the list updates to that publisher.
4. Combine a category and a publisher filter and confirm the results respect both.

Report what you observe at each step, and call out anything that does not behave as expected.
```

## 创建拉取请求

在 **Source Control** 中审查、暂存并发布 `filtering-vscode` 分支。随后在 Copilot Chat 中请求查找筛选议题并为当前分支创建 PR。

创建 PR 后先审查，不要立即合并。Playwright MCP 服务器需要应用在 `http://localhost:4321` 运行；如缺少浏览器，请运行 `npx playwright install chromium`。

## 总结与后续步骤

你了解了 MCP，添加了 Playwright MCP 服务器，在浏览器中测试了筛选功能，并发布分支和创建 PR。接下来，继续[创建自定义代理][next-lesson]。

## 资源

- [什么是 MCP][mcp-blog-post]
- [Microsoft Playwright MCP 服务器][playwright-mcp-server]
- [GitHub MCP 服务器][github-mcp-server]
- [GitHub MCP 注册表][mcp-registry]
- [VS Code 中的 MCP 服务器][vscode-mcp-config]

[playwright-mcp-server]: https://github.com/microsoft/playwright-mcp
[mcp-blog-post]: https://github.blog/ai-and-ml/llms/what-the-heck-is-mcp-and-why-is-everyone-talking-about-it/
[github-mcp-server]: https://github.com/github/github-mcp-server
[mcp-registry]: https://github.com/mcp
[remote-github-mcp-server]: https://github.blog/changelog/2025-06-12-remote-github-mcp-server-is-now-available-in-public-preview/
[vscode-mcp-config]: https://code.visualstudio.com/docs/agents/reference/mcp-configuration
[previous-lesson]: ../2-agent-mode/
[next-lesson]: ../4-custom-agents/
