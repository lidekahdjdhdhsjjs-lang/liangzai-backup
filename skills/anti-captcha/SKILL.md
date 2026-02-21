# Anti-CAPTCHA Skill

绕过机器人检测和人机验证的完整方案

## 概述

使用 `undetected-chromedriver` 库自动绕过反机器人检测系统

## 安装

```bash
pip install undetected-chromedriver selenium
```

## 基础用法

```python
import undetected_chromedriver as uc

# 创建反检测浏览器
driver = uc.Chrome(headless=True, use_subprocess=False)
driver.get('https://example.com')
print(driver.page_source)
driver.quit()
```

## 高级用法

### 1. 保持浏览器登录状态

```python
import undetected_chromedriver as uc

options = uc.ChromeOptions()
options.add_argument('--disable-blink-features=AutomationControlled')
options.user_data_dir = './my_browser_profile'  # 保存登录状态

driver = uc.Chrome(options=options, headless=True)
driver.get('https://twitter.com/home')
```

### 2. 模拟人类行为

```python
import time
import random

def human_delay():
    """随机延迟模拟人类"""
    time.sleep(random.uniform(0.5, 2.0))

def scroll_like_human(driver):
    """模拟人类滚动"""
    for _ in range(random.randint(3, 8)):
        driver.execute_script(f"window.scrollBy(0, {random.randint(100, 500)})")
        time.sleep(random.uniform(0.3, 1.0))
```

### 3. 绕过复杂检测

```python
import undetected_chromedriver as uc

# 禁用自动化标志
options = uc.ChromeOptions()
options.add_experimental_option("excludeSwitches", ["enable-automation"])
options.add_experimental_option('useAutomationExtension', False)

driver = uc.Chrome(options=options, headless=True)

# 执行反检测脚本
driver.execute_cdp_cmd("Page.addScriptToEvaluateOnNewDocument", {
    "source": """
        Object.defineProperty(navigator, 'webdriver', {
            get: () => undefined
        })
    """
})
```

## 常用检测网站

- https://nowsecure.nl - 检测浏览器指纹
- https://bot.sudoer.me - 检测自动化特征
- https://www.google.com/recaptcha/api2/demo - reCAPTCHA测试

## 完整示例: 自动注册账号

```python
import undetected_chromedriver as uc
import time
import random

def register_account(email, password):
    options = uc.ChromeOptions()
    options.add_argument('--disable-blink-features=AutomationControlled')
    options.user_data_dir = './temp_profile'
    
    driver = uc.Chrome(options=options, headless=True)
    
    # 打开注册页
    driver.get('https://example.com/register')
    time.sleep(random.uniform(1, 2))
    
    # 填写表单
    driver.find_element('name', 'email').send_keys(email)
    time.sleep(random.uniform(0.5, 1.5))
    driver.find_element('name', 'password').send_keys(password)
    time.sleep(random.uniform(0.5, 1.5))
    
    # 点击注册按钮
    driver.find_element('css selector', 'button[type="submit"]').click()
    
    time.sleep(2)
    driver.quit()

# 使用
register_account('test@example.com', 'password123')
```

## 注意事项

1. **IP问题**: 此库不隐藏IP，数据中心IP容易被检测
2. **登录状态**: 首次登录后保存profile可复用
3. **不要过快**: 添加随机延迟模拟人类行为
4. **仅供学习**: 遵守网站服务条款

## OpenClaw中集成

在OpenClaw中使用browser工具时:
- 优先复用已打开的标签页
- 添加随机延迟
- 避免连续自动化操作
