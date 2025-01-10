# Selenium 浏览器操作

Selenium 提供了多种操作浏览器的方法，包括启动浏览器、退出浏览器、截屏、窗口设置最大化和最小化等操作。下面是这些常见操作的示例代码。

## 1. 浏览器启动、退出、截屏、窗口设置最大化、最小化 

使用 Selenium 启动浏览器的最常见方法是使用 WebDriver 对象来初始化浏览器驱动。

### 示例代码：

```python
from selenium import webdriver

# 启动Chrome浏览器
driver = webdriver.Chrome()

# 启动Firefox浏览器
# driver = webdriver.Firefox()

# 启动Edge浏览器
# driver = webdriver.Edge()

# 退出整个浏览器
driver.quit()

# 关闭当前窗口
driver.close()

# 将浏览器窗口最大化
driver.maximize_window()

# 截取当前页面的屏幕截图并保存为 PNG 文件
driver.get_screenshot_as_file("screenshot.png")

# 将浏览器窗口最大化
driver.maximize_window()

# 将浏览器窗口最小化
driver.minimize_window()
```

## 2. 页面跳转、前进、后退、刷新、获取URL、获取title

Selenium 提供了多种用于浏览器页面导航的操作，帮助测试脚本模拟用户在浏览器中的常见行为。以下是这些操作的示例代码。

```python
# 跳转到指定的 URL
driver.get("https://www.example.com")

# 向前导航到下一个页面
driver.forward()

# 返回到前一个页面
driver.back()

# 刷新当前页面
driver.refresh()

# 获取当前页面的 URL
current_url = driver.current_url
print(current_url)

# 获取当前页面的标题
page_title = driver.title
print(page_title)

```
## 3. 窗口切换、进入iframe、处理alert、操作cookie、执行js

```python
# 获取所有窗口句柄
windows = driver.window_handles

# 切换到第二个窗口
driver.switch_to.window(windows[1])

# 切换回第一个窗口
driver.switch_to.window(windows[0])

# 通过索引进入 iframe
driver.switch_to.frame(0)

# 通过名称或ID进入 iframe
driver.switch_to.frame("iframeName")

# 通过 WebElement 进入 iframe
iframe_element = driver.find_element_by_tag_name("iframe")
driver.switch_to.frame(iframe_element)

# 退出 iframe，返回主页面
driver.switch_to.default_content()

# 切换到 alert 弹窗
alert = driver.switch_to.alert()

# 接受 alert 弹窗
alert.accept()

# 拒绝 alert 弹窗（适用于 confirm 类型）
alert.dismiss()

# 获取 alert 弹窗的文本
alert_text = alert.text
print(alert_text)

# 输入文本到 prompt 弹窗（如果是 prompt 类型）
alert.send_keys("Test input")
alert.accept()

# 获取所有窗口句柄
windows = driver.window_handles

# 切换到第二个窗口
driver.switch_to.window(windows[1])

# 切换回第一个窗口
driver.switch_to.window(windows[0])

# 执行 JavaScript 代码
driver.execute_script("alert('Hello, world!');")

# 滚动到页面底部
driver.execute_script("window.scrollTo(0, document.body.scrollHeight);")

# 获取页面的标题
title = driver.execute_script("return document.title;")
print(title)

```
