# 成功模式总结 (2026-02-22)

## 模型选择策略
- M2.1: 日常自动化任务 (self-heal, prevention, monitoring)
- M2.5: 复杂学习任务 (foundry-evolution, creative, discussion)

## 成功时间窗口
- 最佳时段: 08:00-22:00
- 避免时段: 23:00-08:00

## 常见失败原因
1. message send 缺少 target 参数
2. delivery mode 与 channel 不匹配

## 优化建议
1. 修复 snapshot-check 的 delivery 配置
2. 统一使用 M2.1 处理基础任务
3. 复杂任务使用 M2.5
