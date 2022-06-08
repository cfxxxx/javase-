说起提高数据库性能，索引是最物美价廉的东西了，不用加内存，不用改程序，不用调sql，查询速度就可能提高百倍千倍

## 索引的原理

索引的代价

1. 磁盘占用
2. 对dml（update delete insert）语句的效率影响

## 索引的类型

1. 主键索引，主键自动的为主索引（类型 primary）
2. 唯一索引（unique）
3. 普通索引（index）
4. 全文索引（fulltext）使用MyISAM
   
   开发中考虑使用：全文搜索Solr和ElasticSearch

## 索引使用

1. 添加索引
   ```mysql
   create [unique] index index_name on table_name(col_name[(length)][asc|desc],...)
   
   alter table table_name add index [index_name](index_col_name,...)
   ```
2. 添加主键（索引）
   ```mysql
   alter table table_name add primary key(列名,...)
   ```
3. 删除索引
   ```mysql
   drop index index_name on table_name
   ```
4. 删除主键索引，比较特别
   ```mysql
   alter table table_name drop primary key
   ```
5. 查询索引
   ```mysql
   show index from table_name
   show indexes from table_name
   show keys from table_name
   ```

## 小结：哪些列上适合使用索引

1. 较频繁的作为查询条件字段应该创建索引
2. 唯一性太差的字段不适合单独创建索引，即使频繁作为查询条件
3. 更新非常频繁的字段不适合创建索引
4. 不会出现在where子句中字段不该创建索引
