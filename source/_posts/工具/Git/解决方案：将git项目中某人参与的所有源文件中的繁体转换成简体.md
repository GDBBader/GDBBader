---


title: 解决方案：将git项目中某人参与的所有源文件中的繁体转换成简体
date: 2021-06-15 11:12:37
tags: [Python,效率,脚本,git]
type:

---


## 一、引言

git项目源码中有繁体有简体，现需要将某人所有参与过的源码文件全部排查并将其中的繁体修改为简体。

## 二、思路

1. 查找某人修改过的所有文件
2. 使用Python替换其中的繁体文字


## 三、查找某人修改过的所有文件

思路：从commit中可以找到所有某人修改过的文件，将其去重后即可得到某人修改过的所有源码文件

```shell
$ git log --name-only --oneline --author=908 --no-merges >> 908.txt
```

此命令将以一行显示不包含merge的commit作者为908的源码文件名。

之后，需要在Excel中去除重复文件（因同一文件，同一人可能有多次commit），并将其转换为xlsx格
式以便使用Python操作。


## 四、使用Python替换其中的繁体文字

```
# -*- coding: utf-8 -*-
"""
Created on 2021-06-05 14:52:38

@author: zps
"""

import langconv
from langconv import *
import pandas as pd

def Traditional2Simplified(sentence):
    '''
    将sentence中的繁体字转为简体字
    :param sentence: 待转换的句子
    :return: 将句子中繁体字转换为简体字之后的句子
    '''
    sentence = Converter('zh-hans').convert(sentence)
    return sentence


def handleIt(fileList):
    '''
    处理文件，覆盖原有文件
    '''
    for i in fileList:
        #f_path = i+"_"
        #f_ = open(f_path,"w")
    
        fileContent = ""
        
        
        try:
            with open(i, 'r',encoding='UTF-8') as f:
                for line in f.readlines():
                    fileContent = fileContent + Traditional2Simplified(line)
            #f_.write(fileContent)
            #f_.close()
            #f.save()
            f.close()
            
            f_ = open(i, 'w+',encoding='UTF-8')
            f_.write(fileContent)
            #f_.save()
            f_.close()
        except Exception:
            pass
        

def getFileList(excelPath):
    fileList = []
    excelData = pd.read_excel(excelPath,usecols=[0])
    #print(excelData)
    fileList = list(excelData['filepath'].values)
    #print(fileList)
    #for i in fileList:
    #    print(i)
    return fileList

if __name__=="__main__":
    #fileList = [
    #    r"C:\Users\zps\Desktop\繁体简体转换\disinfect-handle.vue",
    #    r"C:\Users\zps\Desktop\繁体简体转换\disinfect-list-from-scan.vue"
    #]
    
    #需要转换的文件地址 excel文件
    excelPath = r'C:\Users\zps\Desktop\繁体简体转换\base.xlsx'
    #从excel文件中提取所需要的文件地址列表
    fileList = getFileList(excelPath)
    # 处理文件
    handleIt(fileList)
```


## 参考

1. [Python 繁体中文与简体中文相互转换_博客堂-CSDN博客_python 繁体转简体](https://blog.csdn.net/u012052268/article/details/77823970)
2. [https://raw.githubusercontent.com/skydark/nstools/master/zhtools/langconv.py](https://raw.githubusercontent.com/skydark/nstools/master/zhtools/langconv.py)
3. [https://raw.githubusercontent.com/skydark/nstools/master/zhtools/zh_wiki.py](https://raw.githubusercontent.com/skydark/nstools/master/zhtools/zh_wiki.py)
