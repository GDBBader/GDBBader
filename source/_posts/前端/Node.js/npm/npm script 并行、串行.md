---

title: npm script 并行、串行
date: 2023-04-09 21:32
tags: [JavaScript,Node.js,npm]

---

## 一、前言
前端项目打包后经常需要zip打包备份、mstsc远程登录服务器来进行部署。总是需要在打包后有相同的后续步骤。可以通过npm script来简化操作。

<!-- more -->

## 二、npm script是什么？
简单来说，就是`package.json`中的`scripts`中的命令，如下：
```javascript
{
  // ...
  "scripts": {
    "build": "node build.js"
  }
}
```
如上的`node build.js`的意思就是当在package.json文件所在的文件夹中执行`npm run build`时就会将`npm run build`命令转换为`node build.js`来运行。另外可以通过`npm run`查看当前项目的所有`npm`脚本。

## 三、多条命令并行与串行
并行：用`&`间隔命令
串行：用`&&`间隔命令

```javascript
{
  // ...
  "scripts": {
    "clean": "rimraf ./dist && mkdir dist",
  }
}
```

```
// 以一命令会先执行rimraf ./dist后再执行mkdir dist
npm run clean
```

## 参考
1. [npm scripts 使用指南 - 阮一峰的网络日志 (ruanyifeng.com)](http://ruanyifeng.com/blog/2016/10/npm_scripts.html)