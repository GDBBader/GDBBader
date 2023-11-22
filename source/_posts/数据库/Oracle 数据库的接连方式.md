---

title: Oracle 数据库的接连方式
date: 2023-03-29 21:10
tags: [Oracle,tns]

---

## 一、几种常用的接连方式
1. 通过sqlplus连接
2. 通过tns连接

<!-- more -->

## 二、通过sqlplus连接
```sql
C:\Users\Bader>sqlplus
请输入用户名:  c##bader/bader@localhost:1521/orcl
上次成功登录时间: 星期四 3月  30 2023 23:07:53 +08:00

连接到:
Oracle Database 19c Enterprise Edition Release 19.0.0.0.0 - Production
Version 19.3.0.0.0

SQL> select sysdate from dual;

SYSDATE
--------------
30-3月 -23

SQL>
```

## 三、通过tns接连
1. 查看tnsping命令查看tns文件所在位置
```cmd
C:\Users\Bader>tnsping abc

TNS Ping Utility for 64-bit Windows: Version 19.0.0.0.0 - Production on 30-3月 -2023 23:16:28

Copyright (c) 1997, 2019, Oracle.  All rights reserved.

已使用的参数文件:
D:\Users\Bader\WINDOWS.X64_193000_db_home\network\admin\sqlnet.ora

TNS-03505: 无法解析名称

C:\Users\Bader>
```
`D:\Users\Bader\WINDOWS.X64_193000_db_home\network\admin\`就是`tnsnames.ora`所在的文件夹
2. 编辑`tnsnames.ora`文件
```
ORCL =
  (DESCRIPTION =
    (ADDRESS = (PROTOCOL = TCP)(HOST = localhost)(PORT = 1521))
    (CONNECT_DATA =
      (SERVER = DEDICATED)
      (SERVICE_NAME = orcl)
    )
  )
```
有时会看到如下的配置：
```
ORCL =
  (DESCRIPTION =
    (ADDRESS = (PROTOCOL = TCP)(HOST = localhost)(PORT = 1521))
    (CONNECT_DATA =
      (SERVER = DEDICATED)
      (SID = orcl)
    )
  )

```
SERVICE_NAME：数据库名称
SID：数据库实例名称
3. 使用可视化工具链接

## 参考
1. [ORACLE中SID和SERVICE_NAME的区别-阿里云开发者社区 (aliyun.com)](https://developer.aliyun.com/article/454805)