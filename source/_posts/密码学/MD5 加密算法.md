---
title: MD5 加密算法
date: 2021-03-12 22:37:41
tags: [MD5,算法,密码学]

---

## 一、有哪些分类？

- 大写、小写
- 32位、16位（16进制）
16位一般是将32位的截取的9-24位:str.substring(8, 24);


## 二、用CryptoJS如何实现？

- 32 up : CryptoJS.MD5(rawStr).toString().toUpperCase()
- 32 low: CryptoJS.MD5(rawStr).toString().toLowerCase()
- 16 up : CryptoJS.MD5(rawStr).toString().substring(8, 24).toUpperCase()
- 16 up : CryptoJS.MD5(rawStr).toString().substring(8, 24).toLowerCase()


## 三、MD5算法适用于大量明文的加密传输么？

不适用。


## 四、为什么？

1. MD5 加密出来的数据能在定程度上代表，你是你，但无法还原出你。
2. 加密后得到一个128位的结果值。


## 五、常用于？

1. 可用于用户验证、文件是否有修改等等。


## 参考

1. [cryptojs Md5加密 base64加密和解密_aku12138的博客-CSDN博客](https://blog.csdn.net/aku12138/article/details/112327887)
