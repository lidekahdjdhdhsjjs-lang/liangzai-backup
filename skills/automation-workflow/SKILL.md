---
name: automation-workflow
description: 自动化工作流技能 - 基于GitHub热门自动化项目学习，支持定时任务、事件触发、工作流自动化
---

# Automation Workflow Skill

基于GitHub热门自动化项目的工作流技能。

## 功能

### 1. 定时任务自动化
- 定时执行指定任务
- 支持cron表达式
- 自动重试失败任务

### 2. 事件触发
- GitHub webhook集成
- 文件变化监听
- 时间触发

### 3. 工作流模板
- CI/CD流程
- 自动测试
- 自动部署

## 命令

### 创建定时任务
```
创建定时任务: 每天9点执行 学习脚本
```

### 列出自动化任务
```
查看自动化任务
```

### 执行工作流
```
执行工作流: deploy
```

## 示例

```bash
# 创建每日学习任务
创建定时任务: 每天9点执行 /scripts/learning.sh

# 创建工作流
创建工作流: 测试 -> 构建 -> 部署
```

## 已学习的自动化项目

- Mirror-Dungeon-Bot (⭐125) - 游戏挂机
- claude-cs (⭐80) - 客户支持自动化
- netascode (⭐62) - 网络自动化
- Office-Management-System (⭐44) - 办公自动化

## 集成

- Cron Jobs
- Webhooks
- GitHub Actions

