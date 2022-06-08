## HashSet的全面说明

1. HashSet实现了Set接口
2. HashSet实际上是HashMap
   ```java
   public HashSet(){
     map = new HashMap();
   }
   ```
3. 可以存放null值，但是只能有一个null
4. HashSet不保证元素是有序的，取决于hash后，再确定索引的结果（即不保证存放元素的顺序和取出元素的顺序一致）
5. 不能有重复元素/对象

## HashSet底层机制说明

HashSet底层是HashMap，HashMap底层是数组+链表+红黑树

数组链表模拟

```java
public static void main(String[] args){
  Node[] table = new Node[16];//创建容量为16的数组链表
  
  Node john = new Node("john", null);
  table[2] = john;
  Node jack = new Node("jack", null);
  john.next = jack;//将jack挂载到john
  Node rose = new Node("rose", null);
  jack.next = rose;//将rose挂载到jack
  //于是我们在table数组索引为2的地方生成了一个链表
}

class Node{
  Object item;
  Node next;
  
  public Node(Object item, Node next){
    this.item = item;
    this.next = next;
  }
}
```

## HashSet扩容机制

1. HashSet底层是HashMap
2. 添加一个元素时，先得到hash值，会转成索引值
3. 找到存储数据表table，看这个索引位置是否已经存放的有元素
4. 如果没有直接加入
5. 如果有，调用equals比较，如果相同，就放弃添加，如果不相同，则添加到最后
6. 在Java8中，如果一条链表的元素个数超过TREEIFY_THRESHOLD（默认是8），并且table的大小 >= MIN_TREEIFY_CAPACITY（默认64），就会进行树化

## 源码解读

### HashSet扩容机制

1. HashSet底层是HashMap，第一次添加时，table数组扩容到16，临界值（threshold）是16*加载因子（loadFactor）是0.75 = 12
2. 如果table数组使用到了临界值12，就会扩容到16\*2 = 32，新的临界值就是32*0.75 = 24，依此类推
3. 在Java8中，如果一条链表的元素个数到达TREEIFY_THRESHOLD（默认是8），并且table的大小 >= MIN_TREEIFY_CAPACITY（默认64），就会进行树化（红黑树），否则仍然采用数组扩容机制
