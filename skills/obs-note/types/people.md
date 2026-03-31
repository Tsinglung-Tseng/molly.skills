# 人物笔记规范

适用条件：笔记类型为人物（含 `#type/people` 或 `#function/biography`）。

## 必要元素

### 1. 一句话定位

在标题或开头给出一句简洁的定位，说明这个人是谁、为何重要。

> **D. Richard Hipp** 是 SQLite 之父，世界上部署最广泛的数据库的创造者。

### 2. 时间线图

使用 Mermaid `gantt` 图展示人物生平的关键节点。

### 3. 核心哲学/价值观

提炼人物最核心的思想或行事原则。不是传记罗列，而是 *这个人代表了什么*。

### 4. 名言/座右铭

在 frontmatter 中使用 `motto` 字段记录其代表性言论：

```yaml
motto:
  - "To put your code in the public domain is a generous act."
  - "We test the absolute heck out of it."
```

### 5. 个人网页

搜索，若有个人 blog 页面或大学主页则列在笔记中。

## Frontmatter 规范

```yaml
---
created: YYYY-MM-DD
type: people
tags:
  - domain/[领域]
alias:
  - [英文名]
  - [中文名]
  - [昵称/别称]
people:
  - [人物名称]
motto:
  - "[名言1]"
  - "[名言2]"
---
```

## 内容自由度

除上述必要元素外，笔记内容**由 LLM 根据语境自由组织**。不强制要求固定的章节结构。让内容服务于"为何记录这个人"的具体语境。
