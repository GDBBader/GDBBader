---

title: Vue.js中等号与.运算符的区别
date: 2021-03-08
tags: [uni-app,Vue.js]

---

## 一、看例子，直观

```javascript
methods: {
    add:function(){
        let temp = {}
        
        //用等号
        // temp = this.currentPerson
        
        //用点运算符
        temp.name = this.currentPerson.name;
        temp.age = this.currentPerson.age
        
        this.personList = this.personList.concat(temp)
    }
},
```

## 二、等号结果

![](https://gitee.com/qiebzps/pic/raw/master/img/20210309001531.gif#alt=%E7%AD%89%E5%8F%B7%E7%BB%93%E6%9E%9C)


## 三、.运算符结果

![](https://gitee.com/qiebzps/pic/raw/master/img/20210309001826.gif#alt=.%E8%BF%90%E7%AE%97%E7%AC%A6%E7%BB%93%E6%9E%9C)
