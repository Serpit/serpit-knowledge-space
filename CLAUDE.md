# Knowledge Space — LLM Wiki Schema

这是一个由 LLM 维护的个人知识库。LLM 负责编写和维护所有 wiki 内容，用户负责资料搜集、探索和提问。

## 目录结构

```
raw/            # 原始资料（不可变，LLM 只读不写）
wiki/           # LLM 生成和维护的 wiki 页面
  index.md      # 内容目录
  log.md        # 操作时间线
  sources/      # 资料摘要页（每篇原始资料一个）
  concepts/     # 概念页（主题、方法论、理论）
  entities/     # 实体页（人物、产品、平台、公司）
  analysis/     # 综合分析页（对比、趋势、跨资料洞察）
```

## 页面格式

所有 wiki 页面使用以下 YAML frontmatter：

```yaml
---
title: 页面标题
type: source | concept | entity | analysis
created: YYYY-MM-DD
updated: YYYY-MM-DD
sources:
  - "[[资料摘要页链接]]"
tags:
  - 标签1
  - 标签2
---
```

- 使用 Obsidian `[[wikilink]]` 进行页面间交叉引用
- 摘要页的文件名使用资料标题的简短版本
- 概念页和实体页用简洁的中文命名

## 工作流程

### 摄入（Ingest）

当用户添加新资料到 `raw/` 时：

1. 读取原始资料全文
2. 与用户讨论关键要点（如用户在场）
3. 在 `wiki/sources/` 创建摘要页，包含：
   - 核心观点摘要
   - 关键论据和数据
   - 值得深入的问题
4. 识别资料中的概念和实体，创建或更新对应的 `wiki/concepts/` 和 `wiki/entities/` 页面
5. 建立所有相关页面间的 `[[wikilink]]` 交叉引用
6. 更新 `wiki/index.md`（添加新页面条目）
7. 在 `wiki/log.md` 追加摄入记录

### 查询（Query）

当用户提出问题时：

1. 先读取 `wiki/index.md` 定位相关页面
2. 阅读相关 wiki 页面
3. 综合回答，附带 `[[页面引用]]`
4. 如果答案有价值，考虑作为新页面归档到 `wiki/analysis/`

### 审查（Lint）

定期对 wiki 进行健康检查：

- 页面间的矛盾
- 过时的信息
- 孤立页面（无入站链接）
- 被提及但缺少独立页面的重要概念
- 缺失的交叉引用
- 可通过进一步研究填补的知识空白

## index.md 格式

按类别组织，每个条目一行：

```markdown
## 资料摘要
- [[页面名]] — 一行摘要（YYYY-MM-DD）

## 概念
- [[概念名]] — 一行描述

## 实体
- [[实体名]] — 一行描述

## 综合分析
- [[分析标题]] — 一行描述（YYYY-MM-DD）
```

## log.md 格式

按时间倒序，每条记录格式：

```markdown
## [YYYY-MM-DD] 操作类型 | 标题
简短描述做了什么，涉及哪些页面。
```

操作类型：`ingest`、`query`、`lint`、`update`

## 写作风格

- 中文撰写所有 wiki 内容
- 客观、简洁、信息密度高
- 标注数据来源和原文出处
- 明确区分事实陈述和分析推断
- 遇到矛盾信息时明确标注，不偏向任何一方
