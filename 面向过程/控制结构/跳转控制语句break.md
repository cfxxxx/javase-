## 注意事项和细节说明

1. break语句出现在多层嵌套的语句块中时，可以通过标签指明要终止的是哪一层语句块
2. 标签的基本使用
   1. break语句可以指定退出哪层
   2. label1是标签，由程序员指定
   3. break后指定到哪个label就退出到哪里
   4. 在实际的开发中，尽量不要使用标签
   5. 如果没有指定break，默认退出最近的循环体
   ```java
   label1:{......
   label2:     {......
   label3:           {......
                       break label2;
                      ......
   }}}
   ```