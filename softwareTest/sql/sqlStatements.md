# SQL 语句使用指南

## 1. SELECT 语句
`SELECT` 用于从数据库中查询数据  

**基本语法：**
```sql
SELECT column1, column2 
FROM table_name 
WHERE condition;
```
SELECT：指定要查询的列  
FROM：指定要查询的表  
WHERE：过滤条件，用于筛选符合条件的行  

## 2. INSERT 语句
用于向表中插入新数据  

**基本语法：**
```sql
INSERT INTO table_name (column1, column2) 
VALUES (value1, value2);
```
INSERT INTO：指定要插入数据的表  
VALUES：指定要插入的具体值  

## 3. UPDATE 语句
更新表中的数据  

**基本语法：**
```sql
UPDATE table_name 
SET column1 = value1, column2 = value2 
WHERE condition;
```
INSERT INTO：指定要插入数据的表  
VALUES：指定要插入的具体值  

## 4. DELETE 语句
用于删除表中的数据  

**基本语法：**
```sql
DELETE FROM table_name 
WHERE condition;
```
DELETE FROM：指定要删除数据的表  
WHERE：指定要删除的行  

## 5. JOIN 语句
用于从多个表中查询数据  
**基本语法：**
**内连接**
返回两个表中匹配的行  
```sql
SELECT a.column1, b.column2 
FROM table_a a 
INNER JOIN table_b b 
ON a.id = b.id;
```
INNER JOIN：只返回两个表中匹配的行  
ON：指定连接条件  
**左连接**
返回左表中的所有行，即使右表中没有匹配的行  
```sql
SELECT a.column1, b.column2 
FROM table_a a 
LEFT JOIN table_b b 
ON a.id = b.id;
```
LEFT JOIN：返回左表的所有行，右表没有匹配时返回 NULL  
**右连接**
返回右表中的所有行，即使左表中没有匹配的行
```sql
SELECT a.column1, b.column2 
FROM table_a a 
RIGHT JOIN table_b b 
ON a.id = b.id;
```
LEFT JOIN：返回左表的所有行，右表没有匹配时返回 NULL  

## 5. 子查询
在一个查询中嵌套另一个查询  

**基本语法：**
```sql
SELECT column1 
FROM table_a 
WHERE column2 IN (SELECT column2 FROM table_b WHERE condition);
```
子查询：先执行括号内的查询，然后将结果用于外部查询  

## 6. 聚合函数
用于对一组值进行计算并返回单个值    

**基本语法：**
```sql
SELECT COUNT(*) AS total_rows, 
       AVG(column1) AS average_value, 
       SUM(column2) AS total_sum 
FROM table_name;
```
COUNT：计算行数  
AVG：计算平均值  
SUM：计算总和  

## 7. 窗口函数
用于在查询结果中执行计算，同时保留原始行的详细信息    

**基本语法：**
```sql
SELECT column1, 
       ROW_NUMBER() OVER (ORDER BY column2) AS row_num 
FROM table_name;
```
ROW_NUMBER()：为每一行分配一个唯一的序号  
OVER：定义窗口的范围  

## 复杂查询
1. 查询每个部门的平均工资，并显示部门名称  
```sql
-- 使用 JOIN 和聚合函数
SELECT d.department_name, AVG(e.salary) AS avg_salary 
FROM employees e 
INNER JOIN departments d 
ON e.department_id = d.department_id 
GROUP BY d.department_name;
```
INNER JOIN：连接 employees 和 departments 表  
AVG(e.salary)：计算每个部门的平均工资  
GROUP BY：按部门名称分组

2. 查询工资高于平均工资的员工  
```sql
-- 使用子查询
SELECT employee_name, salary 
FROM employees 
WHERE salary > (SELECT AVG(salary) FROM employees);
```
子查询：先计算平均工资，然后筛选出工资高于平均值的员工  

3. 查询每个部门的员工工资排名
```sql
-- 使用子查询
-- 使用窗口函数
SELECT employee_name, department_id, salary, 
       RANK() OVER (PARTITION BY department_id ORDER BY salary DESC) AS salary_rank 
FROM employees;
```
RANK()：为每个部门的员工按工资排名  
PARTITION BY：按部门分组  
ORDER BY：按工资降序排列  

4. CET查询每个部门的最高工资员工
```sql
-- 使用 CTE
WITH max_salary_cte AS (
    SELECT department_id, MAX(salary) AS max_salary 
    FROM employees 
    GROUP BY department_id
)
SELECT e.employee_name, e.department_id, e.salary 
FROM employees e 
INNER JOIN max_salary_cte m 
ON e.department_id = m.department_id AND e.salary = m.max_salary;
```
WITH：定义 CTE，计算每个部门的最高工资  
INNER JOIN：连接 CTE 和 employees 表，找到最高工资员工  
