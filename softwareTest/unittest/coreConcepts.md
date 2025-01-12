
# unittest 的核心概念

## 1. Test Case（测试用例）
- 表示一个最小的测试单元。
- 每个测试用例是一个类，包含若干个以 `test_` 开头的方法。

## 2. Test Suite（测试套件）
- 一组测试用例的集合。
- 通过 `unittest.TestSuite` 创建测试套件，将多个测试用例组合在一起运行。

## 3. Test Runner（测试运行器）
- 负责运行测试并报告结果。
- 默认的运行器会输出控制台报告，还支持扩展为 HTML 或其他格式的报告。

## 4. Test Fixture（测试夹具）
- 用于在测试方法执行前准备环境，并在执行后清理环境。
- 常用方法包括：
  - `setUp` 和 `tearDown`：在每个测试方法前后运行。
  - `setUpClass` 和 `tearDownClass`：在测试类的开始和结束时运行。

## 5. Assertions（断言）
- 用于验证测试结果是否符合预期。
- 常用的断言方法包括：
  - `assertEqual(a, b)`：验证 `a == b`。
  - `assertNotEqual(a, b)`：验证 `a != b`。
  - `assertTrue(x)`：验证 `x` 为真。
  - `assertFalse(x)`：验证 `x` 为假。
  - `assertIs(a, b)`：验证 `a is b`。
  - `assertIsNot(a, b)`：验证 `a is not b`。
  - `assertIsNone(x)`：验证 `x is None`。
  - `assertIsNotNone(x)`：验证 `x is not None`。
  - `assertIn(a, b)`：验证 `a in b`。
  - `assertNotIn(a, b)`：验证 `a not in b`。
  - `assertGreater(a, b)`：验证 `a > b`。
  - `assertGreaterEqual(a, b)`：验证 `a >= b`。
  - `assertLess(a, b)`：验证 `a < b`。
  - `assertLessEqual(a, b)`：验证 `a <= b`。
  - `assertRaises(exception, callable, ...)`：验证抛出了指定异常
