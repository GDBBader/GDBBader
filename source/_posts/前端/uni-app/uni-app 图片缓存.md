---


title: uni-app 图片缓存
date: 2021-08-31 16:57:11
tags: [uni-app,图片,缓存]
type:

---


## 一、uni-app 缓存

- uni-app 有专门的API来实现缓存
- 以键值对的方式来保存缓存
- 仅支持保存原生类型的数据

## 二、如何实现图片缓存？

如下为接口返回的数据:

```
{
	name:张三
	age:100
	photo:http://**.com/zhangsan.png
}
```

- 第一步:使用[uni-app的下载API](https://uniapp.dcloud.io/api/request/network-file?id=downloadfile)将图片下载下来
- 第二步:将下载至本地的地址替换photo的原值
- 第三步:使用[uni-app缓存API](https://uniapp.dcloud.io/api/storage/storage?id=setstorage)将接口返回的数据保存


## 参考

1. [uni.setStorage - uni-app官网](https://uniapp.dcloud.io/api/storage/storage?id=setstorage)
2. [上传、下载 - uni-app官网](https://uniapp.dcloud.io/api/request/network-file?id=downloadfile)
