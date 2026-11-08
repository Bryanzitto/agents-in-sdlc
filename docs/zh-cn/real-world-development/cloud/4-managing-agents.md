---
title: "练习 4 - 监控和管理代理"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

云端代理异步运行，但监控任务仍然很重要。GitHub 的[代理页面][agents-page]提供了查看任务、操作和活动会话的控制中心。

前几个练习中，你已让云端代理处理文档、游戏 API 和高对比度模式等任务。本练习将查看这些任务，并在高对比度任务进行期间添加浅色模式。

## 查看任务

1. 打开 [Copilot 代理页面](https://github.com/copilot/agents)。
2. 查看文档更新、游戏 API 和高对比度模式等任务。
3. 选择正在运行的任务，查看检出代码、创建环境和运行 MCP 等步骤。

具体步骤会因代理当前的工作状态和采用的方法而异。右侧的 PR 面板还可以查看 PR 和更改的文件。

## 引导云端代理

选择添加高对比度模式的会话，等待它开始工作，然后发送：

```plaintext
While we are working on a high contrast mode, let's also add a light mode. There should be a switch for this mode as well where users can select their desired display mode.
```

按 <kbd>Enter</kbd> 发送，并观察代理如何将新请求加入工作流。

代理会在完成发送消息时正在执行的步骤后，将新请求加入工作流。等待期间，可以继续其他工作并在会话中查看进度。

## 总结与后续步骤

你使用代理页面监控并引导了云端代理任务。接下来，继续[迭代 Copilot 的工作][next-lesson]。

[previous-lesson]: ../3-custom-agents/
[next-lesson]: ../5-iterating/
[agents-page]: https://github.blog/changelog/2025-07-03-agents-page-for-copilot-coding-agent-in-public-preview
