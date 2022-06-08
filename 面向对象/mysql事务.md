## 什么是事务

事务用于保证数据的一致性，他由一组相关的dml语句组成，该组的dml语句要么全部成功，要么全部失败，如：转账就要用事务来处理，用以保证数据的一致性

## 事务和锁

当执行事务操作时（dml语句），mysql会在表上加锁，防止其他用户改表的数据，这对用户来讲是非常重要的

## msql数据库控制台事务的几个重要操作

```mysql
start transaction   开始一个事务
savepoint           保存点名（设置保存点）
rollback to         保存点名（退回事务）
rollback            退回全部事务
commit              提交事务，所有的操作生效，不能回退
```

## 回退事务

在介绍回退事务前，先介绍一下保存点（savepoint）。保存点是事务中的点，用于取消部分事务，当结束事务时，会自动的删除该事务所定义的所有保存点

当执行回退事务时，通过指定保存点可以回退到指定的点

## 提交事务

使用commit语句可以提交事务，当执行了commit语句后，会确认事务的变化，结束事务，删除保存点，释放锁，数据生效。当使用commit语句结束事务后，其他会话【其他连接】将可以查看到事物变化后的新数据

## 事务细节讨论

1. 如果不开始事务，默认情况下，dml操作是自动提交的，不能回滚
2. 如果开始一个事务，你没有创建保存点，你可以执行rollback，默认就是回退到事务开始的状态
3. 可以在这个事务中（未提交的）创建多个保存点：比如savepoint aaa;执行dml;savepoint bbb;
4. 可以在事务没有提交前，选择会退到哪个保存点
5. mysql的事务机制需要innodb的存储引擎还可以使用，myISAM不好用
6. 开始一个事务start transaction或者set autocommit = off;

## mysql事务隔离级别

### 事务隔离级别介绍

1. 多个连接开启各自事务操作数据库中数据时，数据库系统要负责隔离操作，以保证各个连接在获取数据时的准确性
2. 如果不考虑隔离性，可能会引发如下问题：
   - 脏读
   - 不可重复读
   - 幻读

|MySQL隔离级别|脏读|不可重复读|幻读|加锁读|
|--|--|--|--|--|
|读未提交（read uncommitted）|✓|✓|✓|不加锁|
|读已提交（read committed）|×|✓|✓|不加锁|
|可重复读（repeatable read）|×|×|×|不加锁|
|可串行化（serializable）|×|×|×|加锁|

- 脏读（dirty read）：当一个事务读取另一个事务尚未提交的修改时，产生脏读
- 不可重复读（nonrepeatable read）：同一查询在同一事务中多次进行，由于其他提交事务所做的修改或删除，每次返回不同的结果集，此时发生不可重复读
- 幻读（phantom read）：同一查询在同一事务中多次进行，由于其他提交事务所做的插入操作，每次返回不同的结果集，此时发生幻读

### 查看当前会话隔离级别

```mysql
select @@tx_isolation;
```

### 查看系统当前隔离级别

```mysql
select @@flobal.tx_isolation;
```

### 设置当前会话隔离级别

```mysql
set session transaction isolation level repeatable read;
```

### 设置系统当前隔离级别

```mysql
set global transaction isolation level repeatable read;
```

mysql默认的事务隔离级别是repeatable read，一般情况下，没有特殊要求，没有必要修改（因为该级别可以满足绝大部分项目需求）

### 全局修改（修改my.ini配置文件）

[mysqld]

transaction-isolation = REPEATABLE-READ

## 事务的ACID特性

1. 原子性（Atomicity）
   
   原子性是指事务是一个不可分割的工作单位，事务中的操作要么都发生，要么都不发生
2. 一致性（Consistency）
   
   事务必须使数据库从一个一致性状态变换到另一个一致性状态
3. 隔离性（Isolation）
   
   事务的隔离性是多个用户并发访问数据库时，数据库为每一个用户开启的事务，不能被其他事务的操作数据所干扰，多个并发事务之间要相互隔离
4. 持久性（Durability）
   
   持久性是指一个事务一旦被提交，它对数据库中数据的改变就是永久性的，接下来即使数据库发生故障也不应该对其有任何影响
