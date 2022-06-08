## 基本介绍

在某些情况下，程序员可能有以下需求，就会使用到final：

1. 当不希望类被继承时，可以用final修饰
2. 当不希望父类的某个方法被子类覆盖/重写（override）时，可以用final关键字修饰
   
   访问修饰符 final 返回类型 方法名

   3.当不希望类的某个属性的值被修改，可以用final修饰

       public final double TAX_RATE = 0.08

   4.当不希望某个局部变量被修改，可以用final修饰

		final double TAX_RATE = 0.08

## final使用注意事项和细节讨论

1. final修饰的属性又叫常量，一般用XX_XX_XX来命名
2. final修饰的属性在定义时，必须赋初值，并且以后不能再修改，赋值可以在如下位置之一【选择一个位置赋初值即可】：
   1. 定义时：public final double TAX_RATE = 0.08;
   2. 在构造器中
   3. 在代码块中
3. 如果final修饰的属性是静态的，则初始化的位置只能是
   1. 定义时
   2. 在静态代码块，不能在构造器中赋值
4. final类不能继承，但可以实例化对象
5. 如果类不是final类，但是含有final方法，则该方法虽然不能重写，但是可以被继承
6. 一般来说，如果一个类已经是final类了，就没有必要再将方法修饰成final方法
7. final不能修饰构造方法（即构造器）
8. final和static往往搭配使用，效率更高，不会导致类加载，底层编译器做了优化处理
   ```java
   class Demo{
     public static final int i = 16;
     static{
       System.out.println("静态代码块");
     }
   }
   
   //在主方法中
   System.out.println(Demo.i);//此时并不会输出“静态代码块”，因为类没有加载
   ```

	9.包装类（Integer,Double,Float,Boolean都是final），String也是final类
