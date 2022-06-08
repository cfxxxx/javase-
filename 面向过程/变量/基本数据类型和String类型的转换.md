# 基本类型转String类型

语法：将基本类型的值+""即可

```java
int n = 100;
String str = n + "";
```

# String类型转基本数据类型

语法：通过基本类型的包装类调用parseXX方法即可

```java
String str = "123";
int i = Integer.parseInt(str);
double d = Double.parseDouble(str);
boolean b = Boolean.parseBoolean("true");
char c = str.charAt(0);  //将str的第一个字符赋值给c
```

## 注意事项

1. 在将String类型转成基本数据类型时，要确保String类型能够转成有效的数据，比如我们可以把 "123" 转成一个整数，但是不能把 "hello" 转成一个整数
2. 如果格式不正确，就会抛出异常，程序就会终止
