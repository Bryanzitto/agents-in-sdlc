---
title: "练习 5：迭代 GitHub Copilot 的工作"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

## 审查工作

在整个学习路径中，你让 Copilot 添加文档、实现相关游戏功能，并使用自定义代理实现高对比度和浅色模式。生成式 AI 不会改变软件设计和 DevOps 的基本原则。审查 Copilot 生成的代码，并在合并前按正常流程运行检查。

## 安全与云端代理

- Copilot 对存储库只有读取权限，对工作分支才有写入权限。
- 云端代理在 GitHub Actions 创建的临时环境中运行。
- GitHub Actions 工作流运行前需要人工批准。
- 默认限制外部资源（包括 MCP 服务器）的访问。

## 审查并请求更改

1. 打开 Copilot 创建的拉取请求并选择 **Files changed**。
2. 检查 TSDoc、TypeScript 约定、注释头、测试和实现。
3. 返回 **Conversation**，必要时选择 **Approve and run workflows**。
4. 在评论中提及 **@copilot**，请求添加注释、README 或其他改进；选择 **View Session** 查看后续工作。

你还可以在代码的行内评论中提及 Copilot。审查新提交后，继续迭代直到满意，然后将草稿 PR 标记为准备好审查并合并。

## 可选练习：继续委派

可以再创建几个议题并分配给 Copilot，例如：

- 在游戏详情页创建支持者兴趣表单；
- 在游戏列表页实现分页；
- 为数据访问辅助函数添加输入验证和错误处理。

## 总结

你完成了云端代理学习路径：添加自定义指令、分配议题、使用自定义代理、监控会话，并审查和迭代拉取请求。

[previous-lesson]: ../4-managing-agents/
