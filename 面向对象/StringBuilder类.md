## 基本介绍

一个可变的字符序列，此类提供一个与StringBuffer兼容的API，但不保证同步，该类被设计用作StringBuffer的一个简易替换，用在字符串缓冲区被单个线程使用的时候。如果可能，建议优先采用该类，因为在大多数实现中，它比StringBuffer要快

在StringBuilder上的主要操作是append和insert方法，可重载这些方法，已接受任意类型的数据

## String，StringBuffer和StringBuilder的比较

1. StringBuilder和StringBuffer非常类似，均代表可变的字符序列，而且方法也一样
2. String：不可变字符序列，效率低，但复用率高
3. StringBuffer：可变字符序列，效率较高（增删），线程安全
4. StringBuilder：可变字符序列，效率最高，线程不安全
5. String使用注意事项说明：
   ```java
   String s = "a";//创建了一个字符串
   s += "b";//实际上原来的"a"字符串对象已经丢弃了，现在又产生了一个字符串s + "b"
   //(也就是"ab")，如果多次执行这些改变串内容的操作，会导致大量副本字符串对象存留
   //在内存中，降低效率。如果这样的操作放到循环中，会极大影响程序的性能
   //结论是：如果我们对String做大量修改，不要使用String
   ```

## 效率测试

### StringBuilder > StringBuffer > String

## 使用原则

1. 如果字符串存在大量的修改操作，一般使用StringBuffer或StringBuilder
2. 如果字符串存在大量的修改操作，并在单线程的情况，使用StringBuilder
3. 如果字符串存在大量的修改操作，并在多线程的情况，使用StringBuffer
4. 如果字符串很少修改，被多个对象引用，使用String，比如配置信息等
