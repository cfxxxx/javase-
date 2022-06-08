## 基本介绍

Math类包含用于执行基本数学运算的方法，如初等指数，对数，平方根和三角函数

## Math类常见方法应用案例

1. abs			绝对值
2. pow			求幂
   ```java
   double pow = Math.pow(2, 4);//求2的4次幂
   ```
3. ceil			向上取整
4. floor		向下取整
5. round		四舍五入
6. sqrt			求开方
   ```java
   double sqrt = Math.sqrt(9.0);
   ```
7. random	求随机数
   ```java
   Math.random();//返回的是0 <= x < 1之间的的一个随机小数
   (int)(2 + Math.random() * 6);//返回的是2-5之间的随机整数
   ```
8. max			求两个数的最大值
9. min			求两个数的最小值
