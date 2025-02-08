# MySQL 数据库断言封装

本文档记录了如何封装 MySQL 数据库的连接与断言逻辑，以便在接口自动化测试中验证数据库数据是否符合预期，从而提升测试代码的简洁性和可维护性。

---

## 1. 数据库连接封装

我们首先封装一个 `MySQLHelper` 类，用于管理 MySQL 数据库的连接、查询以及更新操作。该类基于 [pymysql](https://pypi.org/project/PyMySQL/) 库实现，并返回字典格式的查询结果，便于后续断言操作。

```python
import pymysql

class MySQLHelper:
    def __init__(self, host, user, password, database, port=3306):
        self.conn = pymysql.connect(
            host=host,
            user=user,
            password=password,
            database=database,
            port=port,
            cursorclass=pymysql.cursors.DictCursor  # 返回字典格式结果
        )
        self.cursor = self.conn.cursor()

    def fetch_one(self, sql, params=None):
        """执行查询并返回单条记录"""
        self.cursor.execute(sql, params)
        return self.cursor.fetchone()

    def fetch_all(self, sql, params=None):
        """执行查询并返回所有记录"""
        self.cursor.execute(sql, params)
        return self.cursor.fetchall()

    def execute(self, sql, params=None):
        """执行增删改操作"""
        self.cursor.execute(sql, params)
        self.conn.commit()

    def close(self):
        """关闭数据库连接"""
        self.cursor.close()
        self.conn.close()
