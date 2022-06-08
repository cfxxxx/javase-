## Collection接口实现类的特点

```java
public interface Collection<E> extends Iterable<E>
```

1. Collection实现子类可以存放多个元素，每个元素可以是Object
2. 有些Collection的实现类，可以存放重复的元素，有些不可以
3. 有些Collection的实现类，有些事有序的（List），有些不是有序（Set）
4. Collection接口没有直接的实现子类，是通过他的子接口Set和List来实现的

## 以实现子类ArrayList来演示

1. add：添加单个元素
2. remove：删除指定元素
3. contains：查找元素是否存在
4. size：获取元素个数
5. isEmpty：判断是否为空
6. clear：清空
7. addAll：添加多个元素
8. containsAll：查找多个元素是否都存在
9. removeAll：删除多个元素

## Collection接口遍历元素的方式1--使用Iterator迭代器

### 基本介绍

1. Iterator对象称为迭代器，主要用于遍历Collection集合中的元素
2. 所有实现了Collection接口的集合类都有一个iterator()方法，用以返回一个实现了Iterator接口的对象，即可以返回一个迭代器
3. Iterator仅用于遍历集合，Iterator本身并不存放对象

### 迭代器的执行原理

```java
Collection col = new ArrayList();
Iterator iterator = col.iterator();//得到一个集合的迭代器

//hasNext():判断是否还有下一个元素,返回boolean类型
while(iterator.hasNext()){
  //next():1.指针下移  2.将下移后集合位置上的元素返回
  Object obj = iterator.next();
  System.out.println(obj);
}//退出循环后，这时iterator迭代器指向最后一个元素
 //如果需要再次遍历，需要重置迭代器
iterator = col.iterator();

//使用itit快捷键快速生成while
//显示所有快捷键的快捷键ctrl + j
```

注意：在调用iterator.next()方法之前必须要调用iterator.hasNext()进行检测，若不调用，且下一条记录无效，直接调用iterator.next()会抛出NoSuchElementException异常

## Collection接口遍历元素的方式2--for循环增强

增强for循环，可以代替iterator迭代器，特点：增强for就是简化版的iterator，本质一样，只能用于遍历集合或数组

### 基本语法

```java
for(元素类型 元素名 : 集合名或数组名) {
  访问元素
}
//使用快捷键I快速生成for
```
