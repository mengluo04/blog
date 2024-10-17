---
layout: blog
title: 使用qrcode.vue在vue项目生成二维码
date: 2024-10-17 11:05:50
categories: 
- 前端
tags:
- vue
- 二维码
---
项目文档地址
https://github.com/scopewu/qrcode.vue
1、安装
```bash
yarn add qrcode.vue
```

2、使用
```js
import { ref } from 'vue'
import QrcodeVue from 'qrcode.vue'
const qrcode = ref("")
const size = ref(400)
```
```html
  <qrcode-vue :value="qrcode" :size="size" level="H"  />
```