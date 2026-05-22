# Tech Stack

## Baseline Model

- `Qwen/Qwen2.5-3B-Instruct`

## Fallback Model

- `Qwen/Qwen2.5-1.5B-Instruct`

## Training Stack

- `transformers`
- `datasets`
- `peft`
- `accelerate`
- `trl`

## Optional Utilities

- `matplotlib`
- `seaborn`
- `pandas`

## Evaluation Stack

- manual sample inspection
- held-out validation set
- format compliance checks

## Inference Stack

- local `transformers` generation for debugging
- `vLLM` for later serving

## Selection Rationale

1. Qwen2.5 官方模型卡提供了标准 `apply_chat_template` 用法
2. 官方文档也给出了 vLLM 和 SGLang 推理示例
3. 3B 规模对第一个项目来说足够小，适合先跑通闭环
4. 如果资源紧张，可以回退到 1.5B 版本
