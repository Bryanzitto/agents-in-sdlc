---
title: "练习 2 - 使用 Copilot 代理模式添加功能"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

代理模式会探索项目、修改多个文件、运行测试并修复发现的问题。本练习将为游戏列表添加类别和发行商筛选。

代理模式与云端代理不同：代理模式在 IDE 中运行，提供快速反馈和交互；云端代理则像团队成员一样通过议题和拉取请求异步工作。

## 运行网站

Tailspin Toys 是一个棋盘游戏众筹平台，使用单个 Astro 应用在构建时生成静态 HTML。页面通过 Drizzle ORM 直接查询本地 SQLite 数据库，可复用的数据访问辅助函数位于 `src/lib/`，交互使用标准 DOM API。

```bash
git checkout main
git pull
git checkout -b filtering-vscode
npm run dev
```

在浏览器中打开 `http://localhost:4321`，了解主页和游戏详情页。

主页显示游戏列表；选择游戏后，详情页会显示标题、描述、发行商和类别。

## 使用代理模式

在 Chat 视图中选择 **Agent**，打开 `.github/instructions/ui.instructions.md`，查看架构、组件设计、可测试性、无障碍性以及 Astro、Tailwind CSS 和 Drizzle 指令的链接。

选择 **Agent**，查看 `.github/instructions/ui.instructions.md`，然后发送：

```plaintext
Please update the site to include filtering by publisher and category based on the requirements from the related GitHub issue in the backlog. A publishers helper already exists from the previous exercise, so preserve and refine that work as needed while completing the remaining data-layer, UI, and tests. Ensure all tests are passing before completion. The server is already running, so you do not need to start it up.
```

审查生成的代码和测试，选择 **Keep**，再在浏览器中验证功能。

代理可能会探索多个文件、修改数据层和 UI 并运行测试。按提示选择 **Continue** 运行测试，等待它修复发现的问题。始终审查 AI 生成的代码后再选择 **Keep**。

## 总结与后续步骤

你使用 Agent 模式协调了数据层、UI 和测试的更改。接下来，使用 [Playwright MCP 服务器][next-lesson]测试功能。

## 资源

- [Copilot ask、edit 和 agent 模式：功能及适用时机][choose-mode]
- [VS Code 中的 Agent 模式][vs-code-agent-mode]

[previous-lesson]: ../1-custom-instructions/
[next-lesson]: ../3-mcp/
[choose-mode]: https://github.blog/ai-and-ml/github-copilot/copilot-ask-edit-and-agent-modes-what-they-do-and-when-to-use-them/
[vs-code-agent-mode]: https://code.visualstudio.com/docs/copilot/chat/chat-agent-mode
