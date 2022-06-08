## 基本说明

1. DAO：data access object数据访问对象
2. 这样的通用类，称为BasicDao，是专门和数据库交互的，即完成对数据库（表）的crud操作
3. 在BasicDao的基础上，实现一张表，对应一个Dao，更好的完成功能，比如Customer表--Customer.java类（javabean）--CustomerDao.java

![screen-capture](9a1f661d179bc5157472291a03203f0e.png)

![screen-capture](9490d1718d72a70375c0d3acec555e8d.png)