# SQL 规范

## 代码风格:

- SQL代码中应用到的所有关键字、保留字均使用大写，例如SELECT、FROM、WHERE、AND、OR、UNION、INSERT、DELETE、GROUP、HAVING和COUNT等。

- SQL代码中应用到的除关键字、保留字之外的代码，库名、表名、字段名均使用小写，下划线风格，不超过32个字符，必须见名知意，禁止拼音英文混用。表名使用单数名词。举例:
```sql
表名: student teacher 
字段名: name exam_date
```
- 主键索引名为:pk_字段名,唯一索引名为:uk_字段,普通索引名则为:idx_字段名。

- 4个空格为1个缩进量，所有的缩进均为1个缩进量的整数倍，按照代码层次对齐。

- 字符串使用单引号。

- 灵活使用缩进和换行来增强可读性,多利用空白隔道与垂直间距:
    1. 同一SQL层级的关键字保持右对齐
    2. 换行让每句的逗号放在句末
    3. 一对括号应该尽量在同一垂直位置

```sql
SELECT 
    price.col1      AS col1,
    price.col2      AS col2,
    price.col3      AS col3,
    MAX(price.col4) AS col4,
FROM (
        SELECT id
        FROM student_score
        WHERE class_cd = 110
     )
WHERE sex = 'man'
    AND exam_dt = '2016-06-01'
GROUP BY
    col1,
    column2
```

## 基础规范: 
- 统一使用InnoDB存储引擎（MySQL 5.6之后为默认）

- 禁止使用select *操作，所有操作必须明确指定列名

- 使用UTF8字符集

- 禁止存储大文件,尽量不使用BLOB类型

- 表必须有主键且尽量选择较短的数据类型

- 禁止使用没有字段名的插入语句:`INSERT INTO table_name VALUES(xxx)`，必须显示指定插入的列属性

- 库名、表名、字段名禁止使用MySQL关键字/保留字 [MySQL关键字](https://dev.mysql.com/doc/refman/8.0/en/keywords.html)
