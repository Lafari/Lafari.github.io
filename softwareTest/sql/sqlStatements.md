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



