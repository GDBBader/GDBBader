---


title: uni-app的文件夹
date: 2021-04-10 22:53:05
tags: [uni-app,www,doc,downloads,documents,文件夹]
type:

---


# 引子：如何将开发时候放在`static`文件夹下的文件，在生成app后还能操作？

开发时候的传文件存在说`_www`下，此文件夹仅自身应用可读，所有不可以进行写操作。而`_doc`文件夹下的文件可且仅可自身应用可读写。

因此，把`_www`下的文件复制到`_doc`文件夹下来进行读写操作即可。


# 扩展

- `PRIVATE_WWW`: 应用私有资源目录常量
- `PRIVATE_DOC`: 应用私有文档目录常量
- `PUBLIC_DOCUMENTS`: 应用公共文档目录常量
- `PUBLIC_DOWNLOADS`: 应用公共下载目录常量

---


# 参考

1. [HTML5+ API Reference](https://www.html5plus.org/doc/zh_cn/io.html#plus.io.PRIVATE_WWW)
