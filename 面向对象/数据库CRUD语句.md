## Insert语句

```mysql
INSERT INTO table_name [(column [, column...])]
VALUES (value [, value...]);
```

### 细节说明

1. 插入的数据应与字段的数据类型相同
   
   比如把 'ABC' 添加到 int 类型会错误
2. 数据的长度应在列的规定范围内，
   
   比如不能将一个长度为80的字符串加入到长度为40的列中
3. 在 values 中列出的数据位置必须与被加入的列的排列位置相对应
4. 字符和日期型数据应包含在单引号中
5. 列可以插入空值【前提是该字段允许为空】, insert into table value(null)
6. insert into table_name (列名) values (),(),() 形式添加多条记录
7. 如果是给表中的所有字段添加数据，可以不写前面的字段名称
8. 默认值的使用，当不给某个字段值时，如果有默认值就会添加，否则报错
   
   如果某个字段没有指定not null，那么当添加数据时，没有给定值，则会默认给null
   
   如果希望指定某个列的默认值，可以在创建表时指定

## Update语句

```mysql
UPDATE table_name
      SET col_name1=expr1 [, col_name2=expr2 ...]
      [WHERE where_definition]
```

### 细节说明

1. UPDATE语法可以用新值更新原有表行中的格列
2. SET子句指示要修改哪些列和要给予哪些值
3. WHERE子句指定应更新哪些行，如没有WHERE子句，这更新所有的行
4. 如果需要修改多个字段，可以通过 set 字段1=值1, 字段2=值2...

## Delete语句

```mysql
DELETE FROM table_name
        [WHERE where_difinition]
```

### 细节说明

1. 如果不使用where子句，将删除表中所有数据
2. Delete语句不能删除某一列的值（可使用 update 设为 null 或者 ''）
3. 使用Delete语句仅删除记录，不删除表本身，如要删除表，使用 drop table 语句
   
   drop table 表名;

## Select语句

```mysql
SELECT [DISTINCT] *|{column1, column2, column3...}
FROM tablename;
```

### 注意事项

1. Select指定查询哪些列数据
2. column指定列名
3. *号代表查询所有列
4. From指定查询哪张表
5. DISTINCT可选，指显示结果时，是否去掉重复数据

### 使用表达式对查询的列进行运算

```mysql
SELECT *|{column1|expression, column2|expression,...}
FROM tablename;
```

### 在Select语句中可使用as语句

```mysql
SELECT column_name as 别名 from 表名
```

### 在Where子句中经常使用的运算符

|比较运算符|>  <  <=  >=  =  !=|大于，小于，大于（小于）等于，不等于|
|--|--|--|
||BETWEEN ... AND ...|显示在某一区间的值|
||IN(set)|显示在in列表中的值，例：in(100,200)|
||LIKE '张pattern' NOT LIKE ''|模糊查询|
||IS NULL|判断是否为空|
|逻辑运算符|and|多个条件同时成立|
||or|多个条件任一成立|
||not|不成立，例：where not(salary>100);|

### 使用order by子句排序查询结果

```mysql
SELECT column1, column2, column3...
FROM table;
order by column asc|desc, ....
```

1. Order by指定排序的列，排序的列既可以是表中的列名，也可以是select语句后指定的列名
2. Asc升序【默认】，Desc降序
3. ORDER BY子句应位于SELECT语句的结尾
