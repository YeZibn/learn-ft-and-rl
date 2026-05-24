# Medical Eval Plan

## Goals

1. 对比原始基座和医疗微调版本
2. 检查 medical-400 与 medical-800 的规模效应
3. 观察是否更保守、更稳健

## Experimental Levels

### 1. Baseline

- `Qwen/Qwen3.5-2B`

### 2. Medical-400

- 训练样本约 400 条
- 验证集固定
- 测试集固定

### 3. Medical-800

- 训练样本约 800 条
- 验证集固定
- 测试集固定

### 4. Ablations

- `medical-800 + lower lr`
- `medical-800 + higher rank`

## Eval Dimensions

1. instruction following
2. answer conservativeness
3. hallucination risk
4. whether it suggests further medical consultation
5. structure clarity

## Output Artifacts

1. experiment summary table
2. sample comparison table
3. qualitative notes
4. training / eval loss charts

