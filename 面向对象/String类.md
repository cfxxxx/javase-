## String类的理解和创建对象

1. String对象用于保存字符串，也就是一组字符序列
2. 字符串常量对象使用双引号括起的字符序列
3. 字符串的字符使用Unicode字符编码，一个字符（不区分字母还是汉字）占两个字节
4. String类较常用的构造方法：
   ```java
   String s1 = new String();
   String s2 = new String(String original);
   String s3 = new String(char[] a);
   String s4 = new String(char[] a, int startIndex, int count);
   String s5 = new String(byte[] b);
   ```
5. String类实现了接口 Serializable 【String可以串行化：可以在网络传输】，接口 Comparable 【String对象可以比较大小】
6. String 是final 类，不能被其它类继承
7. String 有属性 private final char value[ ]; 用于存放字符串的内容
8. value 是一个final 类型，不可以修改：即value不能指向新的地址，但单个字符内容可以变化

## 两种创建String对象的区别

方式一：直接赋值 String s = "hsp";

先从常量池查看是否有"hsp"数据空间，如果有，直接指向；如果没有则重新创建，然后指向，s最终指向的是常量池的空间地址

方式二：调用构造器 String s2 = new String("hsp");

先在堆中创建空间，==里面维护了value属性，指向常量池的hsp空间==，如果常量池没有"hsp"，重新创建，如果有，直接通过vlaue指向，最终指向的是堆中的空间地址

```java
String a = "hsp";
String b = new String("hsp");

System.out.println(a == b.intern());//true
System.out.println(b == b.intern());//false
```

知识点：当调用intern方法时，如果池已经包含一个等于此String对象的字符串（用equals(Object)方法确定)，则返回池中的字符串，否则，将此String对象添加到池中，并返回此String对象的引用

即b.intern()方法最终返回的是常量池的地址

## String的特性

1. String是一个final类，代表不可变的字符序列
2. 字符串是不可变的，一个字符串对象一旦被分配，其内容是不可变的

```java
String a = "hello";//创建对象a
String b = "abc";//创建对象b
//1.先创建一个StringBuilder对象sb
//2.sb.append("hello")
//3.sb.append("abc")
//4.String c = sb.toString()
//以下是toString方法源码
//public String toString(){
//  return new String(value, 0, count);即在这里返回一个新的String对象
//}
//所以最后其实c是指向堆中的对象(String)的value[]属性,value[]指向常量池中的"helloabc"
String c = a + b;

String d = "helloabc";
System.out.println(c == d);//false
//String c = "hello" + "abc"，常量相加，是在池中
//String c = a + b，变量相加，是在堆中
```

## String类的常见方法

String类是保存字符串常量的，每次更新都需要重新开辟空间，效率较低，因此java设计者还提供了StringBuilder和StringBuffer来增强String的功能，并提高效率

- equals			//区分大小写，判断内容是否相等
- equalslgnoreCase			//忽略大小写的判断内容是否相等
- length			//获取字符的个数，字符串的长度
- indexOf			//获取字符（或者字符子串）在字符串中第一次出现的索引，如果找不到返回-1
- lastIndexOf		//获取字符（或者字符子串）在字符串中最后一次出现的索引，找不到返回-1
- substring			//截取指定范围的字串
  ```java
  String name = "hello,张三";
  System.out.println(name.substring(6));//从索引6开始截取后面的所有内容
  System.out.println(name.substring(0, 5));//从索引0开始截取，截取到索引为5-1=4的位置
  System.out.println(name.sunstring(2, 5));//输出：llo
  ```
- trim					//去前后空格
- charAt				//获取某索引处的字符，注意不能使用Str[index]这种方式
- toUpperCase	//全部转换成大写
- toLowerCase	//全部转换成小写
- concat				//拼接字符串
  ```java
  String s1 = "宝玉";
  s1 = s1.concat("林黛玉").concat("薛宝钗").concat("together");
  ```
- replace			//替换字符串中的字符
  ```java
  s1 = "宝玉 and 薛宝钗 薛宝钗 薛宝钗";
  s1 = s1.replace("薛宝钗", "林黛玉");
  //将所有的“薛宝钗”替换成“林黛玉”
  ```
- split					//分割字符串，对于某些分割字符，我们需要转义，比如   |   \\\等
  ```java
  String poem = "锄禾日当午，汗滴禾下土，谁知盘中餐，粒粒皆辛苦";
  String[] split_poem = poem.split("，");//以"，"为分隔符分割，返回一个数组
  ```
- compareTo		//比较两个字符串的大小
- toCharArray		//转换成字符数组
  ```java
  s = "happy";
  char[] chs = s.toCharArray();
  ```
- format				//格式化字符串，%s字符串	%c字符		%d整型	%.2f浮点型（替换后保留两位小数，并且会进行四舍五入的处理）  
  ```java
  String name = "小明";
  int age = 18;
  double score = 100.0;
  String formatStr = "我的名字是%s,年龄是%d,成绩是%.2f";
  String info = String.format(formatStr, name, age, score);
  System.out.println(info);
  ```