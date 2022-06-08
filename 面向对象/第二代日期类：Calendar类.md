## 第二代日期类

1. 第二代日期类，主要就是Calendar类（日历）
   ```java
   public abstract class Calendar extends Object implements Serializable,Cloneable,Comparable<Calendar>
   //Calendar构造器是私有化的，需要通过getInstance()来获取实例
   ```
2. Calendar类是一个抽象类，他为特定瞬间与一组诸如YEAR，MONTH，DAY_OF_MONTH，HOUR等==日历字段==之间的转换提供了一些方法，并为操作日历字段（例如获得下星期的日期）提供了一些方法

```java
Calendar c = Calendar.getInstance();
c.get(Calender.YEAR);
c.get(Calendar.MONTH) + 1;//month字段要+1，因为Calendar把月份从0开始编号
```
