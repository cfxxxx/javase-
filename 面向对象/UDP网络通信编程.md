## 基本介绍

1. 类DatagramSocket和DatagramPacket实现了基于UDP协议网络程序
2. UDP数据报通过数据报套接字DatagramSocket发送和接受，系统不保证UDP数据报一定能够安全送到目的地，也不能确定什么时候可以抵达
3. DatagramPacket对象封装了UDP数据报，在数据报中包含了发送端的IP地址和端口号以及接收端的IP地址和端口号
4. UDP协议中每个数据报都给出了完整的地址信息，因此无需建立发送方和接收方的连接

## 基本流程

1. 核心的两个类/对象 DatagramSocket和DatagramPacket
2. 建立发送端，接收端（没有服务端和客户端概念）
3. 发送数据之前，建立数据包 DatagramPacket对象
4. 调用DatagramSocket的发送，接受方法
5. 关闭DatagramSocket
