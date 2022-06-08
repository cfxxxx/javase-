## Arrays类常见方法应用案例

Arrays里面包含了一系列静态方法，用于管理或操作数组（比如排序和搜索）

1. toString			返回数组的字符串形式
   ```java
   Arrays.toString(arr);
   ```
2. sort					排序（自然排序和定制排序）
   ```java
   Integer[] arr = {1, -1, 7, 0, 9};
   Arrays.sort(arr);//从小到大排序
   //调用定制排序时，传入两个参数
   //1.需要进行排序的数组arr
   //2.实现了Comparator接口的匿名内部类，要求实现compare方法
   Arrays.sort(arr, new Comparator() {
     @Override
     public int compare(Object o1, Object o2){
       Integer i1 = (Integer) o1;
       Integer i2 = (Integer) o2;
       return i2 - i1;//如果是i1 - i2，就是从小到大排序
     }
   })//实现了从大到小排序
   ```
3. binarySearch	通过二分搜索法进行查找，要求必须排好序
   ```java
   Integer[] arr = {1, 2, 90, 123, 567};
   int index = Arrays.binarySearch(arr, 1);//查找值为1的元素，返回元素下标
   //如果数组是无序的，不能使用binarySearch
   //如果不存在该元素，就返回-1
   ```
4. copyOf			数组元素的复制
   ```java
   Integer[] newArr = Arrays.copyOf(arr, arr.length);//拷贝arr数组中
   //前arr.length个元素，可自定义长度
   ```
5. fill					数组元素的填充
   ```java
   Integer[] num = new Integer[]{9, 3, 2};
   Arrays.fill(num, 99);//用99填充num数组，可以理解成是替换原来的元素
   ```
6. equals				比较两个数组元素内容是否完全一致
   ```java
   Integer[] arr = {1, 2, 90, 123, 567};
   Integer[] arr2 = {1, 2, 90, 123, 567};
   boolean equals = Arrays.equals(arr, arr2);//完全一样返回true，否则返回false
   ```
7. asList				将一组值，转换成list
   ```java
   List asList = Arrays.asList(2, 3, 4, 5, 6, 1);
   //返回的asList的编译类型是List（接口）
   //asList的运行类型是java.util.Arrays#ArrayList
   ```