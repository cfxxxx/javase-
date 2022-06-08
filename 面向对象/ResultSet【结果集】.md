## 基本介绍

1. 表示数据库结果集的数据表，通常通过执行查询数据库的语句生成
2. ResultSet对象保持一个光标指向其当前的数据行。最初，光标位于第一行之前
3. next方法将光标移动到下一行，并且由于在ResultSet对象中没有更多行时返回false，因此可以在while循环中使用循环来遍历结果集

```java
String sql = "select * from actor"
Statement statement = connection.createStatement();

ResultSet resultSet = statement.executeQuery(sql);

while (resultSet.next()) {
  int id = resultSet.getInt(1);
  String name = resultSet.getString(2);
  String sex = resulteSet.getString(3);
  Date date = resultSet.getDate(4);
  
  System.out.println(id + "\t" + name + "\t" + sex + "\t" + date);
}

resultSet.close();
statement.close();
connection.close();
```
