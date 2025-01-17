# 1. 引入pytest用例管理框架
**作用**
1. 找到用例  
  - 模块名必须以test_开头或者_test结尾  
  - 类名必须以Test开头，并且不能有init方法  
  - 用例方法必须以test开头  
2. 执行用例
3. 判断结果
4. 生成报告  
**插件**
`pytest` 本身  
`pytest-html` 简单的html报告  
`pytest-xdist` 多线程执行  
`pytest-ordering` 控制用例的执行顺序  
`pytest-rerunfailures` 失败用例重跑  
`pytest-base-url` 设置基础路径（开发，测试，生产，预发布）  
`allure-pytest` 生成allure报告
**安装**
`pip install -r requirements.txt`
**运行**
1. 命令行
  - 在命令行输入pytest执行
  - 同时有很多参数可以使用
  - -v 输出更详细的信息
2. 主函数
```
import pytest
if __name__ == '__main__':
  pytest.main()
```
3. 结合pytest.ini全局配置文件执行。
``` python
[pytest]
#命令行参数
#常见：--html=./reports/report.html --reruns 2
addopts = -vs -m "user_manager or smoke"

#配置执行的用例位置
testpaths = ./testcases

#配置修改默认的模块规则
python_files = test_*.py

#配置修改默认的类规则
python_classes = Test*

#配置修改默认的用例规则
python_functions = test_*

#配置基础路径
base_url = http://www.baidu.com

#标记
markers =
  smoke: 冒烟测试用例
  product_manage: 商品管理
  user_manager: 用户管理
```
# 2. Pytest的前后置，固件，夹具
# 3. 使用fixtrue固件结合contest.py文件实现前后置
# 4. 接口自动化测试框架封装之通过文件保持中间变量实现接口关联
