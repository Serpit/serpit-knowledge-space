---
title: 为什么AI只会说正确的废话，以及怎么把它逼出舒适区
type: source
created: 2026-04-11
updated: 2026-04-11
sources:
  - "raw/为什么AI只会说正确的废话，以及怎么把它逼出舒适区.md"
tags:
  - AI
  - Context Infrastructure
  - 认知框架
---

# 为什么AI只会说正确的废话，以及怎么把它逼出舒适区

**作者**：[[鸭哥]]
**来源**：superlinear.academy

## 核心观点

LLM 的默认输出是 consensus（共识），这由训练机制决定。要突破这个天花板，关键不在于升级模型，而在于注入个人认知上下文（context）。文章提出了一个完整的 Context Infrastructure 系统。

## 关键论点

### Consensus 天花板
- LLM 训练的本质是 next token prediction → 输出概率最高（=共识）的 token
- RLHF 进一步惩罚有争议的输出，鼓励平衡无偏向的回答
- Deep Research 实际上是 Wide Research — 解决的是**信息**不对称，而非**认知**不对称
- AI 可以把小白提升到大众平均水平，但对已在平均水平之上的人几乎无增量

### 从 CPU Bound 到 Memory Bound
- 实验：同模型、同工具、同 prompt，唯一区别是 context → 产出性质完全不同
- 结论：**决定产出性质的是 context，不是模型智能**（在模型智能跨过一道坎之后）
- 类比：CPU 快到一定程度后，提升来自内存架构
- 模型智能不断贬值（人人可用），个人 context 不贬值 → 投资收益递减 vs 累积

### Context Infrastructure 三要素

**1. 大量积累**
- 采集客观行为数据（录音转写、会议记录、微信对话、与 AI 每次交互）
- 自己很难从中提取模式，AI 作为旁观者更合适
- 所有数据放在同一文件夹，支持 cross-reference

**2. 分层提炼**（受 [[OpenClaw]] 启发）
- 筛选标准：**稳定性** — 跨场景、跨时间反复出现的判断才是自我认知结构
- L1 Observer：每天扫描文件变动，提取观察
- L2 Reflector：每周合并重复、清理过期、识别跨项目模式
- L3 Axiom：从稳定模式中蒸馏决策原则
- 经过一年积累 → 44 条 axiom
- 与 [[Mem0]] 的区别：Mem0 蒸馏到事实层（"你偏好 TypeScript"），此系统蒸馏到**判断原则层**（"你怎么权衡可维护性和性能"）

**3. 按需加载**
- Skill 系统：每个 skill 是针对特定任务类型的 context 子集
- 类比 CPU 内存层级：L1=AGENTS.md，L2=skill 库索引，L3=具体 skill 文件
- 渐进披露，只在需要时调用

### 飞轮循环
- 知识产品在消费 context 的同时产生新 context
- 每日 AI 简报 → 消费 axiom + 产出新观察
- 领域调研报告 → 更新认知框架
- 本质：把你的 bias 注入 AI → 显性化 bias 本身就有自我认知价值

## 实验细节
- 对照：Claude Opus 4.6 vs GPT-5.4，同 prompt/工具/后端
- 有 context 的报告：输出 insight（"完美主义是吞吐量的敌人"）
- 无 context 的报告：输出 checklist（正确但无启发）

## 开源参考
- [context-infrastructure](https://github.com/grapeot/context-infrastructure)：完整结构、44 条 axiom、核心 skill、三层记忆系统代码

## 值得深入的问题
- 44 条 axiom 的具体内容和分类方式
- L1→L2→L3 精炼过程的自动化程度
- context density 到什么阈值才能有效压过 consensus prior
