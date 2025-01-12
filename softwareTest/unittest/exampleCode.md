
# unittest 示例代码

以下是一个简单的示例，展示了 `unittest` 的基本用法：

```python
import unittest

class TestMathOperations(unittest.TestCase):
    # 测试前的准备
    @classmethod
    def setUpClass(cls):
        print("Setup resources for the class")

    def setUp(self):
        self.num1 = 10
        self.num2 = 5

    # 测试加法
    def test_addition(self):
        result = self.num1 + self.num2
        self.assertEqual(result, 15)

    # 测试减法
    def test_subtraction(self):
        result = self.num1 - self.num2
        self.assertEqual(result, 5)

    # 测试除法
    def test_division(self):
        result = self.num1 / self.num2
        self.assertEqual(result, 2)

    # 测试后的清理
    def tearDown(self):
        self.num1 = 0
        self.num2 = 0

    @classmethod
    def tearDownClass(cls):
        print("Cleanup resources for the class")

if __name__ == "__main__":
    unittest.main()
```

运行后输出示例：
```plaintext
Setup resources for the class
.test_addition (TestMathOperations) ... ok
.test_subtraction (TestMathOperations) ... ok
.test_division (TestMathOperations) ... ok
Cleanup resources for the class

----------------------------------------------------------------------
Ran 3 tests in 0.002s

OK
```
