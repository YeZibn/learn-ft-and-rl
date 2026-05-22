# Data Schema

## 目标

把指令微调数据统一成可直接用于 Qwen chat template 的消息格式。

## 推荐格式

```json
[
  {
    "id": "sample-0001",
    "messages": [
      {"role": "system", "content": "你是一个有帮助的助手。"},
      {"role": "user", "content": "请用一句话解释什么是机器学习。"},
      {"role": "assistant", "content": "机器学习是让计算机从数据中学习规律并完成任务的方法。"}
    ],
    "metadata": {
      "source": "manual",
      "task_type": "definition",
      "language": "zh"
    }
  }
]
```

## 字段说明

### `id`

样本唯一标识。

### `messages`

对话消息列表，至少包含：

1. `system` 可选
2. `user` 必需
3. `assistant` 必需

### `metadata`

用于记录数据来源和任务信息：

- `source`
- `task_type`
- `language`
- `difficulty`

## 约束

1. 所有训练样本必须经过统一清洗
2. messages 顺序必须稳定
3. assistant 内容必须是标准答案
4. 不混入未验证的长推理链
5. 训练集和验证集必须分离

## 任务类型建议

1. 定义解释
2. 简短问答
3. 格式遵循
4. 改写润色
5. 简单多轮对话

