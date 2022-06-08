## 基本语法

1. switch关键词，表示switch分支
2. 表达式 对应一个值
3. case 常量1：当表达式的值等于常量1，就执行 语块1
4. break：表示退出switch
5. 如果和case常量1匹配，就执行语块1，如果没有匹配，就继续匹配case 常量2
6. 如果一个都没有匹配上，执行default

## switch细节

1. 表达式数据类型应和case后的常量类型一致，或者是可以自动转成可以相互比较的类型，比如输入的是字符，而常量是int
2. switch中表达式的返回值必须是：（byte，short，int，char，enum，String）
3. case子句中的值必须是常量，而不能是变量
4. default字句是可选的，当没有匹配的case时，执行default
5. break语句用来在执行完一个case分支后使程序跳出switch语句块；如果没有写break，程序会顺序执行到switch结尾，除非遇到break
