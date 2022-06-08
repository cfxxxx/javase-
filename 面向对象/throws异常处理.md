## 基本介绍

1. 如果一个方法（中的语句执行时）可能生成某种异常，但是并不能确定如何处理这种异常，则此方法应显示的声明抛出异常，表明该方法不对这些异常进行处理，而由该方法的调用者负责处理
2. 在方法声明中用throws语句可以声明抛出异常的列表，throws后面的异常类型可以是方法中产生的异常类型，也可以是他的父类

```java
public void f1() throws FileNotFoundException,NullPointerException{
  FileInputStream fis = new FileInputStream("d://aa.txt");
}
```

## 注意事项和使用细节

1. 对于编译异常，程序中必须处理，比如try-catch或者throws
2. 对于运行时异常，程序中如果没有处理，默认就是throws的方式处理
3. 子类重写父类方法时，对抛出异常的规定：子类重写的方法，所抛出的异常类型要么和父类抛出的异常一致，要么为父类抛出异常的类型的子类型
   ```java
   class Father{
     public void method() throws RuntimeException{
     }
   }
   
   class Son extends Father{
     public void method() throws ArithmeticException{
     }
   }
   ```
4. 在throws过程中，如果有方法try-catch，就相当于处理异常，就可以不必throws
   ```java
   public void f1() throws FileNotFoundException{
     FileInputStream fis = new FileInputStream("d://aa.txt");
   }
   
   public void f2(){
     try{
       f1();
     }catch(FileNotFoundException e){
       //处理异常
     }
   }
   ```
