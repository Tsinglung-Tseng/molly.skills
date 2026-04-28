# Apple CLI · Claude Code Skill

每个 macOS APP 背后都有一扇命令行的门。
这个 skill 用 `osascript` 直接驱动**日历 / 提醒事项 / 桌面通知**——纯 CLI，零依赖。

## 安装

在 Claude Code 中运行：

```bash
/plugin marketplace add tsinglungtseng/molly.skills
/plugin install apple-cli@molly-skills
```

装完之后 Claude Code 自动识别。下次说「**提醒我明天3点开会**」或「**把跟投资人吃饭加到日历**」就会触发。

## 用法演示

在 Claude Code 里直接说人话：

```
你：提醒我下午4点接孩子
Claude：[调 apple-cli skill] → osascript -e '... make new reminder with properties {name:"接孩子", due date:date "2026-04-28 16:00:00"}'
        ✓ 已添加到提醒事项
```

```
你：明天 19:00 跟投资人吃饭，加到日历
Claude：[调 apple-cli skill] → osascript -e '... make new event ...'
        ✓ 已添加到日历
```

```
你：弹个通知告诉我该出门了
Claude：[调 apple-cli skill] → osascript -e 'display notification "该出门了" with title "提醒" sound name "Glass"'
        ✓ 通知已弹出
```

## 为什么不用 MCP？

MCP 解决信任边界（企业、外部 API、权限隔离）——但你自己电脑上的日历 / 提醒 / 通知不需要那层。`osascript` 这种"老技术"在 LLM 训练数据里出现过百万次，模型天生会用。

详见视频：「**CLI 才是 AI 的母语**」（小红书 / 抖音搜索）。

## 命令速查

| 操作 | 命令 |
|---|---|
| 加日历事件 | `osascript -e 'tell app "Calendar" to tell calendar "X" to make new event ...'` |
| 加提醒 | `osascript -e 'tell app "Reminders" to tell list "X" to make new reminder ...'` |
| 桌面通知 | `osascript -e 'display notification "..." with title "..."'` |
| 查日历 | `osascript -e 'tell app "Calendar" to get name of every calendar'` |
| 今日日程 | `icalBuddy eventsToday`（先 `brew install ical-buddy`） |

完整模板见 `SKILL.md`。

## License

MIT
