---
layout: blog
title: js实现将对象中指定的字段转换为数字类型
date: 2024-08-22 16:07:27
tags:
  - js
categories:
  - 前端
---
```js
/**
 * 将json中指定字段的值转换为数字类型
 * @param obj 需要转换的字段对象
 * @param keys 需要转换成数字的key
 * @returns 转换指定key为数字类型
 */
function convertKeysToNumbers(obj, ...keys) {
    return keys.reduce((newObj, key) => {
        if (obj.hasOwnProperty(key)) {
            const value = parseFloat(obj[key]);
            newObj[key] = isNaN(value) ? obj[key] : value;
        }
        return newObj;
    }, { ...obj });
}

// 示例调用
const originalObj = {
    a: '123',
    b: 'abc',
    c: '45.67',
    d: '8e2',
    e: 'Not a Number'
};

const result = convertKeysToNumbers(originalObj, 'a', 'c', 'd', 'e');
console.log(result);
// 输出: { a: 123, b: 'abc', c: 45.67, d: 800, e: 'Not a Number' }

```