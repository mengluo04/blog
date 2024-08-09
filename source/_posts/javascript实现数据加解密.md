---
layout: blog
title: javascript实现数据加解密
date: 2024-08-09 15:43:27
tags:
- javascript
categories:
- 前端
---
# 安装
```bash
yarn add crypto-js
或
npm install crypto-js
```
# 引入
```js
import CryptoJS from "crypto-js";
```
# 定义加解密的key
```js
const key = '12345'
```
# 加密
```js
/**
 * 加密数据
 *
 * @param {any} text - 要加密的内容
 * @return {string} 加密后的内容
 */
export function aesEncrypt(text) {
  return CryptoJS.AES.encrypt(text, CryptoJS.enc.Utf8.parse(key), {
    mode: CryptoJS.mode.ECB,
    padding: CryptoJS.pad.Pkcs7,
  }).toString();
}
```
# 解密
```js
/**
 * 解密数据
 * @param text - 要解密的数据
 * @returns 解密后的数据
 */
export function aesDecrypt(text) {
  const decrypted = CryptoJS.AES.decrypt(text, CryptoJS.enc.Utf8.parse(key), {
    mode: CryptoJS.mode.ECB,
    padding: CryptoJS.pad.Pkcs7,
  });
  return decrypted.toString(CryptoJS.enc.Utf8);
}
```
# 使用
```js
// 加密
aesEncrypt("12345") // PHIY2w01Sn1KCVZcssWi+g==
// 解密
aesDecrypt("PHIY2w01Sn1KCVZcssWi+g==") // 12345
```