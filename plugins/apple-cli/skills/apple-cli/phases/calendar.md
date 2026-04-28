# Phase: 创建日历事件

## 默认行为

**事件默认带提前 10 分钟的提醒（display alarm）**——除非用户明确说"不要提醒"或指定其他时间。

注意：这里的「提醒」是**日历事件的 alarm**（事件开始前弹出的通知），不是 Reminders.app 的提醒事项。

## 命令模板（带默认 10 分钟提醒）

```bash
osascript -e '
tell application "Calendar"
  tell calendar "<CALENDAR_NAME>"
    set newEvent to make new event with properties {
      summary: "<TITLE>",
      start date: date "<YYYY-MM-DD HH:MM:SS>",
      end date: date "<YYYY-MM-DD HH:MM:SS>"
    }
    tell newEvent
      make new display alarm at end of display alarms with properties {trigger interval: -10}
    end tell
  end tell
end tell'
```

`trigger interval` 单位是分钟，**负数 = 事件开始前**。`-10` = 事件开始前 10 分钟。

## 提醒方式选择

- `display alarm`（默认）→ 弹出 macOS 通知 banner
- `sound alarm` → 播放声音提醒
- `mail alarm` → 发邮件（需配置）

如要播放声音，把 `display alarm` 换成：
```applescript
make new sound alarm at end of sound alarms with properties {trigger interval: -10, sound name:"Glass"}
```

## 用户明确不要提醒时

把 `tell newEvent ... end tell` 整段去掉：

```bash
osascript -e '
tell application "Calendar"
  tell calendar "<CALENDAR_NAME>"
    make new event with properties {
      summary: "<TITLE>",
      start date: date "<YYYY-MM-DD HH:MM:SS>",
      end date: date "<YYYY-MM-DD HH:MM:SS>"
    }
  end tell
end tell'
```

## 列出可用日历（不确定 CALENDAR_NAME 时）

```bash
osascript -e 'tell application "Calendar" to get name of every calendar'
```

默认日历名常见值：`"Calendar"`、`"日历"`、`"Home"`、`"Work"`。

## 执行

通过 Bash 工具执行命令。**把命令本身展示给用户**——这个 skill 的教学价值就是让用户看到他正在用 CLI。

## 契约.post

- 命令已执行成功（无错误返回）
- 默认 10 分钟提前提醒已包含（除非用户明确不要）
- 用户已看到执行的具体命令
