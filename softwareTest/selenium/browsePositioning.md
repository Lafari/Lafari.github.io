# Selenium 定位

Selenium 提供了多种定位元素的方法。以下是八大常用的定位策略，每种方法的特点和示例代码

## 1. 常用的定位方式包括 ID、Name、Class Name、Tag Name、Link Text、Partial Link Text、CSS Selector 和 XPath

```python
# 通过元素的ID定位
element = driver.find_element_by_id("elementId")  # 通过ID查找元素

# 通过元素的Name属性定位
element = driver.find_element_by_name("elementName")  # 通过Name属性查找元素

# 通过元素的Class Name定位
element = driver.find_element_by_class_name("elementClassName")  # 通过Class Name查找元素

# 通过元素的Tag Name定位
element = driver.find_element_by_tag_name("tagName")  # 通过Tag Name查找元素

# 通过完整的链接文本定位
element = driver.find_element_by_link_text("Full Link Text")  # 通过完整链接文本查找元素

# 通过部分链接文本定位
element = driver.find_element_by_partial_link_text("Partial Link Text")  # 通过部分链接文本查找元素

# 通过CSS选择器定位
element = driver.find_element_by_css_selector(".className")  # 通过CSS选择器查找元素

# 通过XPath定位
element = driver.find_element_by_xpath("//tagName[@attribute='value']")  # 通过XPath表达式查找元素

```

## 2. CSS选择器、XPATH选择器、XPATH函数、XPATH相对定位、DevTool调试法

```python
# 使用CSS选择器通过类名定位元素
element = driver.find_element_by_css_selector(".className")  # 查找类名为className的元素

# 使用CSS选择器通过ID定位元素
element = driver.find_element_by_css_selector("#elementId")  # 查找ID为elementId的元素

# 使用CSS选择器通过属性定位元素
element = driver.find_element_by_css_selector("[name='elementName']")  # 查找name属性为elementName的元素

# 使用XPath选择器通过标签和属性定位
element = driver.find_element_by_xpath("//input[@name='username']")  # 查找name属性为username的input元素

# 使用XPath选择器通过层级路径定位
element = driver.find_element_by_xpath("/html/body/div/form/input")  # 通过层级路径查找input元素

# 使用XPath函数通过文本内容定位
element = driver.find_element_by_xpath("//button[text()='Submit']")  # 查找文本为Submit的按钮

# 使用XPath函数通过部分文本内容定位
element = driver.find_element_by_xpath("//a[contains(text(), 'Learn')]")  # 查找包含Learn文本的链接

# 使用XPath函数通过属性值进行匹配
element = driver.find_element_by_xpath("//input[starts-with(@name, 'user')]")  # 查找name属性以user开头的input元素

# 使用XPath相对定位查找子元素
element = driver.find_element_by_xpath("//div[@class='container']//button")  # 查找class为container的div内的button

# 使用XPath相对定位查找前一个或后一个兄弟元素
element = driver.find_element_by_xpath("//label[text()='Username']/following-sibling::input")  # 查找紧随Username标签后的input元素

// 测试CSS选择器
document.querySelector(".className");  // 查找class为className的元素

// 测试XPath选择器
document.evaluate("//button[text()='Submit']", document, null, XPathResult.FIRST_ORDERED_NODE_TYPE, null).singleNodeValue;  // 查找文本为Submit的按钮

```
