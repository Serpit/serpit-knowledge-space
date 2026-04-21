# Knowledge Space — LLM Wiki Schema

这是一个由 LLM 维护的个人知识库。LLM 负责编写和维护所有 wiki 内容，用户负责资料搜集、探索和提问。

## 目录结构

```
raw/            # 原始资料（不可变，LLM 只读不写）
wiki/           # LLM 生成和维护的 wiki 页面
  index.md      # 内容目录
  log.md        # 操作时间线
  rubric.md     # 资料质量评分标准（摄入时参照）
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

### source 页扩展字段

`type: source` 的摘要页在上述基础 frontmatter 外，额外包含质量评估字段：

```yaml
quality:
  density: 1-5       # 信息密度
  factuality: 1-5    # 事实性
  originality: 1-5   # 原创性
  clarity: 1-5       # 结构清晰度
  overall: 1-5       # 综合（主观判断，不必是平均）
bias:                # 立场标签，可多选
  - neutral | vendor | opinion
red_flags:           # 劣质信号，可空
  - 简短描述
review: 一两句评分理由
```

评分标准见 `wiki/rubric.md`。摘要页正文顶部应包含"质量评估"小节，复述 review 和关键理由。

## 工作流程

### 摄入（Ingest）

当用户添加新资料到 `raw/` 时：

1. 读取原始资料全文
2. **先在对话中向用户给出以下内容，等待用户确认或调整后再落盘：**
   - 资料摘要（核心观点、关键论据和数据、值得深入的问题）
   - 质量评估：五个维度的建议分、综合 overall、bias 标签、red_flags、一两句评分理由
   - 参照 `wiki/rubric.md` 的标准
3. 用户确认后，在 `wiki/sources/` 创建摘要页，写入最终评分到 frontmatter，正文顶部包含"质量评估"小节
4. 识别资料中的概念和实体，创建或更新对应的 `wiki/concepts/` 和 `wiki/entities/` 页面
5. 建立所有相关页面间的 `[[wikilink]]` 交叉引用
6. 更新 `wiki/index.md`（添加新页面条目，含 overall 分数）
7. 在 `wiki/log.md` 追加摄入记录（含 overall 分数）

**关键原则**：LLM 不自动落盘评分，评分必须经用户确认。用户可质疑/调整任意维度，给出理由后重新打分。

### 查询（Query）

当用户提出问题时：

1. 先读取 `wiki/index.md` 定位相关页面
2. 阅读相关 wiki 页面
3. 综合回答时按 source 质量加权：
   - `overall ≥ 4`：主论据，放心引用
   - `overall = 3`：可作为佐证，注意交叉验证
   - `overall ≤ 2`：仅作为"有人这么说"提及，明确标注质量偏低
   - `bias: vendor` 的一手信息可用，但必须注明立场
4. 综合回答，附带 `[[页面引用]]`
5. 如果答案有价值，考虑作为新页面归档到 `wiki/analysis/`

### 审查（Lint）

定期对 wiki 进行健康检查：

- 页面间的矛盾
- 过时的信息
- 孤立页面（无入站链接）
- 被提及但缺少独立页面的重要概念
- 缺失的交叉引用
- 可通过进一步研究填补的知识空白

## index.md 格式

按类别组织，每个条目一行。资料摘要条目前置 overall 分数以便快速判断：

```markdown
## 资料摘要
- [[页面名]] `[4]` — 一行摘要（YYYY-MM-DD）

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
