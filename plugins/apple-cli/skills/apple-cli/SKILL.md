---
name: apple-cli
description: >
  通过 osascript 直接操作 macOS 原生应用——日历、提醒事项、桌面通知，
  纯命令行，无需 MCP server。当用户提到"加日历"、"加事件"、"提醒我"、
  "添加提醒"、"发通知"、"显示通知"、"明天X点开会"、"今天日程"、
  "add to calendar"、"remind me"、"create reminder"、"show notification"
  时立即触发。同样适用于：用户想批量创建提醒、把任务清单一次写到提醒事项、
  让 Claude 帮忙安排日程并自动落库时。
allowed-tools:
  - Bash
---

通过 osascript 把日历事件、提醒事项、桌面通知"写"出来——每个 macOS APP 背后都有一扇命令行的门。

## 执行流程

本 skill 按阶段执行，每阶段按需加载本 skill 目录下的规则文件。

### Phase 1: 识别意图 + 解析时间
Read 本 skill 目录下的 `phases/identify.md` 并执行。
契约.post: 已确定走哪个（或哪几个）分支（calendar / reminder / notification / query），已收集执行所需的全部参数。

### Phase 2: 执行（按分支条件加载，只加载匹配的）

根据 Phase 1 结果，**只 Read 本 skill 目录下与本次任务相关的分支文件**：

- 若 calendar → Read `phases/calendar.md`
- 若 reminder → Read `phases/reminder.md`
- 若 notification → Read `phases/notification.md`
- 若 query → Read `phases/query.md`

如同时多个分支（例：用户一次说"加日历并提醒我"），按顺序逐个 Read 并执行。

契约.post: 命令已通过 Bash 执行，结果已展示给用户（包括命令本身——这个 skill 的教学价值就是让用户看到他正在用 CLI）。

### Phase 3: 错误处理（仅出错时加载）

若 Phase 2 命令执行失败、报权限错误、或日历/列表名不存在：
Read 本 skill 目录下的 `phases/errors.md` 并按其指引处理。

否则跳过此阶段。

## 设计哲学

这个 skill 的目的不是省事——MCP 也能做。它的目的是**展示 CLI 的可组合性**：
- 同一行 `osascript -e '...'` 模板，改几个词就能驱动十几个 APP
- 命令可以写进脚本、和其他工具用 `|` 连接
- 没有 MCP server 启动成本，没有 token 浪费在 schema 上

对应视频：「9¾ 站台——每个 APP 都有一扇命令行的门」。
