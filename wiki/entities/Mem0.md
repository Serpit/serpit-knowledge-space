---
title: Mem0
type: entity
created: 2026-04-11
updated: 2026-04-11
sources:
  - "[[AI正确的废话与Context突破]]"
  - "[[Agent原理架构与工程实践]]"
tags:
  - 产品
  - AI
  - 记忆系统
---

# Mem0

## 简介

一个 AI 记忆系统（mem0.ai），用于为 LLM 提供持久化的用户记忆。

## 局限性（[[鸭哥]]的批评）

Mem0 的蒸馏只到**事实层**就停了：
- "你偏好 TypeScript"
- "你住在上海"

事实告诉 AI **你是谁**，但无法告诉 AI **你怎么想**。

要让 AI 产出从 consensus 变成 non-consensus，需要深入到**判断原则层**：
- "评估技术方案时，你怎么权衡可维护性和性能"
- "你的优先级排序是什么"

这是 Context Infrastructure 与 Mem0 的核心区别。参见 [[上下文工程]]。

## 相关页面
- [[AI正确的废话与Context突破]]
- [[OpenClaw]]（更深度的记忆实现）
