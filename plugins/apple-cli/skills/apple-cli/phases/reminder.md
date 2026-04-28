# Phase: 添加提醒事项

## 单条命令模板

```bash
osascript -e '
tell application "Reminders"
  tell list "<LIST_NAME>"
    make new reminder with properties {
      name: "<CONTENT>",
      due date: date "<YYYY-MM-DD HH:MM:SS>"
    }
  end tell
end tell'
```

如果用户没指定 `due date`（截止时间），可省略 `due date` 这一行——提醒会作为无时限项。

## 列出可用提醒列表（不确定 LIST_NAME 时）

```bash
osascript -e 'tell application "Reminders" to get name of every list'
```

默认列表名 `"Reminders"`（中文系统可能是 `"提醒事项"`）。

## 批量添加（用户给一串列表）

```bash
for item in "带合同" "确认会议室" "打印名片"; do
  osascript -e "tell application \"Reminders\" to tell list \"Reminders\" to make new reminder with properties {name:\"$item\"}"
done
```

## 执行

通过 Bash 工具执行命令。**把命令本身展示给用户**——这个 skill 的教学价值就是让用户看到他正在用 CLI。

## 契约.post

- 命令已执行成功（无错误返回）
- 用户已看到执行的具体命令
