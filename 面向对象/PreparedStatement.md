## 基本介绍

```java
String sql = "select count(*) from admin where username=? and password=?";
```

1. PreparedStatement执行的SQL语句中的参数用问号（？）来表示，调用PreparedStatement对象的 setXxx() 方法来设置这些参数 .setXxx() 方法有两个参数，第一个参数是要设置的SQL语句中的参数的索引（从1开始），第二个是设置的SQL语句中的参数的值
2. 调用 executeQuery() ，返回 ResultSet 对象
3. 调用 executeUpdate() ：执行更新，包括增删改

## 预处理的好处

1. 不再使用+拼接sql语句，减少语法错误
2. 有效的解决了SQL注入问题
3. 大大减少了编译次数，效率较高