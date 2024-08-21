---
layout: blog
title: js实现全部异步请求完再返回数据
date: 2024-08-20 18:21:46
categories: 
- 前端
tags:
- javascrapt
---
使用`Promise.all`实现
1、定义一个数组
```js
const arr = []
```
2、定义多个promise的方法
```js
const promises = new Promise((resolve, reject) => {
    setTimeout((resolve) => {
        resolve()
    }, 1000);
})
```
3、将promise方法添加到数组
4、使用`Promise.all`依次执行数组中的方法
```js
Promise.all(arr)
    .then((results) => {
        // results 是一个数组，每个元素对应一个请求的结果
    })
    .catch((error) => {
        console.error(error);
    });
```