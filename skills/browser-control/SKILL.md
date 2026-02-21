# Browser Control Skill

全自动浏览器控制技能，基于 OpenClaw browser 工具。

## 功能

- 自动化网页操作
- 元素点击和输入
- 内容提取和快照
- 表单填写和提交
- 页面导航和滚动

## 工具

### browser_navigate
导航到指定 URL

**参数:**
- targetUrl: 目标网址

**示例:**
```
browser action=navigate targetUrl="https://www.baidu.com"
```

### browser_click
点击页面元素

**参数:**
- ref: 元素引用
- request: 点击请求

### browser_type
在输入框输入文本

**参数:**
- ref: 输入框引用
- text: 要输入的文本
- request: 类型请求

### browser_snapshot
获取页面快照（可交互）

**参数:**
- compact: 是否紧凑模式

**示例:**
```
browser action=snapshot compact=true
```

### browser_screenshot
截取屏幕截图

**参数:**
- fullPage: 是否截取全页

### browser_act
执行复杂操作序列

**参数:**
- request: 操作请求（包含多个步骤）

## 常用操作类型

- `click` - 点击
- `type` - 输入
- `press` - 按键
- `hover` - 悬停
- `select` - 选择
- `fill` - 填充表单

## 使用示例

```
用户: 打开百度搜索 AI
→ browser action=navigate targetUrl="https://www.baidu.com"
→ browser action=snapshot  # 获取页面快照
→ browser action=act request={"kind":"type","ref":"search-input","text":"AI"}
→ browser action=act request={"kind":"click","ref":"search-button"}

用户: 截取当前页面
→ browser action=screenshot fullPage=true
```

## 检查浏览器状态

```bash
# 启动浏览器
openclaw browser start

# 查看状态
openclaw status | grep -i browser
```

## 注意事项

- 部分网站需要登录
- 复杂操作可能需要等待页面加载
- 建议先 snapshot 查看页面结构
