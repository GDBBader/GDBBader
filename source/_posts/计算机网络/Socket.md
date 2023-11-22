---

title: Socket
date: 2023-02-16 21:22
tags: [Socket]

---

## 一、什么是Socket
套接字
> 一个[[套接字]]就是网络上[[进程]]通信的一端，提供了[[应用层]]进程利用[[网络协议]]交换数据的机制。——[套接字_百度百科](https://baike.baidu.com/item/%E5%A5%97%E6%8E%A5%E5%AD%97/9637606)
![image.png](https://pic-1313582683.cos.ap-chongqing.myqcloud.com/2022/202302162130543.png)

Socket = IP + Port

## 二、如何进行网络通信
需要一对套接字，即一个Client Socket，一个Server Socket。

1. 服务端监听
2. 客户端请求
3. 连接确认

理解：
1. 我（张三）上班了。
2. 张三，在不在？
3. 我在。

## 参考
1. [套接字_百度百科](https://baike.baidu.com/item/%E5%A5%97%E6%8E%A5%E5%AD%97/9637606)