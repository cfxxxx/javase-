## ArrayList的注意事项

1. permits all elements, including null, ArrayList可以加入null，并且多个
2. ArrayList是由数组来实现数据存储的
3. ArrayList基本等同于Vector，除了ArrayList是线程不安全（执行效率高）。在多线程情况下，不建议使用ArrayList

## ArrayList的底层操作机制源码分析

1. ArrayList中维护了一个Object类型的数组elementData
   ```java
   transient Object[] elementData;
   ```
2. 当创建对象时，如果使用的是无参构造器，则初始elementData容量为0（JDK7是10）
3. 当添加元素时：先判断是否需要扩容，如果需要扩容，则调用grow方法，否则直接添加元素到合适位置
4. 如果使用的是无参构造器，则初始elementData容量为0，第一次添加，则扩容elementData容量为10，如需要再次扩容，则扩容elementData为1.5倍
5. 如果使用的是指定容量capacity的构造器，如果需要扩容，则直接扩容elementData为1.5倍