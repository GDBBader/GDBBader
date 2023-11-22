---

title: SQL 一个表的多个栏位匹配另一个表
date: 2022-10-21 23:03
tags: [SQL,SQL Server]

---
## 〇、问题
1. union如何使用？

## 一、前言
一个员工，有多个不同角色的主管，如何查询某一员工的某一角色的主管？
或者说，一个学生，不同学科的成绩，如何查询某一学生的某一学科的成绩？
![](https://pic-1313582683.cos.ap-chongqing.myqcloud.com/2022/202210212318914.png)

<!-- more -->

## 二、难点
1. 如何将数据转换成如下的形式
![](https://pic-1313582683.cos.ap-chongqing.myqcloud.com/2022/202210212320417.png)

## 三、步骤
### 3.1 数据转换
```sql
select 
	user_id,
	'chinese' type,
	chinese score
from user_score union
select 
	user_id,
	'math' type,
	math score
from user_score union
select 
	user_id,
	'english' type,
	english score
from user_score;
```

### 3.2 查询
```sql
select
	user_id,
	type,
	score
from (
	select 
		user_id,
		'chinese' type,
		chinese score
	from user_score union
	select 
		user_id,
		'math' type,
		math score
	from user_score union
	select 
		user_id,
		'english' type,
		english score
	from user_score
) user_score1
where
	user_score1.user_id = 'u1' and type = 'math';
```

## 参考
1. [UNION (Transact-SQL) - SQL Server | Microsoft Learn](https://learn.microsoft.com/zh-cn/sql/t-sql/language-elements/set-operators-union-transact-sql?view=sql-server-ver16)