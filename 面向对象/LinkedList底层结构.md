## LinkedList的全面说明

1. LinkedList实现了双向链表和双端队列的特点
2. 可以添加任意元素（元素可以重复），包括null
3. 线程不安全，没有实现同步

## LinkedList的底层操作机制

1. LinkedList底层维护了一个双向链表
2. LinkedList中维护了两个属性first和last分别指向首节点和尾节点
3. 每个节点（Node对象），里面又维护了prev，next，item三个属性，其中通过prev指向前一个，通过next指向后一个节点，最终实现双向链表
4. 所以LinkedList的元素的添加和删除，不是通过数组完成的，相对来说效率较高

## LinkedList底层结构

```java
LinkedList linkedlist = new  LinkedList();
//调用public LinkedList(){}无参构造器
//此时linkedlist的属性first = null，last = null
linkedlist.add(1);
/*执行添加
  public boolean add(E e){
    linkLast(e);
    return true;
  }
  将新的节点添加到双向链表的最后
  void linkedList(E e){
    final Node<E> l = last;
    final Node<E> newNode = new Node<>(l, e, null);//三个形参分别为prev, E, next
    last = newNode;
    if(l == null){
      first = newNode;
    }else{
      l.next = newNode;
    }
    size++;
    modCount++;
  }
```

## ArrayList和LinkedList的比较

||底层结构|增删的效率|改查的效率|
|--|--|--|--|
|ArrayList|可变数组|较低，数组扩容|较高|
|LinkedList|双向链表|较高，通过链表追加|较低|

### 如何选择ArrayList和LinkedList

1. 如果我们改查的操作多，选择ArrayList
2. 如果我们增删的操作多，选择LinkedList
3. 一般来说，在程序中，80%-90%都是查询，因此大部分情况下会选择ArrayList
4. 在一个项目中，根据业务灵活选择，也可能是这样，一个模块使用的是ArrayList，另一个模块是LinkedList
