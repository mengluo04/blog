---
layout: blog
title: javascript生成指定位数的随机数
date: 2024-08-12 10:41:34
tags: javascript
categories:
- 前端
---
1、定义用于生成随机数的种子
```js
const characters = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789';
```
2、通过`Math.random()`生成随机数
3、示例代码
```js
function generateCaptcha(length = 4) {
    const characters = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789';
    let captcha = '';

    for (let i = 0; i < length; i++) {
        const randomIndex = Math.floor(Math.random() * characters.length);
        captcha += characters[randomIndex];
    }
    return captcha
}
```
4、调用
```js
generateCaptcha(8) // UDC4I2ID
```