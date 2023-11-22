---


title: gitignore 如何写
date: 2021-06-06 20:40:55
tags: [git]
type:

---


## 一、一个文件夹下的所有文件及文件夹都被忽略

```
...其他配置
folder_name
...其他配置
```


## 二、单独的文件

比如`~`开头的文件,打开Excel文件是会自动产生这么一个临时文件,使用如下表达式

```
所有~开头的文件
~*

指定某一特定文件夹
/folder_name/~*
```

---


## 参考

1. [选项 6：搜索"~"文件](https://docs.microsoft.com/zh-cn/office/troubleshoot/word/recover-lost-unsaved-corrupted-document#option-6-search-for--files)
2. [Description of how Word creates temporary files](https://support.microsoft.com/zh-cn/help/211632/description-of-how-word-creates-temporary-files)
