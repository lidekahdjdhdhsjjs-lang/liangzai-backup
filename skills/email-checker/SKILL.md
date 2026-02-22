# Email Checker Skill

查看邮箱收到的邮件和验证码。

## 功能

- 登录邮箱 (支持多种邮箱)
- 查看收件箱邮件列表
- 读取最新邮件内容
- 提取验证码

## 工具

### email_login
登录邮箱并自动检查收件箱

**参数:**
- email: 邮箱地址
- password: 密码

### email_check_inbox
检查收件箱最新邮件

**示例:**
```
email_check_inbox
```

### email_get_verification_code
从邮件中提取验证码

**参数:**
- keyword: 邮件关键词 (如 "X", "Twitter", "GitHub")

## 使用方式

1. 先登录邮箱
2. 检查收件箱
3. 获取验证码

## 常用邮箱登录

### R-Mail (rurl.vip)
- URL: https://mail.rurl.vip/
- 用户名: mbou7
- 密码: 16Y57q3ZQg

### Gmail
- URL: https://mail.google.com

### Outlook
- URL: https://outlook.live.com

## 浏览器查看邮件

使用 OpenClaw browser 工具直接查看:

```bash
# 打开邮箱
browser action=open targetUrl="https://mail.rurl.vip/"

# 等待登录后查看收件箱
browser action=snapshot
```

## 示例对话

```
用户: 查看邮件
→ 使用 browser 打开邮箱登录页面
→ 手动登录或自动填写凭据
→ 查看收件箱快照

用户: 获取X验证码
→ 打开邮箱
→ 查看最新邮件
→ 从邮件内容提取验证码
```
