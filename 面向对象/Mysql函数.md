## 统计函数

### 合计/统计函数-count

Count 返回行的总数

```mysql
Select count(*)|count(列名) from tablename
[WHERE where_definition]
```

解释：count(*) 返回满足条件的记录的行数

```
      count(列) 统计满足条件的列有多少个，但是会排除为null的情况
```

### 合计函数-sum

```mysql
Select sum(列名) {,sum(列名)...} from tablename
[WHERE where_difinition]
```

注意：sum仅对数值起作用，否则会报错

```
      对多列求和，","号不能少
```

### 合计函数-avg

```mysql
Select avg(列名) {,avg(列名)...} from tablename
[WHERE where_difinition]
```

### 合计函数-max/min

max/min函数返回满足where条件的一列的最大/最小值

```mysql
Select max(列名) from tablename
[WHERE where_difinition]
```

### 分组统计

使用group by子句对列进行分组

```mysql
SELECT column1, column2, column3... FROM tablename
group by column
```

使用having子句对分组后的结果进行过滤

```mysql
SELECT column1, column2, column3...
FROM tablename
 group by column having ...
```

group by用于对查询的结果分组统计

having子句用于限制分组显示结果

***

## 字符串相关函数

|CHARSET(str)|返回字串字符集|
|--|--|
|CONCAT(string2 [, ...])|连接字串|
|INSTR(string,substring)|返回substring在string中出现的位置，没有则返回0|
|UCASE(string2)|转换成大写|
|LCASE(string2)|转换成小写|
|LEFT(string2,length)|从string2中的左边起取length个字符|
|LENGTH(string)|string长度【按照字节】|
|REPLACE(str,search_str,replace_str)|在str中用replace_str替换search_str|
|STRCMP(string1,string2)|逐字符比较两字串大小|
|SUBSTRING(str,position [, length])|从str的position开始【从1开始计算】，取length个字符|
|LTRIM(string2) RIRIM(string2) trim|去除前端空格或后端空格，或者左右两端空格|

***

## 数学函数

|ABS(sum)|绝对值|
|--|--|
|BIN(decimal_number)|十进制转二进制|
|CONV(number2,from_base,to_base)|进制转换|
|FLOOR(number2)|向下取整，得到比num2小的最大整数|
|FORMAT(number,decimal_places)|保留小数位数|
|HEX(DecimalNumber)|转16进制|
|LEAST(number,number2 [,...])|求最小值|
|MOD(numerator,denominator)|求余|
|RAND([seed])|随机数，其范围为0<=v<=1.0，如果seed不变，随机数也不变化|
|CEILING(number2)|向上取整，得到比num2大的最小整数|

## 时间日期相关函数

|CURRENT_TIME()|当前时间|
|--|--|
|CURRENT_TIMESTAMP()|当前时间戳|
|DATE(datetime)|返回datetime的日期部分|
|DATE_ADD(date2,INTERVAL d_value d_type)|在date2中加上日期或时间|
|DATE_SUB(date2,INTERVAL d_value d_type)|在date2上减去一个日期或时间|
|DATEDIFF(date1,date2)|两个日期差（结果是天）|
|TIMEDIFF(date1,date2)|两个时间差（多少小时多少分钟多少秒）|
|NOW()|当前时间|
|YEAR\|MONTH|DATE(datetime) FROM_UNIXTIME|
|CURRENT_DATE()|当前日期|
|YEAR\|MONTH|DAY|DATE(datetime)|只显示年月日|
|UNIX_TIMESTAMP()|从1970-1-1到现在的秒数|
|FROM_UNIXTIME()|将一个整型秒数转换成现在的时间|

### 细节说明：

1. DATE_ADD() 和 DATE_SUB() 中的 interval 后面可以是 year minute second day 等
2. DATEDIFF(date1, date2) 得到的是天数，而且是date1-date2的天数，因此可以取负数
3. 这是个函数的日期类型可以是date,datetime或者timestamp

## 加密和系统函数

|USER()|查询用登录mysql的用户，以及登录的ip|
|--|--|
|DATABASE()|查询当前使用的数据库名称|
|MDS(str)|为字符串算出一个 MD5 32位的字符串，（用户密码）加密|
|PASSWORD(str)|从原文密码str计算并返回密码字符串，常用于对mysql数据库的用户密码加密|

## 流程控制函数

|IF(expr1,expr2,expr3)|如果expr1为true,则返回expr2 否则返回expr3|
|--|--|
|IFNULL(expr1,expr2)|如果expr1不为NULL，则返回expr1，否则返回expr2|
|SELECT CASE WHEN expr1 THEN expr2 WHEN expr3 THEN expr4 ELSE expr5 END;|如果expr1为true，则返回expr2，否则判断expr3如果为true，则返回expr4，否则返回expr5|
