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
