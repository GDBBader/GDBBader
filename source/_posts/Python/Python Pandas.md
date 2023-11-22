---


title: Python Pandas
date: 2021-08-28 18:22:23
tags: [Python,Pandas]
type:

---


## 一、什么是Pandas


### 1.1 介绍

一个著名的、基于NumPy的数据处理库。使用前需要先引入

```python
import Pandas as pd
```


### 1.2 Series & DataFrames

![](https://gitee.com/qiebzps/pic/raw/master/img/20210815140551.png#alt=)


#### 1.2.1 创建DataFrames

```python
data = {'age': [14, 28], 'name': ['lilei', 'lihux']}
df = pd.DataFrames(data)

>   df
<   age   name
0   14  lilei
1   28  lihux
```


#### 1.2.2 自定义行名

```python
df = pd.DataFrame(data,index=['a','b'])


>   df
<   age   name
a   14  lilei
b   28  lihux
```


#### 1.2.3 访问行

```python
> 	df.loc['b']
< 	age        28
	name    lihux
	Name: b, dtype: object
	
>	df.loc['b'].age
< 	28
```


#### 1.2.4 访问列

```python
>	df['age']
< 	a    14
	b    28

>	df[['age','name']]
<	age   name
a   14  lilei
b   28  lihux
```


#### 1.2.5 切片

```python
>    df.iloc[1]
<    age        28
<    name    lihux
```


#### 1.2.6 条件

```python
<   df[(df['age']>20)&(df['age']<40)]
>   age   name
	b   28  lihux
```


### 1.3 读取数据

```python
df = pd.read_csv('./file.csv')

df.head()# 读取前几行（默认为5行）
df.tail()# 读取末尾几行
```


### 1.4 将DataFrame写入文件


#### 1.4.1 写入Excel

```python
df.to_excel('./writetoexcel.xlsx',sheet_name='sheet1')
```

![](https://gitee.com/qiebzps/pic/raw/master/img/20210815160102.png#alt=)


#### 1.4.2 写入CSV

```python
df.to_csv('./writetoexcel.csv')
```

![](https://gitee.com/qiebzps/pic/raw/master/img/20210815160050.png#alt=)

```python
# 不加索引
df.to_csv('./writetoexcel.csv',index=None)
```

![](https://gitee.com/qiebzps/pic/raw/master/img/20210815160913.png#alt=)

```python
# 不加列名
df.to_csv('./writetoexcel.csv',index=None)
```

![](https://gitee.com/qiebzps/pic/raw/master/img/20210815161140.png#alt=)

```python
# 向CSV中追加数据
df.to_csv('./writetoexcel.csv',mode='a')
```

![](https://gitee.com/qiebzps/pic/raw/master/img/20210815162301.png#alt=)


## 参考

1. [Learn Python for Data Science | Sololearn](https://www.sololearn.com/learning/1161)
2. [IO tools (text, CSV, HDF5, …) — pandas 1.3.1 documentation](https://pandas.pydata.org/docs/user_guide/io.html?highlight=writer)
3. [pandas.DataFrame.to_excel — pandas 1.3.1 documentation](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.to_excel.html)
4. [pandas.DataFrame.to_csv — pandas 1.3.1 documentation](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.to_csv.html)
