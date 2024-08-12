---
layout: blog
title: 使用idcard库进行身份证验证
date: 2024-08-12 10:46:19
tags:
  - javascript
categories:
  - 前端
---
项目地址：https://github.com/navyxie/idcard
1、安装

```bash
npm i idcard
# 或
yarn add idcard
```

2、引入

```js
var idCard = require("idcard");
// 或
import idCard from "idcard";
```

3、使用

- verify
  校验身份证合法性，返回 boolean 值

```js
idCard.verify("440882199100201232"); //false
idCard.verify("342201198910082425"); //true
```

- info
  获取身份证详细信息，返回一个 json 对象，key:valid 为 boolean 值，代表身份证是否合法

```js
idCard.info("440882199100201232");
```

身份证合法时返回的数据结构

```js
{
	valid: true,//身份证是否合法的标志
	gender: 'M',//M->男，F->女
	birthday: 19910210,//
	province: {
		code: '440000',//行政区域编码
		text: '广东省'
	},
	city: {
		code: '440800',
		text: '湛江市'
	},
	area: {
		code: '440882',
		text: '雷州市'
	},
	cardType: 1,//身份证类型，1->大陆，2->港澳台
	cardText: '大陆',
	address: '广东省湛江市雷州市',
	age:24,
	constellation:'水瓶'//星座
}
```

身份证非法时返回的数据结构

```js
{
  valid: false;
}
```
- generateIdcard
  随机生成一个合法身份证号码，返回身份证号码
```js
idCard.generateIdcard();//返回随机身份证号码
```
- getAge
  根据生日返回年龄
```js
idCard.getAge(19910210);//25 (调用时的日期：2016/03/23)
```