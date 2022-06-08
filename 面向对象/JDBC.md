## 基本介绍

1. JDBC为访问不同的数据库提供了统一的接口，为使用者屏蔽了细节问题
2. Java程序员使用JDBC，可以连接任何提供了JDBC驱动程序的数据库系统，从而完成对数据库的各种操作

## JDBC程序编写步骤

1. 注册驱动--加载Driver类
2. 获取连接--得到Connection
3. 执行增删改查--发送SQL命令给mysql执行
4. 释放资源--关闭相关连接

## 获取数据库连接的5种方式

### 方式一

```java
//获取Driver类实现对象
Driver driver = new com.mysql.jdbc.Driver();

String url = "jdbc:mysql://localhost:3306/ckj_db01"

Properties info = new Properties();
info.set("user","root");
info.set("password","ckj");
Connection conn = driver.connect(url, info);
```

### 方式二

```java
//使用Class类实现动态加载
Class clazz = Class.forName("com.mysql.jdbc.Driver");
Driver driver = (Driver)clazz.newInstance();
```

### 方式三

```java
//使用DriverManager替换Driver
Class clazz = Class.forName("com.mysql.jdbc.Driver");
Driver driver = (Driver)clazz.newInstance();

String url = "jdbc:mysql://localhost:3306/ckj_db01"
String user = "root";
String password = "ckj";
 
DriverManager.registerDriver(driver);
Connection conn = DriverManager.getConnection(url, user, password);
```

### 方式四

```java
//使用Class.froName自动完成注册驱动
Class.forName("com.mysql.jdbc.Driver");

String url = "jdbc:mysql://localhost:3306/ckj_db01"
String user = "root";
String password = "ckj";

Connection conn = DriverManager.getConnection(url, user, password);
```

## 方式五

```java
//使用配置文件，连接数据库更灵活
1.
新建properties对象，加载properties文件中的信息
Connection connection = DriverManager.getConnection(url,user,password);

2.
user=root
password=ckj
url=jdbc:mysql:/localhost:3306/ckj_db01
driver=com.mysql.jdbc.Driver
```
