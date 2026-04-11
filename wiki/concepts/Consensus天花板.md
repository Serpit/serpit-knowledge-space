---
title: Consensus 天花板
type: concept
created: 2026-04-11
updated: 2026-04-11
sources:
  - "[[AI正确的废话与Context突破]]"
tags:
  - AI
  - LLM
  - 核心概念
---

# Consensus 天花板

## 定义

LLM 的默认输出天然趋向共识（consensus），这是由训练机制决定的结构性限制，而非能力不足。

## 形成机制

1. **Next Token Prediction**：每步输出概率最高的 token → 最多人认同的内容
2. **RLHF 安全对齐**：惩罚有争议的、带强烈立场的输出，鼓励平衡全面的回答
3. 两层叠加 → 默认行为是**回归均值**

## 表现

- AI 产出像"正确的废话"：找不出错误，但没有启发
- Deep Research 实际是 Wide Research：解决信息不对称，非认知不对称
- 可以把小白提升到大众平均水平，但对超越平均水平的人几乎无增量
- "深刻"的定义本身就是非共识，而非共识恰好是 LLM 被训练去规避的

## 突破路径

用足够密度的个人认知上下文压过训练时的 consensus prior。参见 [[上下文工程]] 中的 Context Infrastructure 方法。

几句话的 system prompt 做不到 → 需要一套系统来采集和精炼个人认知。

## 相关概念
- [[上下文工程]]：突破天花板的系统性方法
- [[AI Agent]]：天花板在 Agent 场景中同样存在
