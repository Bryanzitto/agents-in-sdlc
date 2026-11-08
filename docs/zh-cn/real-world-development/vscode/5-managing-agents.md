---
title: "练习 5 - 监控和管理代理"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

[← 上一课：自定义代理][previous-lesson]

VS Code 中的 Copilot Chat 会实时显示工具调用、文件编辑和命令。你可以审查差异、接受或撤销编辑，并使用后续提示引导代理。

代理可能会请求运行终端命令；只批准信任的命令。打开聊天顶部的 **Files changed** 可查看本次会话修改的全部文件。

## 监控进度

1. 返回 Copilot Chat。
2. 观察文件读取、编辑和终端命令。
3. 选择 **Keep** 接受编辑，或选择 **Undo** 撤销编辑。
4. 等待高对比度模式完成。

## 添加浅色模式

在同一会话中发送：

```plaintext
Nice work! Now add a light-mode toggle alongside the high-contrast toggle. Light mode should follow the same pattern — persist via local storage and be accessible from the same area of the UI. The user should be able to enable high-contrast and light mode independently.
```

审查每项编辑；必要时使用 **Stop** 停止代理并发送澄清提示。完成后，在 **Source Control** 中检查组件、样式、无障碍属性和本地存储，然后提交更改。

确认切换控件包含 ARIA 属性、键盘导航和语义 HTML，并确认设置会通过 local storage 在页面重新加载后保留。满意后，在下一课中发布更改。

## 总结与后续步骤

你学习了如何实时监控、接受或撤销编辑，并在同一会话中扩展代理工作。接下来，继续[迭代 Copilot 的工作][next-lesson]。

[previous-lesson]: ../4-custom-agents/
[next-lesson]: ../6-iterating/
