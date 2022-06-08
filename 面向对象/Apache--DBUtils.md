## 基本介绍

1. commons-dbutils 是 Apache 组织提供的一个开源JDBC工具类库，他是对JDBC的封装，使用dbutils能极大简化jdbc编码的工作量

### DBUtils类

1. QueryRunner类：该类封装了SQL的执行，是线程安全的。可以实现增删改查，批处理
2. 使用QueryRunner类实现查询（queryRunner.query(connection, sql, ResultSetHandler, 可变参数...)）
3. ResultSetHandler接口：该接口用于处理 java.sql.ResultSet，将数据按要求转换为另一种形式
4. 实现dml操作
   
   queryRunner.update(connection, sql, 可变参数...) //返回受影响的行数int
   ```java
   ArrayHandler：把结果集中的第一行数据转成对象数组
   ArrayListHandler：把结果集中的每一行数据都转成一个数组，再存放到List中
   BeanHandler：将结果集中的第一行数据封装到一个对应的JavaBean实例中
   BeanListHandler：将结果集中的的每一行数据都封装到一个对应的JavaBean实例中，存放到List里
   ColumnListHandler：将结果集中某一列的数据存放到List中
   KeyedHandler(name)：将结果集中的每行数据都封装到Map里，再把这些map再存到一个map里，其key为指定的key
   MapHandler：将结果集中的第一行数据封装到一个Map里，key是列名，value就是对应的值
   MapListHandler：将结果集中的每一行数据都封装到一个Map里，然后再存放到List
   ScalarHandler：将单行单列的结果封装为一个Object对象
   ```