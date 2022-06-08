## 第一代日期类

1. Date								精确到毫秒，代表特定的瞬间
2. SimpleDateFormat			格式和解析日期的类
   
   SimpleDateFormat	格式化和解析日期的具体类。它允许进行格式化（日期-->文本），解析（文本-->日期）和规范化
3. 应用实例
   ```java
   Date d1 = new Date();//获取当前系统时间
   Date d2 = new Date(9234567);//通过指定毫秒数得到时间
   System.out.println(d1.getTime());//获取某个时间对应的毫秒数
   
   SimpleDateFormat sdf = new SimpleDateFormat("yyyy年MM月dd日 hh:mm:ss E");
   String format = sdf.format(d1);//format将日期转换成指定格式的字符串
   
   String s = "1996年01月01日 10:20:30 星期一";
   Date parse = sdf.parse(s);//把一个格式化的字符串转换成对应的Date
   //使用的sdf格式需要是正确的格式，否则会抛出格式转换异常
   ```