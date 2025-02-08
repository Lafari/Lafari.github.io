# pytest+Python 接口自动化热加载技术封装说明文档

本文档详细说明如何在使用 `pytest` 进行接口自动化测试时，封装和使用热加载（Hot Reload）技术来提升开发效率。

---

## 1. 背景与需求

在接口自动化测试过程中，通常需要频繁修改测试代码、用例数据或配置。为加快开发和调试效率，希望代码发生变化时能够自动检测并重新执行测试，而无需每次手动重启测试，这就是所谓的**热加载**技术。

在 Python 生态中，`pytest` 作为流行的测试框架，本身并不直接提供热加载功能，但可以通过以下两种方式实现：

- **利用第三方插件**：例如 [pytest-watch](https://pypi.org/project/pytest-watch/)（简称 `ptw`），它可以监控项目文件变化并自动触发 `pytest` 测试运行。
- **自定义封装**：利用 Python 的文件监控库（如 `watchdog`）封装一套热加载模块，监听代码变更并自动调用 `pytest` 重新运行测试。

---

## 2. 利用 pytest-watch 插件

### 安装与使用

1. 安装 `pytest-watch`：
   ```bash
   pip install pytest-watch
