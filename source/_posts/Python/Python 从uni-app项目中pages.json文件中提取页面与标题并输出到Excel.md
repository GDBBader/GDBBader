---


title: Python 从uni-app项目中pages.json文件中提取页面与标题并输出到Excel
date: 2021-05-27 00:03:04
tags: [Python,uni-app,json,Excel,脚本,效率,pandas]
type:

---


## 一、引言

最近在有需求需要将pages.json中的页面与标题的对应关系提取出来。其中包括分包，需要完整的页面地址。

## 二、解决方案

```python
# -*- coding: utf-8 -*-

import json
import pandas as pd

p = r"C:\Users\**\Desktop
ew 1.json"
excel_path = r"C:\Users\**\Desktop\pagesJson2Excel.xlsx"
with open(p,'r',encoding='utf-8') as load_f:
    load_dict = json.load(load_f)
    #获取分包中的页面地址与标题
    subList = []
    for i in load_dict["subPackages"]:
        sub_root = i["root"]
        sub_pages = i["pages"]
        for j in sub_pages:
            sub_path = "/"+sub_root +"/" +j["path"]
            sub_title = j["style"]["navigationBarTitleText"]
            subList = subList +[[sub_path,sub_title]]
    #print(subList)
    
    
    #获取主包中的页面地址与标题
    main_list = []
    for i in load_dict["pages"]:
        main_path = "/"+i["path"]
        main_title = i["style"]["navigationBarTitleText"]
        main_list = main_list + [[main_path,main_title]]
        #print(main_title)
    #print(main_list)
    
    #合并
    pages_list = main_list+subList
    #print(pages_list)
    
    #Excel输出
    writer = pd.ExcelWriter(excel_path)
    main_list = pd.DataFrame(main_list)
    main_list.to_excel(writer,header=['页面地址','标题'],index=None)
    writer.save()
```


## 三、效果

![](https://gitee.com/qiebzps/pic/raw/master/img/20210527000933.png#alt=)


## 参考

1. [【python】UnicodeDecodeError: 'gbk' codec can't decode byte 0xad in position...解决办法_HelenLee-CSDN博客](https://blog.csdn.net/weixin_43289135/article/details/104301294)
2. [pages.json - uni-app官网](https://uniapp.dcloud.io/collocation/pages?id=subpackages)
3. [python读写json文件 - Bigberg - 博客园](https://www.cnblogs.com/bigberg/p/6430095.html)
4. [Python读取JSON文件_fei347795790的博客-CSDN博客_python读取json文件](https://blog.csdn.net/fei347795790/article/details/94394963)
