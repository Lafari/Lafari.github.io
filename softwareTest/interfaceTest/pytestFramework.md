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
**Jmeter和Postman：前置脚本和后置脚本**
```python
#每个用例之前和之后
def setup(self):
  print("用例请求之前：数据库链接")
def teardown(self):
  print("用例请求之后：数据库关闭")

#每个类之前和之后
def setup_class(self):
  print("类请求之前：数据库链接")
def teardown_class(self):
  print("类请求之后：数据库关闭")
```
# 3. 使用fixtrue固件结合contest.py文件实现前后置
**装饰器**
@pytest.fixtrue(scope="作用范围",autouse="自动执行",params=“参数化”,ids="参数别名",name="固件别名")  
scope:function 函数  
scope:class 类+自动执行  
scope:module 模块+自动执行  
scope:session 回话+自动执行  

**在一个文件中设置的固件fixtrue只能在当前文件起作用。如果希望对所有py文件起作用，那么需要结合conftest.py文件**
```python
@pytest.fixture(scope="session",autouse=False,params=[["baili","baili123"],
["beifan","beifan123"]],ids=["data1","data2"],name="sql")
def exe_sql(request):
  print("请求之前：查询数据库")
  yield request.param
  print("请求之后：关闭数据库")
```

# 4. 接口自动化测试框架封装之通过文件保持中间变量实现接口关联
**原因**
1. 类文件不能跨py使用
2. 统一管理中间变量
