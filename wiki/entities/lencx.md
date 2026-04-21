---
title: lencx（浮之静）
type: entity
created: 2026-04-21
updated: 2026-04-21
sources:
  - "[[Agent Memory架构本质]]"
tags:
  - 人物
  - AI
  - Agent
---

# lencx（浮之静）

## 简介

AI 领域独立写作者，运营公众号"浮之静"。关注 Agent 架构、Harness、Memory、Token 命名、AI 操作系统等工程与哲学交叉议题。写作风格自称"暴论"，观点密度高、敢于对流行叙事划界。

## 主要观点

- **Memory 的难点从来不在容量，在治理**——写入/管理/读取/遗忘都是治理问题。
- **Memory ≠ State / Policy / Profile / 蒸馏**：四组边界必须划清，否则概念越讲越大。
- **Agent 记忆的四个建模对象**：用户模型、任务模型、世界模型、自我模型；意图是四层耦合后浮现的上层能力。
- **记忆单元六维**（内容、类型、置信度、来源、作用域、时间衰减）与**五类型**（event / assertion / belief / constraint / commitment）。
- **读取范式升级**：从 `retrieve(query)` 到 `read(task_context, belief_graph)`。
- **死的不是经验本身，而是那些失去了更新机制的经验**。

## 相关创作（文中自荐）

- 《知识会长成"壳"，禁锢你》
- 《Agent 暴论：你不是造物主，是保姆》
- 《Token 命名困境：当信息论闯入语言学》
- 《AI 操作系统：从指令到意图》
- 《元技能：让 AI 像你一样思考》
- 《Ilya Sutskever：AI 研究、泛化与未来之路》

注：Claude Code 源码中包含大量 memory 设计，作者评价 memory 在工程上"不亚于一套大型系统设计"的交叉学科领域。

## 相关页面

- [[Agent Memory架构本质]]
- [[Agent Memory]]
