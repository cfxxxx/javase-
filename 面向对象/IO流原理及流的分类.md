## Java IO流原理

1. I/O是Input/Output的缩写，I/O是非常实用的技术，用于处理数据传输。如读写文件，网络通讯等
2. Java程序中，对于数据的输入输出操作以“流（stream）”的方式进行
3. java.io包下提供了各种“流”类和接口，用以获取不同种类的数据，并通过方法输入或输出数据
4. 输入input：读取外部数据（磁盘，光盘等存储设备的数据）到程序（内存）中
5. 输出output：将程序（内存）数据输出到磁盘，光盘等存储设备中

## 流的分类

- 按操作数据单位不同分为：字节流（8 bit），字符流（按字符）
- 按数据流的流向不同分为：输入流，输出流
- 按流的角色的不同分为：节点流，处理流/包装流
  |抽象基类|字节流|字符流|
  |--|--|--|
  |输入流|InputStream|Reader|
  |输出流|OutputStream|Writer|
  1. Java的IO流共涉及40多个类，实际上非常规则，都是从如上4个抽象基类派生的
  2. 由这四个类派生出来的子类名称都是以其父类名作为子类名后缀

## IO流体系图-常用的类

- InputStream抽象类是所有类字节输入流的超类
  
  InputStream常用的子类
  - FileInputStream：文件输入流
  - BufferedInputStream：缓冲字节输入流
  - ObjectInputStream：对象字节输入流
- FileOutputStream
- FileReader和FileWriter介绍
  
  FileReader和Filewriter是字符流，即按照字符来操作IO
  
  **FileReader相关方法**
  1. new FileReader(File/String)
  2. read：每次读取单个字符，返回该字符，如果到文件末尾返回-1
  3. read(char[])：批量读取多个字符到数组，返回读取到的字符数，如果到文件末尾返回-1
     
     相关API：
     
     new String(char[])：将char[]转换成String
     
     new String(char[], off, len)：将char[]的指定部分转换成String
  
  **FileWriter相关方法**
  1. new FileWriter(File/String)：覆盖模式，相当于流的指针在首端
  2. new FileWriter(File/String, true)：追加模式，相当于流的指针在尾端
  3. writer(int)：写入单个字符
  4. writer(char[])：写入指定数组
  5. writer(char[], off, len)：写入指定数组的指定部分
  6. writer(String)：写入整个字符串
  7. writer(String, off, len)：写入字符串的指定部分
     
     相关API：
     
     String类：toCharArray将String转换成char[]
  
  注意：FileWriter使用后，必须关闭（close）或刷新（flush），否则写入不到指定的文件