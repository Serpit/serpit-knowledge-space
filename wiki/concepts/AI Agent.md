---
title: AI Agent
type: concept
created: 2026-04-11
updated: 2026-04-11
sources:
  - "[[Agent原理架构与工程实践]]"
  - "[[AI正确的废话与Context突破]]"
  - "[[Agentic Engineering工程革命]]"
tags:
  - AI
  - 核心概念
---

# AI Agent

## 定义

执行路径由 LLM 动态决定（而非代码预先写死）的 AI 系统。与 Workflow 的核心区别在于控制权掌握在谁手里。

## 核心循环

感知 → 决策 → 行动 → 反馈，不断循环直到模型返回纯文本。核心实现不到 20 行代码，扩展能力不改循环本身。

## 五种控制模式

1. **提示链**：顺序步骤，适合线性流程
2. **路由**：输入分类 → 专用处理流程
3. **并行**：分段法/投票法
4. **编排器-工作者**：中央 LLM 动态分解任务
5. **评估器-优化器**：生成-评估循环

## 工程关键点

- [[Harness工程]] 比模型更关键
- [[上下文工程]] 决定稳定性
- 工具设计按 ACI 原则（面向 Agent 目标，非底层 API）
- 记忆系统分四层（工作/程序性/情景/语义）
- 评测先于调优

## 代表实现
- [[OpenClaw]]：五层解耦的开源 Agent 框架
- Claude Code、Codex 等编码 Agent

## 相关概念
- [[Agentic Engineering]]：人从代码编写者转为 Agent 协调者的工程范式
- [[Consensus天花板]]：Agent 同样面临的产出质量限制
- [[AI变现]]：Agent 技术的商业化方向
