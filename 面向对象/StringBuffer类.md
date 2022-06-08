## 基本介绍

- java.lang.StringBuffer代表可变的字符序列，可以对字符串的内容进行增删
- 很多方法与String相同，但StringBuffer是可变长度的
- StringBuffer是一个容器

## String VS StringBuffer

1. String保存的是字符串常量，里面的值不能更改，每次String类的更新实际上就是更改地址，效率较低//private final char value[]
2. StringBuffer保存的是字符串变量，里面的值可以更改，每次StringBuffer的更新实际上可以更新内容，不用每次更新地址，效率较高//char[] value（存放在堆中）

## StringBuffer的构造器

```java
StringBuffer();
  //构造一个其中不带字符的字符串缓冲区，其初始容量为16个字符
StringBuffer(CharSequence seq);
  //构造一个字符串缓冲区，它包含与指定CharSequence相同的字符
StringBuffer(int capacity);
  //构造一个不带字符，但具有指定初始容量的字符缓冲区，即对char[]大小进行指定
StringBuffer(String str);
  //构造一个字符串缓冲区，并将其内容初始化为指定的字符串内容
  //public StringBuffer(String str){
    super(str.length() + 16);//初始化char[]容量为str的长度+16
    append(str);//将str的内容添加到char[]
  }
```

## String和StringBuffer相互转换

String --> StringBuffer

```java
//方式一：使用构造器
String str = "hello";
StringBuffer stringbuffer = new StringBuffer(str);
//方式二：使用append方法
StringBuffer stringbuffer = new StringBuffer();
stringbuffer = stringbuffer.append(atr);
```

StringBuffer --> String

```java
StringBuffer stringbuffer = new StringBuffer("程柯嘉");
//方式一：使用toString()方法
String string = StringBuffer.toString();
//方式二：使用构造器
String string = new String(stringbuffer);
```

## StringBuffer类常见方法

1. 增 append
   ```java
   StringBuffer s = new StringBuffer();
   s.append("hello,").append("张三丰").append("赵敏").append(100).append(true);
   ```
2. 删 delete(start, end)
   ```java
   s.delete(11, 14);//删除索引11-14的字符，包含11不包含14
   ```
3. 改 replace(start, end, string) //将start-end间的内容替换掉，不含end
4. 查 indexOf //查找子串在字符串第一次出现的索引，如果找不到则返回-1
5. 插 insert
   ```java
   s.insert(9, "赵敏");//在索引为9的位置插入”赵敏“
   ```
6. 获取长度 length
