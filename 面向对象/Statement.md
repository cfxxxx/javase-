## 基本介绍

1. Statement对象 用于执行静态SQl语句并返回其生成的结果的对象
2. 在连接建立后，需要对数据库进行访问，执行命令或是SQL语句，可以通过
   - Statement【存在SQL注入问题】
   - PreparedStatement【预处理】
   - CallableStatement【存储过程】
3. Statement对象执行SQL语句，存在SQL注入风险
4. SQL注入是利用某些系统没有对用户输入的数据进行充分的检查，而在用户输入数据中注入非法的SQL语句段或命令，恶意攻击数据库
5. 要防范SQL注入，只要用PreparedStatement（从Statement扩展而来）取代Statement就可以了