---


title: Python 爬虫爬取博客链接与标题（用以年轮导入）
date: 2021-05-29 00:11:15
tags: [Python,脚本,效率,博客,年轮,记忆]
type:

---


## 一、引言

博客发布完成以后，为了能经常性回顾涉及的知识点，借助年轮来做周期性查看。为提高效率，因此使用爬虫简化从博客到年轮的操作。

## 二、解决

```python
# -*- coding: utf-8 -*-
"""
Created on Sun May 30 23:42:23 2021

@author: zps
"""

import requests
from bs4 import BeautifulSoup

base_url = "https://qiebzps.gitee.io/archives/"

r = requests.get(base_url)
r.encoding = r.apparent_encoding
soup = BeautifulSoup(r.text,'lxml')
titleItems = soup.select(".archive-article-title")


f = open('d:/blogs.txt','w+')
for  i in titleItems:
    result = {
        "title" : i.getText(),
        "link" : i.get('href')
        }
    f.write(result['title']+'\t'+result['link']+'
')
f.close()
```


## 参考

1. [Python 文件I/O | 菜鸟教程](https://www.runoob.com/python/python-files-io.html)
