---


title: Python路径处理
date: 2021-08-15 11:26
tags: [Python,Path,pathlib]
type:

---


## 一、pathlib库

> 面向对象的文件系统路径


## 二、使用

1. 
引入并创建Path对象
```python
from pathlib import Path
p = Path('./')
```


2. 
获取文件名后缀
```python
p.iterdir()
l = p.iterdir()
for i in l:
    print(i.suffix)
    print(i.suffixes)
```


3. 
获取不带后缀的文件名
```python
print(i.stem)
```


4. 
获取文件完整路径
```python
print(i.absolute())#文件绝对路径

print(p.absolute())#文件夹绝对路径
```


5. 
获取当前路径下的某一类文件
```python
list(p.glob('**/*.py'))
```




## 参考

1. [pathlib — Object-oriented filesystem paths — Python 3.9.6 documentation](https://docs.python.org/3/library/pathlib.html#pathlib.PurePath.suffix)
