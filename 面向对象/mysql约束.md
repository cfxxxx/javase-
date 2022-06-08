## 基本介绍

约束用于确保数据库满足特定的商业规则

在mysql中，约束包括：not null，unique，primary key，foreign key和check五种

### primary key（主键）

```mysql
字段名 字段类型 primary key
```

用于唯一的标识表行的数据，当定义主键约束后，该列不能重复

主键使用细节讨论：

1. 主键不能重复且不能为null
2. 一张表最多只能有一个主键，但可以是复合主键
   ```mysql
   create table t
   (
   id int, 
   `name` varchar(32),
   email varchar(32),
   primary key(id, `name`) --这里就是复合主键：id和name不能同时相等
   );
   ```
3. 主键的指定方式有两种：
   1. 直接在字段名后指定：字段名 primary key
   2. 在表定义最后写：primary key（列名）
4. 使用desc 表名 可以看到主键的情况

### not null（非空）

如果在列上定义了not null，那么当插入数据时，必须为列提供数据

```mysql
字段名 字段类型 not null
```

### unique（唯一）

当定义了唯一约束后，该列值是不能重复的

```mysql
字段名 字段类型 unique
```

unique 细节：

1. 如果没有指定not null，则unique字段可以有多个null
2. 一张表可以有多个unique字段

### foreign key（外键）

用于定义主表和从表之间的关系：外键约束要定义在从表上，主表则必须具有主键约束或是unique约束，当定义外键约束后，要求外键列数据必须在主表的主键列存在或是为null

```mysql
foreign key(本表字段名) references 主表名(主键名或unique字段名)
```

细节说明：

1. 外键指向的表的字段，要求是primary key或者是unique
2. 表的类型是innodb，这样的表才支持外键
3. 外键字段的类型要和主键字段的类型一致（长度可以不同）
4. 外键字段的值，必须在主键字段中出现过，或者为null【前提是外键字段允许为null】
5. 一旦建立主外键的关系，数据不能随意删除了

### check

用于强制行数据必须满足的条件，假定在sal列上定义了check约束，并要求sal列值在1000~2000之间，如果不在1000~2000之间就会提示出错

```mysql
列名 类型 check(check条件)
```
