## Collections工具类介绍

1. Collections是一个操作Set，List和Map等集合的工具类
2. Collections中提供了一系列静态的方法对集合元素进行排序，查询和修改等操作
   - 排序操作（均为static方法）
     1. reverse（List）：反转List中元素的顺序
     2. shuffle（List）：对List集合元素进行随机排序
     3. sort（List）：根据元素的自然顺序对指定List集合元素按升序排序
     4. sort（List，Comparator）：根据指定的Comparator产生的顺序对List集合元素进行排序
     5. swap（List，int，int）：将指定list集合中的i处元素和j出元素进行交换