# Phase: 错误处理

仅在 Phase 2 命令执行报错或权限被拒时加载。

## 常见错误及处理

### "日历不存在" / "Can't find calendar"

列出可用日历让用户选：

```bash
osascript -e 'tell application "Calendar" to get name of every calendar'
```

中文系统常见值：`"日历"`、`"工作"`、`"个人"`。
英文系统常见值：`"Calendar"`、`"Home"`、`"Work"`。

### "列表不存在" / "Can't find list"

列出可用提醒列表：

```bash
osascript -e 'tell application "Reminders" to get name of every list'
```

### 时间解析失败 / "Can't make ... into type date"

通常是日期字符串格式问题。改用：
- 标准：`"YYYY-MM-DD HH:MM:SS"`（如 `"2026-04-28 19:00:00"`）
- 英文：`"April 28, 2026 19:00:00"`

如系统语言为中文，AppleScript 也接受 `"2026年4月28日 19:00:00"`。

### 权限被拒（错误码 -1743 / "Not authorized to send Apple events"）

引导用户开启自动化权限：

> 打开「系统设置 → 隐私与安全性 → 自动化」。
> 找到 **Terminal**（或 Claude Code 用的终端 app）展开列表。
> 把对应 APP（**日历** / **提醒事项**）的开关打开。

如果列表里没有 Terminal/Claude Code 条目，先尝试再次执行命令——系统会自动弹权限请求。

### 第一次运行的权限弹窗

第一次执行时 macOS 会弹权限请求：
- "Terminal 想要访问你的日历" → 允许
- "Terminal 想要访问你的提醒事项" → 允许
- 通知不需要授权

## 契约.post

- 已识别错误类型
- 已给出明确的修复指引
- （若可恢复）已重试命令
