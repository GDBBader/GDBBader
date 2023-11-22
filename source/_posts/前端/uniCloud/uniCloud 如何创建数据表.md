---

title: uniCloud 如何创建数据表
date: 2022-10-16 05:50
tags: [uni-app,uniCloud,JavaScript,JSON]

---

## 一、前言
如何在uniCloud数据库中创建一个数据表？

<!-- more -->

## 二、步骤
### 2.1 设计数据表（Schema）
1. 在HX在创建一个Schema
![](https://pic-1313582683.cos.ap-chongqing.myqcloud.com/2022/202210160622794.png)
2. 设计Schema
```json
{
	"bsonType": "object", // 固定节点
	"description": "表的描述",
	"required": [], // 必填字段
	"permission": { 
		"read": false, // 前端非admin的读取记录权限控制。默认值是false，即可以不写。可以简单的true/false，也可以写表达式
		"create": false, // 前端非admin的新增记录权限控制。默认值是false，即可以不写。可以简单的true/false，也可以写表达式 
		"update": false, // 前端非admin的更新记录权限控制。默认值是false，即可以不写。可以简单的true/false，也可以写表达式
		"delete": false, // 前端非admin的删除记录权限控制。默认值是false，即可以不写。可以简单的true/false，也可以写表达式
		"count": false // 前端非admin的求数权限控制。默认值是true，即可以不写。可以简单的true/false，也可以写表达式
	},
	"properties": { // 表的字段清单
		"_id": { // 字段名称，每个表都会带有_id字段
			"description": "ID，系统自动生成"
			// 这里还有很多字段属性可以设置
		}
	},
	"fieldRules":[
		// 字段之间的约束关系。比如字段开始时间小于字段结束时间。也可以只校验一个字段。支持表达式
	]
}
```
注意：schema文件命名时需要以`.schema.json`为后缀。
![](https://pic-1313582683.cos.ap-chongqing.myqcloud.com/2022/202210160628891.png)
### 2.2 通过Schema生成数据表
### 2.2.1 上传Schema
![](https://pic-1313582683.cos.ap-chongqing.myqcloud.com/2022/202210160629815.png)
### 2.2.2 完成
![](https://pic-1313582683.cos.ap-chongqing.myqcloud.com/2022/202210160631560.png)

## 参考
1. [DB Schema概述 | uni-app官网](https://uniapp.dcloud.net.cn/uniCloud/schema.html#schema-root)