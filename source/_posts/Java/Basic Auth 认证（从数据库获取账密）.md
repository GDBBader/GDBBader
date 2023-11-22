---
title: Basic Auth 认证（从数据库获取账密）
date: 2022-10-12 16:01:19
tags: [Basic Auth,Java,Spring Security]
---

## 一、前言
上一章已经实现了Basic Auth认证，但往往账密都是从数据库获取的。在这一章将学习如何与数据库交互。

<!-- more -->

## 二、前置学习
### 2.1 什么是UserDetailsService
在与数据库的交互中我们会看到如下代码：
```java
    @Override
    public void configure(AuthenticationManagerBuilder auth) throws Exception {
        // 使用自定义身份验证组件
        auth.userDetailsService(userDetailsService).passwordEncoder(passwordEncoder());
    }
```
意思就是“我要用自定义的userDetailsService实现类来处理是否认证通过”

在实现中，其内有一个名为loadUserByUsername()的方法，用来返回用户详情（这一步就是从数据查出来的。检查用户是否有效，是否被删除，是否存在，有这些异常就抛UsernameNotFoundException）。

## 2.2 passwordEncoder()
在这个方法中定义验证密码是否通过的方法。

## 参考
1. [Spring Security - Form Login with Database](https://www.tutorialspoint.com/spring_security/spring_security_form_login_with_database.htm)