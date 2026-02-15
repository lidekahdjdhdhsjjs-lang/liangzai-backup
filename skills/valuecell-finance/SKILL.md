---
name: valuecell-finance
description: 多智能体金融分析平台 - 股票研究、新闻分析、投资建议。基于ValueCell架构设计。
metadata: {"openclaw":{"emoji":"📈","os":["linux","darwin","win32"]}}
triggers:
  - pattern: "股票|股价|股市|A股|港股|美股"
    description: "股票相关查询"
  - pattern: "分析|研究报告|投资建议"
    description: "金融分析"
  - pattern: "新闻|资讯|行情"
    description: "金融新闻"
auto_invoke: true
examples:
  - "分析一下苹果公司的股票"
  - "查询特斯拉最新新闻"
  - "给我A股投资建议"
  - "分析腾讯控股投资价值"
---

# ValueCell Finance - 多智能体金融分析

模仿ValueCell架构设计的多智能体金融分析技能。

## 功能

### 1. 股票研究 (Research Agent)
- 基本面分析
- 财务指标
- 市值、PE、PB分析

### 2. 新闻分析 (News Agent)
- 实时新闻抓取
- 情感分析
- 影响评估

### 3. 投资建议 (Grid Agent)
- 买入/卖出建议
- 风险评估
- 仓位管理

## 使用方法

### 基本查询
```bash
# 查询股票信息
echo "分析苹果公司(AAPL)" 

# 查询新闻
echo "查询特斯拉最新新闻"
```

### 集成QVeris
使用已安装的qveris技能获取实时金融数据。

## 依赖

- qveris (已安装)
- yfinance (Python库)

## 架构

参考ValueCell多智能体架构:
- ResearchAgent: 研究分析
- NewsAgent: 新闻抓取
- GridAgent: 投资决策
