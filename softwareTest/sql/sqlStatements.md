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


