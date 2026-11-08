---
title: "练习 1 - 自定义指令（VS Code）"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

[← 上一课：先决条件][previous-lesson] · [下一课：代理模式 →][next-lesson]

本练习将探索存储库指令、生成 publishers 数据访问辅助函数、添加文档标准，并将更改提交到 `main`。

上下文对于生成式 AI 至关重要。指令文件可以告诉 Copilot 要做什么以及如何完成。你将先使用现有指令生成辅助函数，再添加存储库级标准并使用相同提示重新生成。

## 指令文件

Tailspin Toys 的规范包括单元测试、现代深色 UI、TSDoc 注释和文件头注释。`.github/copilot-instructions.md` 用于所有请求；`.github/instructions/*.instructions.md` 可限制到特定文件类型。

两类指令文件分别是 `.github/copilot-instructions.md`（存储库的每个请求）和 `.github/instructions/*.instructions.md`（特定语言、文件类型或任务）。在 IDE 中，指令文件用于 Copilot Chat 代码生成，不用于代码补全或下一步编辑建议。

1. 查看 `.github/copilot-instructions.md`、`.github/instructions/unit-tests.instructions.md` 和 `.github/instructions/drizzle.instructions.md`。
2. 创建分支：

   ```bash
   git checkout -b custom-instructions
   ```

3. 在 Agent 模式中请求生成 `src/lib/publishers.ts` 的数据访问辅助函数。
4. 在 **Code formatting requirements** 下添加 TSDoc 和文件头标准。
5. 使用相同提示再次生成，并审查结果。
6. 暂存、提交并推送更改，然后创建和合并 PR。

```markdown
- Every exported function should have a TSDoc comment describing its purpose, parameters, and return value.
- Before imports or any code, add a comment block to the file that explains its purpose.
```

在重新生成前，关闭旧编辑器标签，打开 `src/lib/publishers.ts`，选择 **Agent**，并发送：

```plaintext
Create or update src/lib/publishers.ts with a data-access helper that returns a list of all publishers with the name and id for each. Apply the file changes.
```

第一次生成的辅助函数通常不会包含 TSDoc 或文件头。将上述两行标准添加到 `.github/copilot-instructions.md` 后，在新聊天中发送相同提示，检查生成的文件是否包含文件头和函数 TSDoc。

## 总结与后续步骤

你观察了指令更新如何影响生成的代码。接下来，在[代理模式][next-lesson]中实现筛选功能。

[previous-lesson]: ../0-prerequisites/
[next-lesson]: ../2-agent-mode/
[instruction-files]: https://code.visualstudio.com/docs/copilot/copilot-customization
