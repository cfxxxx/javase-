## equals方法

> == 和 equals 的对比

### == 是一个比较运算符

1. ==：既可以判断基本类型，又可以判断引用类型
2. ==：如果判断基本类型，判断的值是否相等
3. ==：如果判断引用类型，判断的是地址是否相等，即判定是不是同一个对象
4. equals：是Object类中的方法，只能判断引用类型
5. 默认判断的是地址是否相等，==子类中往往重写该方法，用于判断内容是否相等。比如Integer，String   （ctrl + b查看jdk源码）==

```java
Integer i1 = new Integer(1000);
Integer i2 = new Integer(1000);

System.out.println(i1 == i2);//false
System.out.println(i1.equals(i2));//true
```

***

## hashcode方法

1. 提高具有哈希结构的容器的效率
2. 两个引用，如果指向的是同一个对象，则哈希值肯定是一样的
3. 两个引用，如果指向的是不同对象，则哈希值是不一样的
4. 哈希值主要根据地址号来的，但不能将哈希值完全等价于地址

***

## toString方法

### 基本介绍

默认返回：全类名（包名 + 类名） + @ + 哈希值的十六进制，子类往往重写toString方法，用于返回对象的属性信息

```java
class Monster{
  private String name;
  private String job;
  private double sal;
  
  public Monster(String name, String job, double sal){
    this.name = name;
    this.job = job;
    this.sal = sal;
  }
  
  //使用alt + ins快捷键生成重写后的toString方法
  public String toString(){ //重写后一般是把对象的属性输出，当然也可以自己修改
    return "Monster{" + 
            "name='" + name + '\'' +
            ", job=" + job + '\'' +
            ", sal=" + sal +
            '}';
  }
}
```

当直接输出一个对象时，toString方法会被默认调用

```java
Monster monster = new Monster("小明", "打工", 15);

System.out.println(monster);//默认调用monster.toString
```

***

## finalize方法

1. 当对象被回收时，系统自动调用该对象的finalize方法，子类可以重写该方法，做一些释放资源的操作
2. 什么时候被回收：当某个对象没有任何引用时，则jvm就会认为这个对象是一个垃圾对象，就会使用垃圾回收机制来销毁该对象，在销毁对象前，会先调用finalize方法
3. 垃圾回收机制的调用，是由系统来决定，也可以通过System.gc()主动触发垃圾回收机制

```java
public class Test{
  public static void main(String[] args){
    Car c = new Car("大众");
    c = null;
    //这时car对象就是一个垃圾，垃圾回收器就会回收(销毁)对象，自动调用该对象的finalize方法
    System.gc();//主动调用垃圾回收器
  }
}

class Car{
  private String name;
  
  public Car(String name){
    this.name = name;
  }
  
  //通过ctr + ins快捷键自动生成重写finalize()方法
  protected void finalize() throws Throwable{
    //可以加上自己的业务逻辑，比如释放资源：数据库连接，或者打开文件
    super.finalize();
  }
}
```
