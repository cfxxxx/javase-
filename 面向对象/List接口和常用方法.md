## List接口基本介绍

List接口是Collection接口的子接口

1. List集合类中的元素有序（即添加顺序和取出顺序一致），且可重复
2. List集合类中的每个元素都有其对应的顺序索引，即支持索引
3. List容器中的元素都对应一个整数型的序号记载其在容器中的位置，可以根据序号存取容器中的元素
4. JDK API中List接口的常用实现类有：
   
   ArrayList，LinkedList和Vector

```java
List list = new ArrayList();
list.add("贾宝玉");
list.add("张三丰");

list.add(1, "hsp");//在索引为1的位置加入hsp，如果没有索引默认加在最后

List list2 = new ArrayList();
list2.add("jack");
list2.add("tom");

list.addAll(1, list2);//在索引为1的位置加入list2的元素
list.get(int index);//获取索引为index的元素
list.indexOf(Object ele)//返回元素ele第一次在集合中出现的位置
list.remove(int index);//移除指定index位置的元素
list.set(int index, Object ele);//将索引为index位置的元素替换为ele
list.subList(int fromIndex, int toIndex);//返回从fromIndex到toIndex位置的子集合
```

## List的三种遍历方式

1. 方式一：使用iterator
2. 方式二：使用增强for
3. 方式三：使用普通for
   ```java
   for(int i = 0; i < list.size(); i++){
     Object object = list.get(i);
   }
   ```

说明：使用LinkedList完成 使用方式和ArrayList一样
