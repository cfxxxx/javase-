## Mysql用户

mysql中的用户，都存储在系统数据库mysql中user表中

其中user表的重要字段说明：

1. host：允许登录的“位置”，localhost表示该用户只允许本机登录，也可以指定ip地址，比如192.168.1.100
2. user：用户名
3. authentication_string：密码，是通过mysql的password（）函数加密之后的密码

## 创建用户

```mysql
create user '用户名' @'允许登录的位置' identified by '密码';
```

说明：创建用户，同时指定密码

## 删除用户

```mysql
drop user '用户名' @'允许登录的位置';
```

## 用户修改密码

修改自己的密码：

```mysql
set password = password('密码');
```

修改他人的密码（需要有修改用户密码的权限）：

```mysql
set password for '用户名'@'登陆位置' = password('密码');
```

## Mysql中的权限

## 给用户授权

### 基本语法

```mysql
grant 权限列表 on 库.对象名 to '用户名'@'登陆位置' 【identified by'密码'】
```

### 说明：

1. 权限列表，多个权限用逗号分开
   ```mysql
   grant select on ...
   grant select,delete,create on ...
   grant all[privileges] on ...//表示赋予该用户在该对象上的所有权限
   ```
2. 特别说明
   
   \*.*		代表本系统中的所有数据库的所有对象（表，视图，存储过程）
   
   库.*		表示某个数据库中的所有数据对象（表，视图，存储过程）
3. identified by可以省略，也可以写出
   1. 如果用户存在，就是修改该用户的密码
   2. 如果该用户不存在，就是创建该用户

## 回收用户授权

### 基本语法：

```mysql
revoke 权限列表 on 库.对象名 from '用户名'@'登陆位置';
```

## 权限生效指令

如果权限没有生效，可以执行下面命令

```mysql
flush privileges;
```

## 细节说明

1. 在创建用户的时候，如果不指定Host，则为%，%表示所有IP都有连接权限create user xxx;
2. 你也可以这样指定
   
   create user  'xxx'@'192.168.1.%'表示xxx用户在192.168.1.*的ip可以登录mysql
3. 在删除用户的时候，如果host不是%，需要明确指定'用户'@'host值'
