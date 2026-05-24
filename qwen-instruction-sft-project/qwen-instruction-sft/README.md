# Qwen Instruction SFT

## 目标

用 Qwen 跑通一条最小可用的指令微调流程，验证：

1. 数据格式
2. Chat template 对齐
3. LoRA 微调
4. 验证集评测
5. 输出风格和指令遵循的提升

## 项目范围

这是第一个小项目，先不做 RL，不做复杂 Agent，只做基础指令微调。

## 目录约定

- `docs/`：项目文档、方案、记录
- `data/`：原始数据、清洗数据、训练数据
- `src/`：代码
- `configs/`：训练配置
- `notebooks/`：训练与对比实验 notebook
- `runs/`：实验输出、日志、检查点

## 当前下一步

1. 定义数据 schema
2. 定义训练目标
3. 选定模型和技术栈
4. 搭建第一版训练流程
5. 在 notebook 里加入对比实验与结果图像输出
6. 增加 medical 独立 notebook 与消融实验
