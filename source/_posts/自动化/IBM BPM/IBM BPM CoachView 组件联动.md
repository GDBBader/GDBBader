---

title: IBM BPM CoachView 组件联动
date: 2022-07-26 10:38
tags: [BPM,CoackView]

---
-问：组件之间如何联动？例如两个下拉列表，省-市。
-答：可以通过在选中省之后通过JavaScript改变市的下拉列表的选项。
```javascript
${Single_Select1}.setItem(1, "abc", "abc");
${Single_Select1}.setItem(2, "def", "def");
```