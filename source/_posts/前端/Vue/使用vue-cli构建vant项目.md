---


title: 使用vue-cli构建vant项目
date: 2021-07-22 15:52:11
tags: [vue-cli,vant]
type:

---


## 一、vue-cli构建项目

1. 安装vue-cli

```
node -v
npm -v

npm install -g @vue/cli
```

2. 创建项目

```
vue create projectName
```

3. 运行开发服务器

```
npm run serve
```

## 二、安装vant

```
# Vue 2 项目，安装 Vant 2：
npm i vant -S

# Vue 3 项目，安装 Vant 3：
npm i vant@next -S
```


## 三、使用vant

1. 
导入所有组件（也可按需导入）
![](https://gitee.com/qiebzps/pic/raw/master/img/20210813001641.jpg#alt=)
![](https://gitee.com/qiebzps/pic/raw/master/img/20210813001648.jpg#alt=)

2. 
使用


```html
<van-button type="primary">主要按钮</van-button>
```


## 参考

1. [使用 Vue CLI 创建应用程序 - Learn | Microsoft Docs](https://docs.microsoft.com/zh-cn/learn/modules/vue-cli-components/3-vue-cli-exercise)
2. [Vant - 轻量、可靠的移动端组件库](https://vant-contrib.gitee.io/vant/#/zh-CN/quickstart)
