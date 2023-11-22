---


title: Pyhton 自动爬取并筛选年轮中没有的博客
date: 2021-05-31 23:32:47
tags: [Python,年轮,效率,记忆,脚本,博客,爬虫,正则表达式]
type:

---


## 一、引言

需要通过年轮增强记忆。需要记忆的材料在博客中。因此：

1. 从年轮中导出现有卡片
2. 爬取现有博客文章
3. 筛选出年轮中没有的博客
4. 输出成可以导入年轮的格式
5. 导出年轮

## 二、开搞


### 2.1 从年轮中导出现有卡片

![](https://gitee.com/qiebzps/pic/raw/master/img/20210531234112.jpg#alt=)
导出文件如下，可以看出，文件名就是年轮卡片名：
![](https://gitee.com/qiebzps/pic/raw/master/img/20210531234254.png#alt=)


### 2.2 爬取现有博客文章

[Python 爬虫爬取博客链接与标题（用以年轮导入） | 勿贪多 勿嫌少](https://qiebzps.gitee.io/2021/05/29/Python%20%E7%88%AC%E8%99%AB%E7%88%AC%E5%8F%96%E5%8D%9A%E5%AE%A2%E9%93%BE%E6%8E%A5%E4%B8%8E%E6%A0%87%E9%A2%98%EF%BC%88%E7%94%A8%E4%BB%A5%E5%B9%B4%E8%BD%AE%E5%AF%BC%E5%85%A5%EF%BC%89/)


### 2.3 筛选出年轮中没有的博客


#### 2.3.1 读取年轮卡片列表

改造[Python 提取代码中的接口 | 勿贪多 勿嫌少](https://qiebzps.gitee.io/2021/05/23/Python%20%E6%8F%90%E5%8F%96%E4%BB%A3%E7%A0%81%E4%B8%AD%E7%9A%84%E6%8E%A5%E5%8F%A3/)中的getFilePath方法

```python
# -*- coding: utf-8 -*-
"""
Created on Mon May 31 23:48:50 2021

@author: zps
"""

import os 
import re
def getFilePath(targetDir):
    fileList = os.listdir(targetDir)
    global filePathList
    for i in fileList:
        if os.path.isdir(i):
            getFilePath(i)
        else:
            if re.match('.*[\.]txt',i):
                filePathList.append(i.split(".")[0])
def main():
    getFilePath(targetDir)
    print(filePathList)

if __name__ == '__main__':
    filePathList = [] # 保存年轮卡片标题列表
    targetDir = r"C:\targetDir"

    main()
```


#### 2.3.2 读取博客页面Url列表

```python
def getUrlList(base_url,pages):
    for i in range(pages):
        if i == 0:
            u = base_url
        else:
            u = base_url+"page/"+str(i+1)
        blogUrlList.append(u)
```


#### 2.3.3 获取当前页所有博客列表

```python
def getBlogTitle(base_url):
    r = requests.get(base_url)
    r.encoding = r.apparent_encoding
    soup = BeautifulSoup(r.text,'lxml')
    titleItems = soup.select(".archive-article-title")
    for i in titleItems:
        result = {
            "title" : i.getText(),
            "link" : base_url.replace("archives","").replace("page/","") + i.get('href')
        }
        blogTitleList.append(result)
```


#### 2.3.4 筛选输出到Excel

```python
def out2Excel(blogUrlList,getBlogTitle):
    #Excel输出
    writer = pd.ExcelWriter('d:/blogs.xlsx')
    pdList = []
    
    # 获取博客标题、链接列表
    for i in blogUrlList:
        getBlogTitle(i)
    
    for i in blogTitleList:
        if i['title'] not in filePathList:
            print(i)
            t = i['title']
            l = i['link']
            mdlink = '[' + str(t) + ']' + '(' + l + ')'
            pdList.append([t,mdlink])
    pdList = pd.DataFrame(pdList)
    pdList.to_excel(writer,header=['标题','博客'],index=None)
    writer.save()

    print(pdList)
```


## 三、完整代码

```python
# -*- coding: utf-8 -*-
"""
Created on Mon May 31 23:48:50 2021

@author: zps
"""

import os 
import re

import requests
from bs4 import BeautifulSoup

import pandas as pd

def getFilePath(targetDir):
    fileList = os.listdir(targetDir)
    global filePathList
    for i in fileList:
        if os.path.isdir(i):
            getFilePath(i)
        else:
            if re.match('.*[\.]txt',i):
                filePathList.append(i.split(".")[0])
def main():
    # 获取年轮卡片列表
    getFilePath(targetDir)
    # 获取博客地址列表
    getUrlList(blogUrl,10)
    
    
    out2Excel(blogUrlList,getBlogTitle)
    
    
def out2Excel(blogUrlList,getBlogTitle):
    #Excel输出
    writer = pd.ExcelWriter('d:/blogs.xlsx')
    pdList = []
    
    # 获取博客标题、链接列表
    for i in blogUrlList:
        getBlogTitle(i)
    
    for i in blogTitleList:
        if i['title'] not in filePathList:
            print(i)
            t = i['title']
            l = i['link']
            mdlink = '[' + str(t) + ']' + '(' + l + ')'
            pdList.append([t,mdlink])
    pdList = pd.DataFrame(pdList)
    pdList.to_excel(writer,header=['标题','博客'],index=None)
    writer.save()

    print(pdList)

def getBlogTitle(base_url):
    r = requests.get(base_url)
    r.encoding = r.apparent_encoding
    soup = BeautifulSoup(r.text,'lxml')
    titleItems = soup.select(".archive-article-title")
    for i in titleItems:
        result = {
            "title" : i.getText(),
            "link" : base_url.replace("archives","").replace("page/","") + i.get('href')
        }
        blogTitleList.append(result)
def getUrlList(base_url,pages):
    for i in range(pages):
        if i == 0:
            u = base_url
        else:
            u = base_url+"page/"+str(i+1)
        blogUrlList.append(u)
        
        
    


if __name__ == '__main__':
    filePathList = [] # 保存年轮卡片标题列表
    targetDir = r"C:\targetDir"
    
    blogUrl = "https://qiebzps.gitee.io/archives/"
    pages = 10 # 博客页数
    blogUrlList = [] # 保存博客url列表
    blogTitleList = [] # 保存博客列表
    
    
    main()
```


## 四、效果

![](https://gitee.com/qiebzps/pic/raw/master/img/20210601010944.png#alt=)


## 参考

1. [Python 爬虫爬取博客链接与标题（用以年轮导入） | 勿贪多 勿嫌少](https://qiebzps.gitee.io/2021/05/29/Python%20%E7%88%AC%E8%99%AB%E7%88%AC%E5%8F%96%E5%8D%9A%E5%AE%A2%E9%93%BE%E6%8E%A5%E4%B8%8E%E6%A0%87%E9%A2%98%EF%BC%88%E7%94%A8%E4%BB%A5%E5%B9%B4%E8%BD%AE%E5%AF%BC%E5%85%A5%EF%BC%89/)
2. [Python 提取代码中的接口 | 勿贪多 勿嫌少](https://qiebzps.gitee.io/2021/05/23/Python%20%E6%8F%90%E5%8F%96%E4%BB%A3%E7%A0%81%E4%B8%AD%E7%9A%84%E6%8E%A5%E5%8F%A3/)
3. [Python 从uni-app项目中pages.json文件中提取页面与标题并输出到Excel | 勿贪多 勿嫌少](https://qiebzps.gitee.io/2021/05/27/Python%20%E4%BB%8Euni-app%E9%A1%B9%E7%9B%AE%E4%B8%ADpages.json%E6%96%87%E4%BB%B6%E4%B8%AD%E6%8F%90%E5%8F%96%E9%A1%B5%E9%9D%A2%E4%B8%8E%E6%A0%87%E9%A2%98%E5%B9%B6%E8%BE%93%E5%87%BA%E5%88%B0Excel/)
