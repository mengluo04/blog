---
layout: blog
title: vue中使用锚点定位
date: 2024-08-02 18:24:42
categories: 
- 前端
tags:
- vue
---
1、给子元素设置唯一ref或id
```html
<div class="title-box" v-for="item in arr" :key="item.id" :id="item.id"></div>
```
2、给父元素设置ref或者id
```html
<div ref="ItemBoxRef" id="itembox" ></div>
```
3、给元素绑定点击事件
```html
<div @click="scrollToSection(id)"><div>
```
4、实现方法
```javaScript
const scrollToSection = (id) => {
// 获取目标元素和父元素
const element = document.getElementById(id);
const scrollableParent = document.getElementById("itembox");
if (element && scrollableParent) {
    scrollableParent.scrollTop = element.offsetTop - 100;
}
};
```