## 基本介绍

1. Properties类继承自Hashtable类并且实现了Map接口，也是使用一种键值对的形式来保存数据
2. 它的使用特点和Hashtable类似
3. Properties还可以用于从xxx.properties文件中，加载数据到Properties类对象，并且进行读取和修改
4. Properties是专门用于读写配置文件的集合类
   
   配置文件的格式：
   
   键 = 值
5. 注意：键值对不需要有空格，值不需要用引号，默认类型是String

## Properties类常见方法

- load：加载配置文件的键值对到Properties对象
- list：将数据显示到指定设备（流对象）
- getProperty(key)：根据键获取值
- setProperty(ket, value)：设置键值对到Properties对象
- store：将Properties中的键值对存储到配置文件，在Idea中，保存信息到配置文件，如果含有中文，会存储为unicode码