# 基于 Qwen 的 Agent 进阶微调与强化学习教学大纲

## 课程定位

这是一条从基础知识到 Agent 训练与部署的完整学习路线，重点是把 Qwen 作为统一底座，系统学习：

1. 监督微调
2. 偏好学习
3. 强化学习
4. Agent 数据构建
5. Agent 评测与系统落地

## 课程设计原则

1. 先补前置知识，再进训练与对齐
2. 先做单轮能力，再做多轮轨迹
3. 先学数据与评测，再学优化算法
4. 先掌握工程可复现性，再追求算法复杂度
5. 先把 SFT 做扎实，再上偏好学习和 RL

## 前置知识分层

### A. 必备基础

1. Python 基础
2. Linux 与命令行
3. Git 基础
4. PyTorch 张量、反向传播、优化器
5. 机器学习基本概念：训练、验证、过拟合、泛化

### B. LLM 进入门槛

1. Transformer 自注意力
2. Decoder-only 架构
3. Tokenizer 与上下文窗口
4. 自回归语言建模目标
5. Prompt、Chat template、system/user/assistant 结构

### C. 训练与部署基础

1. 显存、batch、gradient accumulation
2. LoRA / QLoRA 的基本概念
3. Hugging Face 生态
4. 基础评测方法
5. 推理与服务化的基本约束

## 学习分层

### 第一层：基础认知

- 模块 0: Agent, Qwen, and Training Paradigms Overview
- 模块 1: Qwen Model Ecosystem
- 模块 2: Transformer and SFT Foundations

### 第二层：SFT 与工程

- 模块 3: SFT Pipeline
- 模块 4: Agent SFT Data
- 模块 5: PEFT and Training Engineering

### 第三层：偏好学习与 RL

- 模块 6: Preference Learning
- 模块 7: RL Foundations
- 模块 8: LLM RL in Qwen Practice

### 第四层：Agent 专项能力

- 模块 9: Agent Reinforcement Learning
- 模块 10: Process Supervision, Reflection, and Search
- 模块 11: Memory and RAG

### 第五层：评测、安全、部署与前沿

- 模块 12: Agent Evaluation
- 模块 13: Safety, Alignment, and Robustness
- 模块 14: Deployment and Optimization
- 模块 15: Frontier Topics

## 模块设计说明

每个模块按以下维度组织：

1. 为什么学
2. 需要哪些前置知识
3. 核心概念
4. 关键实践
5. 典型错误
6. 本模块产出

## 模块 0: Agent, Qwen, and Training Paradigms Overview

### 目标

建立全局地图，理解 Agent 训练不是单点算法问题，而是数据、模型、奖励、工具、评测共同作用的系统问题。

### 核心内容

1. 什么是 LLM Agent
2. Agent 与 Chat Model 的差别
3. Qwen 作为底座模型的角色
4. Continued Pretraining, SFT, Preference Learning, RL 的关系
5. 任务完成率、工具成功率、恢复能力为什么比 loss 更重要
6. Agent 的基本能力拆解：指令跟随、工具使用、规划、反思、记忆、检索、执行与恢复

### 建议产出

- 画出 Agent 能力树
- 画出训练范式路线图

## 模块 1: Qwen Model Ecosystem

### 目标

理解 Qwen 系列模型、Tokenizer、Chat template、工具调用格式和训练生态。

### 核心内容

1. Qwen model family
2. Base / Instruct / MoE / multimodal 的差异
3. Chat template 与 special tokens
4. Hugging Face、PEFT、TRL、vLLM、LLaMA-Factory、ms-swift、verl
5. Tool calling 与结构化输出
6. 常见格式错配问题

### 建议产出

- 跑通 Qwen 推理
- 跑通 Qwen LoRA demo

## 模块 2: Transformer and SFT Foundations

### 目标

补齐模型与训练的底层原理，为后续微调和对齐打牢基础。

### 核心内容

1. Transformer decoder-only 结构
2. 自回归目标与 token-level loss
3. instruction tuning 的本质
4. 数据质量与行为质量的差异
5. 为什么 SFT 会学会模式，但不一定学会偏好
6. 训练退化的常见原因

### 建议产出

- 能解释一个模型是如何通过 next-token prediction 学到行为的

## 模块 3: SFT Pipeline

### 目标

掌握监督微调的完整流程。

### 核心内容

1. 数据格式与 schema
2. 数据清洗、去重、切分
3. 数据混合与配比
4. Full fine-tuning, LoRA, QLoRA
5. 超参数与训练监控
6. 评测与回归检查

### 建议产出

- 一套可复用的 SFT pipeline

## 模块 4: Agent SFT Data

### 目标

把“对话数据”升级成“任务轨迹数据”。

### 核心内容

1. trajectory 结构
2. tool-use 样本
3. planning 样本
4. reflection / correction 样本
5. 多轮任务分解
6. 合成数据与 teacher distillation
7. 过程监督与结果监督的区别

### 建议产出

- 一个 Agent trajectory schema
- 一批工具调用样本

## 模块 5: PEFT and Training Engineering

### 目标

掌握高效训练和工程稳定性。

### 核心内容

1. LoRA / QLoRA 原理
2. target modules 的选择
3. rank, alpha, dropout 的影响
4. 显存与吞吐估算
5. FSDP / DeepSpeed / ZeRO
6. checkpoint、恢复、稳定性排障

### 建议产出

- 单机或多卡可复现实验脚本

## 模块 6: Preference Learning

### 目标

理解偏好学习为何是 SFT 之后的关键层。

### 核心内容

1. 偏好数据的定义
2. Reward model 与 pairwise preference
3. DPO, ORPO, KTO, SimPO 的基本差异
4. 偏好学习如何改变行为排序
5. 偏好学习的局限

### 建议产出

- 一个小型偏好学习实验

## 模块 7: RL Foundations

### 目标

建立强化学习的数学与算法底座。

### 核心内容

1. MDP / POMDP
2. policy, reward, value, return
3. REINFORCE
4. actor-critic
5. PPO
6. KL 约束
7. sparse reward 和 credit assignment

### 建议产出

- 能解释 PPO 为什么适合 LLM 优化

## 模块 8: LLM RL in Qwen Practice

### 目标

把 RL 真正用到 Qwen 上。

### 核心内容

1. RLHF 流程
2. RLAIF
3. DPO 与 PPO 的边界
4. GRPO 与 group-based optimization
5. outcome reward 与 process reward
6. rule-based reward 与 verifier-based reward

### 建议产出

- 一个可运行的 Qwen RL demo

## 模块 9: Agent Reinforcement Learning

### 目标

把训练对象从“回答质量”转向“任务完成质量”。

### 核心内容

1. tool-use RL
2. web / code / environment interaction
3. trajectory-level reward
4. intermediate reward
5. recovery behavior
6. reward hacking

### 建议产出

- 一个任务完成率可观测的 Agent RL 环境

## 模块 10: Process Supervision, Reflection, and Search

### 目标

让模型不仅看结果，也看过程。

### 核心内容

1. process supervision
2. ReAct
3. self-reflection
4. verifier-guided reasoning
5. tree search / beam search / MCTS 的位置
6. test-time compute 与训练的关系

### 建议产出

- 一个带自检机制的 Agent

## 模块 11: Memory and RAG

### 目标

让 Agent 学会使用外部知识与长期记忆。

### 核心内容

1. RAG 基础
2. retrieval / rerank / generation
3. short-term memory 与 long-term memory
4. memory write / read 策略
5. 什么时候用参数记忆，什么时候用外部记忆

### 建议产出

- 一个接入检索与记忆的 Agent

## 模块 12: Agent Evaluation

### 目标

建立可复现、可比较的评测体系。

### 核心内容

1. exact match, pass@k, win rate, success rate
2. tool selection accuracy
3. tool argument accuracy
4. plan quality
5. recovery rate
6. online vs offline evaluation
7. judge model 的偏差

### 建议产出

- 一个 Agent eval benchmark

## 模块 13: Safety, Alignment, and Robustness

### 目标

控制 Agent 行为风险。

### 核心内容

1. prompt injection
2. tool abuse
3. hallucinated tool use
4. refusal 与 helpfulness 的平衡
5. sandbox 与 permission
6. 对抗测试与策略约束

### 建议产出

- 一套安全测试用例

## 模块 14: Deployment and Optimization

### 目标

把模型与 Agent 稳定部署到真实系统。

### 核心内容

1. vLLM 部署
2. batching 与 KV cache
3. latency / throughput tradeoff
4. function calling 服务化
5. logging, replay, feedback loop
6. versioning 与 rollback

### 建议产出

- 一个可观测、可回放、可迭代的服务

## 模块 15: Frontier Topics

### 目标

建立后续持续扩展的研究视野。

### 核心内容

1. multi-agent
2. self-play
3. curriculum learning
4. code agent
5. web agent
6. multimodal agent
7. long-horizon optimization

### 建议产出

- 一份前沿论文跟踪清单

## 课程建议顺序

1. 模块 0
2. 模块 1
3. 模块 2
4. 模块 3
5. 模块 4
6. 模块 5
7. 模块 6
8. 模块 7
9. 模块 8
10. 模块 9
11. 模块 10
12. 模块 11
13. 模块 12
14. 模块 13
15. 模块 14
16. 模块 15

## 索引同步规则

新增、删除、重命名模块后，必须同步更新 `index/index.md`。
