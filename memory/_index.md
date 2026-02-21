# 🧠 记忆系统索引

## 功能状态
| 功能 | 状态 |
|------|------|
| 语义搜索 | ✅ 已启用 |
| 自动摘要 | ✅ 每日23:00执行 |
| 遗忘机制 | ✅ 90天保留/180天归档 |
| 结构化存储 | ✅ 分类目录 |
| 索引文件 | ✅ 本文件 |

## 目录结构
```
memory/
├── _index.md           # 本索引
├── MEMORY.md           # 长期记忆 (核心)
├── permanent.json      # 永久配置
├── search.json         # 搜索配置
├── daily/             # 每日记录
│   ├── summary-2026-02.md   # 月度摘要
│   └── evolution-*.md       # 进化记录
├── skills/            # 技能知识
├── system/            # 系统配置
└── projects/          # 项目记忆
```

## 语义搜索
- 配置文件: search.json
- 使用MiniMax Embedding
- 索引路径: memory/.index/

## 自动摘要 Cron
- 时间: 每天 23:00
- 输出: memory/daily/summary-YYYY-MM.md

## 遗忘机制
- 保留: 90天内记忆
- 归档: 180天以上记忆
- 永不删除: 核心配置
