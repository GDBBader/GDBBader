---


title: MIME
date: 2021-04-06 23:03:47
tags: [MIME,扩展名,魔术数字]
type:

---


# MIME是什么？

- **媒体类型**（通常称为 **Multipurpose Internet Mail Extensions** 或 **MIME** 类型 ）
- 是一种标准
- 表示文档、文件或字节流的性质和格式的标准


# 使用

通常是**浏览器**用来以某种MIME格式来识别文件内容的。例如：浏览器看到`text/html`就知道这个文件是html文件。


# 文件扩展名

这与操作系统根据文件扩展名来决定用怎样的方式打开文件类似。（Windows系统是根据文件扩展名，Unix/Linux 采用更精确的文件魔术编号（magic number）来确定文件类型。


# 文件中的魔术数字

> 魔术数字也会在文件中使用。在特定文件格式中加入固定数值和固定字符串，然后便可以通过检查文件是否包含这些数据来快速地识别文件格式。
例如：GIF文件开头会包含GIF89a（47 49 46 38 39 61）或GIF87a（47 49 46 38 37 61）这两种字符串。


---


# 参考

1. [MIME 类型 - HTTP | MDN](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Basics_of_HTTP/MIME_types)
2. [魔术数字 (程序设计) - 维基百科，自由的百科全书](https://zh.wikipedia.org/wiki/%E9%AD%94%E8%A1%93%E6%95%B8%E5%AD%97_%28%E7%A8%8B%E5%BC%8F%E8%A8%AD%E8%A8%88%29)
3. [文件扩展名 - 维基百科，自由的百科全书](https://zh.wikipedia.org/wiki/%E6%96%87%E4%BB%B6%E6%89%A9%E5%B1%95%E5%90%8D)
