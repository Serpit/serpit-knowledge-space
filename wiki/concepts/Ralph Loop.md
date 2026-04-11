---
title: Ralph Loop
type: concept
created: 2026-04-12
updated: 2026-04-12
sources:
  - "[[Agentic Engineering工程革命]]"
tags:
  - AI Agent
  - 工程模式
---

# Ralph Loop

## 定义

一种 Agent 迭代执行机制：把同一 Prompt 反复喂给 AI，状态通过文件系统传递。

## 工作原理

1. Agent 每轮读取 `state.json`，按 `current_phase` 执行对应步骤
2. 完成时输出 `<promise>` 标记
3. Stop Hook 检测到标记后允许退出
4. 下一轮再次进入，读取更新后的状态继续

## 适用场景

多步骤、跨系统、需迭代修复的任务。在 [[Agentic Engineering工程革命]] 的运营活动配置案例中，驱动了 10 步执行流程（需求解析 → 商品创建 → 活动创建 → 配置生成 → Go 校验 → DB 写入 → API 验证 → 前端验证 → 玩法引擎测试 → 经验沉淀）。

## 相关概念
- [[Agentic Engineering]]：Ralph Loop 所属的工程体系
- [[AI Agent]]：Ralph Loop 的执行主体
