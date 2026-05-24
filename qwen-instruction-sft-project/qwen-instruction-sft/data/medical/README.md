# Medical Data Workspace

## Purpose

用于保存 medical 分支的数据切分、抽样和转换结果。

## Suggested Layout

- `raw/`：原始下载或缓存
- `train/`：训练切片
- `valid/`：验证切片
- `test/`：测试切片

## Versions

- `medical-400`
- `medical-800`

## Rules

1. 与主通用指令集独立
2. 验证集和测试集固定
3. 先评测，再决定是否训练

