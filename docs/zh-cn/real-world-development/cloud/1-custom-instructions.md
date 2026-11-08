---
title: "练习 1 - 自定义指令（云端代理）"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

[← 上一课：先决条件][previous-lesson] · [下一课：Copilot 云端代理 →][next-lesson]

使用生成式 AI 时，上下文至关重要。[指令文件][instruction-files]可以告诉 Copilot 不仅要做什么，还要如何完成。

本练习将介绍如何：

- 通过存储库自定义指令和路径范围指令文件提供项目上下文；
- 向 `.github/copilot-instructions.md` 添加存储库范围的标准。

> [!NOTE]
> 与 VS Code 和 CLI 环境不同，这里不会运行“前后对比”提示。云端代理会异步处理 GitHub 议题，因此稍后在审查它生成的拉取请求时才能看到指令文件的影响。

## 指令文件

### 场景

Tailspin Toys 的开发规范包括：数据层始终需要单元测试；UI 应采用现代深色设计；代码应包含 TSDoc 注释；每个文件开头应有说明用途的注释块。

自定义指令可提供编码风格、库和注释偏好。`.github/copilot-instructions.md` 会用于存储库的每个请求；`.github/instructions/*.instructions.md` 可针对特定文件类型或任务提供指导。

有两类指令文件：

- `.github/copilot-instructions.md` 会随存储库的**每个**请求发送给 Copilot，应包含适用于大多数请求的项目背景、技术栈和全局规范。
- `.github/instructions/*.instructions.md` 可针对特定语言、文件类型或任务提供指导，例如 TypeScript、Astro 组件或单元测试。

> [!NOTE]
> 在 IDE 中，指令文件仅用于 Copilot Chat 的代码生成，不用于代码补全或下一步编辑建议。
>
> Copilot Chat、Copilot CLI 和云端代理在生成代码时都会使用存储库级指令文件以及带有 `applyTo` frontmatter 的 `*.instructions.md` 文件。
>
> Copilot 还支持使用其他标准的指令文件，例如 AGENTS.md 和 CLAUDE.md。

### 管理指令文件的最佳实践

- 让 `copilot-instructions.md` 专注于项目背景、结构和全局编码标准。
- 使用 `*.instructions.md` 为文件类型（单元测试、Astro 组件、数据层）或具体任务提供指令。
- 使用自然语言，保持指导清晰，并提供代码应有和不应有的示例。

没有唯一正确的指令文件组织方式。通过试验找出最适合项目的方法。

> [!TIP]
> 每个使用 GitHub Copilot 的项目都应有一组完善的指令文件。可以查看本项目中的 [UI 更新指令][ui-instructions]和 [Astro 指令][astro-instructions]。
>
> Copilot 也可以帮助生成指令文件。在 VS Code 中可选择 **Configure Chat → Generate Agent Instructions**，在 Copilot CLI 中可使用 `/init`。如需模板，可浏览包含指令文件、自定义代理和其他资源的 [awesome-copilot][awesome-copilot]。

[ui-instructions]: https://github.com/github-samples/tailspin-toys/blob/main/.github/instructions/ui.instructions.md
[astro-instructions]: https://github.com/github-samples/tailspin-toys/blob/main/.github/instructions/astro.instructions.md
[awesome-copilot]: https://github.com/github/awesome-copilot
[custom-instructions-support]: https://docs.github.com/copilot/reference/custom-instructions-support

## 探索项目中的自定义指令文件

打开项目提供的 `copilot-instructions.md` 和各类 `*.instructions.md` 文件，了解其内容。

1. 打开 `.github/copilot-instructions.md`，查看项目简介以及 **Agent notes**、**Code standards**、**Scripts** 和 **Repository Structure** 等部分。
2. 在 **Code standards** 下查看嵌套的 **GitHub Actions Workflows** 指导。
3. 打开 `.github/instructions` 文件夹，查看 Astro、Drizzle、测试等指令。
4. 打开 `.github/instructions/unit-tests.instructions.md`，查看顶部的 `applyTo` 字段；例如 `**/*.test.ts` 匹配的 TypeScript 测试文件都会应用这些指令。
5. 查看该文件中针对本项目单元测试的具体要求。
6. 打开 `.github/instructions/drizzle.instructions.md` 并滚动到底部，查看它对其他指令文件和项目现有文件的链接。这样可以将较大的指令拆成可复用的小文件，并提供生成代码时可参考的示例。

> [!NOTE]
> `copilot-instructions.md` 中的 **Code formatting requirements** 记录了项目编码标准，但尚未要求代码内文档。下一步将添加 TSDoc 注释和文件注释头规则。

## 添加存储库标准

1. 创建并切换到分支：

   ```bash
   git checkout -b custom-instructions-cloud
   ```

2. 打开 `.github/copilot-instructions.md`，在 **Code formatting requirements** 下添加：

   ```markdown
   - Every exported function should have a TSDoc comment describing its purpose, parameters, and return value.
   - Before imports or any code, add a comment block to the file that explains its purpose.
   ```

3. 暂存并提交更改，然后推送分支并创建指向 `main` 的拉取请求。

提交并合并更新：

```bash
git add .github/copilot-instructions.md
git commit -m "Add doc comment and file-header standards to copilot instructions"
git push -u origin custom-instructions-cloud
```

在 github.com 上创建从 `custom-instructions-cloud` 指向 `main` 的拉取请求并合并。云端代理会从议题目标分支读取指令，因此必须将更改合并到 `main`。

> [!TIP]
> 存储库级文件适合项目范围的标准，`*.instructions.md` 文件适合语言、文件类型或任务范围的规则。

## 总结与后续步骤

你探索了指令文件，并添加了存储库范围的文档标准。接下来，将[第一个议题分配给 Copilot 云端代理][next-lesson]。

[previous-lesson]: ../0-prerequisites/
[next-lesson]: ../2-cloud-agent/
[instruction-files]: https://docs.github.com/copilot/customizing-copilot/about-customizing-github-copilot-chat-responses
[instructions-best-practices]: https://docs.github.com/enterprise-cloud@latest/copilot/using-github-copilot/coding-agent/best-practices-for-using-copilot-to-work-on-tasks#adding-custom-instructions-to-your-repository
[copilot-instructions-five-tips]: https://github.blog/ai-and-ml/github-copilot/5-tips-for-writing-better-custom-instructions-for-copilot/
