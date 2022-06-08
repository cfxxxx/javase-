应用场景：

1. BigInteger适合保存比较大的整型
2. BigDecimal适合保存精度更高的浮点型

## BigInteger和BigDecimal常见方法

1. add				加
2. substrac		减
3. multiply		乘
4. divide			除

```java
//BigInteger
BigInteger bigInteger = new BigInteger("222222222222222222");
BigInteger bigInteger2 = new BigInteger("100");
BigInteger add = bigInteger.add(bigInteger2);

//BigDecimal
BigDecimal bigDecimal = new BigDecimal("2.1111111111111111111111");
BigDecimal bigDeciaml2 = new BigDecimal("1.11111111111111111111");
BigDecimal add = bigDecimal.add(bigDecimal2);

//注意：使用除法时，可能会抛出ArithmeticException除不尽异常
BigDecimal divide = bigDecimal.divide(bigDecimal2, BigDecimal.ROUND_CEILING);
//BigDecimal.ROUND_CEILING表示保留到分子的精度
```
