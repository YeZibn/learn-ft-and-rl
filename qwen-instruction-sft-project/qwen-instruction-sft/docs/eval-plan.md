# Eval Plan

## Goals

1. 检查是否能稳定遵循指令
2. 检查是否保持输出格式
3. 检查是否比基座更稳

## Evaluation Layers

### 1. 原始基座对比

对照对象：

- 原始 `Qwen/Qwen3.5-4B`
- 所有 LoRA 微调实验

目标：

- 判断微调是否真的带来改进
- 判断不同实验是否优于原始模型

### 2. 训练指标

核心指标：

1. training loss
2. eval loss
3. best checkpoint

目标：

- 检查训练是否稳定
- 检查是否过拟合
- 比较不同实验的收敛趋势

### 3. 规则评测

用于格式化任务的自动检查：

1. JSON 是否可解析
2. 三点列表是否完整
3. 单句解释是否满足要求

目标：

- 检查模型是否按格式完成任务
- 减少只看 loss 的盲区

### 4. 定性评测

固定 prompts 对比：

1. definition
2. rewrite
3. formatting
4. multi-turn

目标：

- 看输出风格是否更稳
- 看指令遵循是否更清晰
- 看是否优于原始基座

## Experiment Comparison

当前建议至少比较：

1. 原始 `Qwen/Qwen3.5-4B`
2. `exp-001-baseline-lora`
3. `exp-002-higher-rank`
4. `exp-003-lower-lr`
5. `exp-004-higher-dropout`
6. `exp-005-longer-train`

## Eval Set Design

- 不与训练集重复
- 覆盖不同任务类型
- 保留一些长尾样本

## Expected Outputs

每轮实验至少产出：

1. training loss comparison
2. eval loss comparison
3. format compliance summary
4. qualitative sample comparison
5. experiment summary table
