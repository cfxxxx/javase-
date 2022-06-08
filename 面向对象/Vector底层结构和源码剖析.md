## Vector的基本介绍

1. Vector类的定义说明
   ```java
   public class Vector<E> extends AbstractList<E> 
   implements List<E>, RandomAccess, Cloneable, Serializable
   ```
2. Vector底层也是一个对象数组，protected Object[] elementData;
3. Vector是线程同步的，即线程安全，Vector类的操作方法带有synchronized
   ```java
   public synchronized E get(int index){
     if(index >= elementCount){
       throw new ArrayIndexOutOfBoundsException(index);
     }
     return elementData(index);
   }
   ```
4. 在开发中，需要线程同步安全时，考虑使用Vector

## Vector底层结构和ArrayList的比较

||底层结构|版本|线程安全（同步） 效率|扩容倍数|
|--|--|--|--|--|
|ArrayList|可变数组|jdk1.2|不安全，效率高|如果是有参构造1.5倍，如果是无参，第一次10，从第二次开始按1.5倍扩容|
|Vector|可变数组|jdk1.0|安全，效率不高|如果是无参，默认10，满后就按2倍扩容，如果指定大小，则每次直接按2倍扩容|