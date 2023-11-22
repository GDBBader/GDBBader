---

title: Oracle 创建用户
date: 2022-07-14 22:58
tags: [Oracle,sql]

---
## 一、创建用户

创建一个名为C##MD的用户，密码是tiger.

```
create user C##MD identified by "tiger";
```

<!-- more -->

## 二、授权

现在虽然已经创建了用户，但是还无法登陆，需要授予create session权限后才能正常登录。

```
grant create session to C##MD;
```

## 问题

-   如何创建用户并使之能登陆。

## 参考

1.  [Oracle用户 - FreeIT教程](https://www.oraclejsq.com/article/010100133.html)