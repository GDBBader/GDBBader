---


title: Oracle with as
date: 2021-08-18 09:01:31
tags: [Oracle,with as,sql]
type:

---


## 一、什么是with as?

创建临时表的一种方法。

## 二、创建临时表

1. 单个临时表

```sql
WITH dd AS (SELECT SYSDATE FROM DUAL)
SELECT *
  FROM dd;
```

2. 多个临时表

```sql
WITH
    s1 AS (SELECT 1 num FROM DUAL),
    s2 AS (SELECT 2 num FROM DUAL)
SELECT *
  FROM s1, s2
 WHERE s1.num < s2.num;
```


## 参考

1. [关于oracle with as用法 - Ruthless - 博客园](https://www.cnblogs.com/linjiqin/p/3152667.html)
