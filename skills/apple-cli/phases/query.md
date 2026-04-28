# Phase: 查询今日日程

## 选项 1：ical-buddy（推荐）

需要先 `brew install ical-buddy`（一次性安装）。

```bash
icalBuddy eventsToday              # 今天
icalBuddy eventsToday+3            # 今天到 3 天后
icalBuddy -nc -ec "<排除某日历>" eventsToday   # 排除某日历
icalBuddy -ic "<只看某日历>" eventsToday        # 只看某日历
```

输出格式较友好（已含时间和日历名）。

## 选项 2：纯 osascript（无需安装）

```bash
osascript -e '
tell application "Calendar"
  set today to current date
  set hours of today to 0
  set minutes of today to 0
  set seconds of today to 0
  set tomorrow to today + (1 * days)
  set output to ""
  repeat with cal in calendars
    set evts to (every event of cal whose start date ≥ today and start date < tomorrow)
    repeat with e in evts
      set output to output & (summary of e) & " @ " & (start date of e as string) & linefeed
    end repeat
  end repeat
  return output
end tell'
```

## 执行

通过 Bash 执行，把结果格式化展示给用户。

## 契约.post

- 已查询到结果（即使是空）
- 用户已看到执行的命令和结果
