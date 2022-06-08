## System类常见方法和案例

1. exit							退出当前程序
   ```java
   System.exit(0);//0表示一个状态，正常的状态
   ```
2. arraycopy				复制数组元素，比较适合底层调用，一般使用Arrays.copyOf完成复制数组
   ```java
   int[] src = {1, 2, 3};
   int[] dest = new int[3];
   System.arraycopy(src, 0, dest, 0, 3);
   //src   表示原数组
   //0     表示从原数组的哪个索引开始拷贝
   //dest  目标数组，表示把原数组的数据拷贝到哪个数组
   //0     表示把原数组的数据拷贝到目标数组的哪个索引
   //3     表示从原数组拷贝多少个数据到目标数组
   ```
3. currentTimeMillens	返回当前时间距离1970-1-1的毫秒数
4. gc							运行垃圾回收机制
