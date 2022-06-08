## Map接口实现类的特点

1. Map与Collection并列存在，用于保存具有映射关系的数据：Key-Value
2. Map中的key和value可以是任何引用类型的数据，会封装到HashMap$Node对象中
3. Map中的key不允许重复，原因和HashSet一样
4. Map中的value可以重复
5. Map的key可以为 null，value也可以为null，注意key为null，只能有一个，value为null，可以多个
6. 常用String类作为Map的key
7. key和value之间存在单向的一对一关系，即通过指定的key总能找到对应的value

## Map接口常用方法

1. put：添加
2. remove：根据键删除映射关系
3. get：根据键获取值
4. size：获取元素个数
5. isEmpty：判断个数是否为0
6. clear：清除
7. containsKey：查找键是否存在

## Map接口遍历方法

1. containsKey：查找键是否存在
2. keySet：获取所有的键
3. entrySet：获取所有的的关系
   ```java
   Set entrySet = map.entrySet();
   //1.增强for
   for(Object entry: entrySet){
     Map.Entry m = (Map.Entry) entry;
     m.getKey();
     m.getValue();
   }
   //2.迭代器
   Itreator iterator = entrySet.iterator();
   while(iterator.hasNext()){
     Object next = iterator.next();
     Map.Entry m = (Map.Entry) next;
     m.getKey();
     m.getValue();
   }
   ```
4. values：获取所有的值

## HashMap小结

1. Map接口的常用实现类：HashMap，Hashtable和Properties
2. HashMap是Map接口使用频率最高的实现类
3. HashMap是以key-val对的方式来存储数据
4. key不能重复，但是值可以重复，允许使用null键和null值
5. 如果添加相同的key，则会覆盖原来的key-val，等同于修改（key不会替换，val会替换）
6. 与HashSet一样，不会保证映射的顺序，因为底层是以hash表的方式来存储的
7. HashMap没有实现同步，因此线程是不安全的
