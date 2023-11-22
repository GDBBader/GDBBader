---


title: Python 提取代码中的接口
date: 2021-05-23 23:49:11
tags: [效率,Python,脚本,Excel,pandas,正则表达式]
type:

---


## 一、引言

现有如下任务：将大量vue、nvue源文件中使用到的接口列示出来

## 二、解决方案

```python
# -*- coding: utf-8 -*-
"""
Created on Sun May 23 21:59:07 2021

@author: zps
"""

import os
import re
import pandas as pd


def getUrlList(path):
   # path = r"D:\pythonDemo\getUrlDemo\abc.vue"
   f = open(path,'r', encoding=('utf-8'))
   targetList = []
   lines = f.readlines()
   for i in lines:
       j = re.findall('url.*v{1}.*', i.replace('\"',"\'"))
       if len(j)>0:
           targetList = targetList + j
   print(targetList)
   return targetList

def getFilePath(targetDir):
   fileList = os.listdir(targetDir)
   global filePathList
   for i in fileList:
       fullPath = os.path.join(targetDir, i)
       if os.path.isdir(fullPath):
           getFilePath(fullPath)
       else:
           if re.match('.*[\.]n{0,1}vue',fullPath):
               filePathList.append(fullPath)
def writeExcel(targetDir,filePathList):
   global start
   URLSPATH = os.path.join(targetDir,"Urls.xlsx")  
   writer = pd.ExcelWriter(URLSPATH)
   for i in filePathList:
       urlList = getUrlList(i)
       for u in urlList:
           table_lines = [[i,u,u.split("\'")[1]]]
           table_lines = pd.DataFrame(table_lines)
           print(table_lines)
           table_lines.to_excel(writer,startrow=start+1,header=None,index=None)
           start = start + 1
   writer.save()
   writer.close()
   
   

targetDir = r"D:\pythonDemo"
filePathList = []
start = 0
getFilePath(targetDir)
writeExcel(targetDir,filePathList)
```


## 三、效果

![](https://gitee.com/qiebzps/pic/raw/master/img/20210523235449.png#alt=)


## 参考

1. [【数据分析入门】之：如何用Python代替Excel（1） - 知乎](https://zhuanlan.zhihu.com/p/36975054)
2. [python遍历目录下的所有文件和目录详细介绍_修炼之路-CSDN博客_python遍历目录下所有文件](https://blog.csdn.net/sinat_29957455/article/details/82778306)
3. [怎么创建python文件-Python学习网](https://www.py.cn/faq/python/13438.html)
4. [Python replace()方法 | 菜鸟教程](https://www.runoob.com/python/att-string-replace.html)
5. [Python 正则表达式 | 菜鸟教程](https://www.runoob.com/python/python-reg-expressions.html)
