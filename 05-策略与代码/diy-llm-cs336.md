# Diy-LLM：Stanford CS336 中文版，从零手搓大模型

- 来源：https://github.com/datawhalechina/diy-llm
- 在线阅读：https://datawhalechina.github.io/diy-llm/
- 入库：sikai 2026-11-10 亲自指定
- 核实：2026-11-10，仓库真实存在，公开，默认分支 main，2,883 stars、279 forks，2025-11-24 创建，2026-11-10 更新
- 许可证：CC BY-NC-SA 4.0（知识共享署名-非商业性使用-相同方式共享 4.0）

## sikai 为什么收它

这是 sikai 定的品味线之一：**要的是能跟着做出来的中文版，不是机翻稿**。Diy-LLM 是 Stanford CS336《Language Modeling from Scratch》的中文版，Datawhale 社区用半年多时间按中文学习者的习惯重新组织：补背景知识、写作业实现、核对参考内容来源、加入国产模型案例，成稿由贡献者人工撰写定稿、交叉审校，不是 AI 批量生成的内容。

## 它到底是什么

一门“大模型是怎样炼成的”课：从分词器、数据与训练，到系统优化、推理、对齐、评估与多模态，把构建 LLM 的整条链路连成一套知识体系。共 16 章正文 + 6 个配套作业。

- 第 2 章：手写 BPE 分词器；
- 第 4 章：RoPE、RMSNorm、SwiGLU、AdamW、Pre-Norm 与 Post-Norm；
- 第 5 章：混合专家模型 MoE，Top-K 路由、负载均衡、DeepSeekMoE；
- 第 6–8 章：GPU 优化、FlashAttention、CUDA / Triton、分布式训练、ZeRO；
- 第 9 章：Scaling Laws，Chinchilla 定律；
- 第 11 章：数据工程，过滤、去重、脱敏、数据配比；
- 第 13 章：预训练、SFT、DPO、RLHF；
- 第 14 章：可验证奖励的强化学习，GRPO、RLVR 与 R1 训练方案；
- 第 15 章：多模态模型，从 CLIP 到 LLaVA、Qwen-VL。

6 个作业：手搓大模型、系统优化、扩展定律、数据处理、模型对齐、模型评估，每个作业都有可运行的实现。

## 从哪开始

1. 先读前言和“学完能做什么”，确认你要的是“能动手做出来”，不是“了解概念”；
2. 按章节顺序读 `docs/zh/`，再做 `coursework/` 里的 6 个作业；
3. 没有 GPU 也能学理论部分，作业里部分内容可以在 CPU 上调试，完整训练建议用云算力。

## 对具身有什么用

这不是机器人课，是机器人背后的模型课。具身用的 VLA（视觉-语言-动作模型）、写代码的模型，底层都是这里的 Transformer、MoE、SFT、GRPO。读它不是为了马上写机器人代码，是为了明白：模型为什么是这个结构、训练时钱花在哪、GRPO 的奖励是怎么来的。14 章的 GRPO / RLVR 和 06-强化学习夹里的 Agentic RL Lab 是同一条线，可以对照着读。

## 诚实提醒

中文版按工程流程重新编排，章节编号与原版 lecture 不是一一对应，以本项目的章节顺序为准。项目与 Stanford 无官方隶属关系，原版讲义见 stanford-cs336/lectures。
