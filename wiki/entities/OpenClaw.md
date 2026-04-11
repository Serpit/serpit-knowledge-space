---
title: OpenClaw
type: entity
created: 2026-04-11
updated: 2026-04-11
sources:
  - "[[Agent原理架构与工程实践]]"
  - "[[AI正确的废话与Context突破]]"
tags:
  - 产品
  - AI Agent
  - 开源
---

# OpenClaw

## 简介

一个开源的 [[AI Agent]] 框架，把上下文分层、Skills 延迟加载、结构化通信协议和文件系统状态等工程原则落地为可运行系统。

## 五层架构

1. **Gateway**：WebSocket 服务，统一路由消息
2. **Channel 适配器**：23+ 渠道统一接口（Telegram、Discord、飞书等）
3. **Pi Agent**：维护主循环、会话状态、调度
4. **工具集**：shell/fs/web/browser/MCP，按 ACI 原则设计
5. **上下文+记忆**：Skills 延迟加载 + MEMORY.md，50% token 阈值自动整合

## 关键设计

- **消息总线**：Channel 和 Agent 解耦，渠道只管收发
- **SOUL.md**：定义 Agent 身份、约束、完成标准
- **cron + heartbeat**：主动触发模式，不等用户消息
- **长任务恢复**：进度写磁盘，崩溃后从断点继续
- **安全边界**：白名单授权 + 工作空间隔离 + 操作审计日志

## 记忆系统（混合检索）

1. `memory/YYYY-MM-DD.md`：追加写日志
2. `MEMORY.md`：精选事实，Agent 主动维护
3. `memory_search`：70% 向量 + 30% 关键词混合检索

[[鸭哥]]的 Context Infrastructure 分层提炼系统受 OpenClaw 启发。

## 相关页面
- [[Agent原理架构与工程实践]]
- [[AI Agent]]
- [[上下文工程]]
