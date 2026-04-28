# Phase: 桌面通知

## 命令模板

```bash
osascript -e 'display notification "<BODY>" with title "<TITLE>" subtitle "<SUBTITLE>" sound name "Glass"'
```

`subtitle` 和 `sound name` 都可省略。

可选 `sound name`：`"Glass"`、`"Hero"`、`"Ping"`、`"Pop"`、`"Submarine"`、`"Funk"`、`"Bottle"`、`"Frog"`。

## 执行

通过 Bash 工具执行。**展示命令给用户**。

## 契约.post

- 通知已弹出
- 用户已看到执行的具体命令
