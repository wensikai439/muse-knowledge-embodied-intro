# 从零开始学 Agent · 第 10 章 Agentic-RL：智能体强化学习训练

- 来源：https://haozhe-xing.github.io/agent_learning/zh/chapter_agentic_rl/
- 入库：sikai 2026-11-10 亲自指定，sikai 点名要的是 10.2 节
- 核实：2026-11-10，在线书真实存在，第 10 章目录与 10.2 节标题已核对；GitHub 仓库地址未核实，以上面这个在线阅读地址为准

## sikai 为什么收它

这是 sikai 定的品味线之一：**先把 SFT + LoRA 这一步做扎实，再谈强化学习**。第 10 章的逻辑就是这条线：Agent 不能只靠提示词，能力上界就是基座模型的上界；Agentic-RL 是让模型通过反复实践自己悟出最优解法。

## 它到底讲什么

第 10 章学完后，你应该能做到：理解 Agentic-RL 的概念和技术路线；掌握 SFT + LoRA 的实现方法；深入理解 PPO、DPO、GRPO 三大算法的原理；了解 DP / TP / PP / SP / ZeRO 分布式训练方法；完成一个完整的 SFT + GRPO 训练 Pipeline；通过最小可运行 demo 理解 GRPO / RLVR 的组内采样、相对优势和 KL 约束；掌握专为 Agent 微调的数据构建方法（工具调用轨迹、Gorilla / ToolBench 数据集）。

章节结构：

| 节 | 内容 | 核心收获 |
|---|---|---|
| 10.1 | 什么是 Agentic-RL | 理解 Agentic-RL 与传统后训练的本质区别，掌握 MDP 框架建模方法 |
| 10.2 | SFT + LoRA 基础训练 | 掌握监督微调的形式化原理与 LoRA 参数高效训练方法 |
| 10.2b | 分布式训练基础 | DP / TP / PP / SP / ZeRO 分布式训练方法 |
| 10.3 | PPO：近端策略优化 | 从策略梯度出发，系统理解重要性采样、优势函数、GAE 和 Clip 机制 |
| 10.4 | DPO：直接偏好优化 | 掌握从 RLHF 到 DPO 的完整数学推导，理解隐式奖励的思想 |
| 10.5 | GRPO / GSPO + 奖励函数设计 | 理解组内比较替代 Critic 的原理，以及多维度奖励函数设计与奖励黑客防御 |
| 10.6 | 实战：完整训练 Pipeline | 先用最小 GRPO / RLVR demo 跑通核心机制，再基于 GSM8K 完成从数据准备到模型部署的完整训练 |
| 10.7 | 最新研究进展（2025—2026） | 纵览 DeepSeek-R1、DAPO、VAPO、SAR、T-STAR、UCPO、DelTA、SRPO、GROW 等前沿工作 |
| 10.8 | 专为 Agent 的微调 | 工具调用数据构建、三大开源数据集（Gorilla / ToolBench / AgentInstruct）、Agent SFT 专项配置 |

## 10.2 节要先弄懂的两个词

- **SFT（监督微调，Supervised Fine-Tuning）**：用标注好的“输入—标准输出”对训练模型，告诉模型该用什么格式、什么风格、什么流程回答。便宜、快、稳，是几乎所有部署模型都会经过的一步。
- **LoRA（低秩适配，Low-Rank Adaptation）**：不动原始的大权重矩阵，只在旁边挂一个很小的“补丁”（低秩矩阵）来学习任务，参数量仅占原始的 1%–5%，却能接近全参微调的效果。

## 从哪开始

sikai 点名要的是 10.2，先读 10.2，把 SFT + LoRA 的形式化原理和实现方法弄懂；再读 10.1，弄清 Agentic-RL 和传统后训练的区别；然后按 10.3 → 10.4 → 10.5 的顺序读 PPO、DPO、GRPO；最后读 10.6 的实战 Pipeline，跑通最小 demo。

## 对具身有什么用

这章是 06-强化学习夹里“从 SFT 到 RL”的那座桥：机器人策略也一样，先用示范数据做 SFT 定格式、定行为，再用强化学习在环境里试错、改策略。10.8 的工具调用数据构建，对具身也直接有用——机器人的工具调用轨迹，和 Agent 的工具调用轨迹是同一类数据。
