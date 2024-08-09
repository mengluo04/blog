---
layout: blog
title: javascript格式化时间日期
date: 2024-08-09 15:47:10
tags:
  - javascript
categories:
  - 前端
---

# 安装 dayjs

```bash
yarn add dayjs
或
npm install dayjs
```

# 引入 dayjs

```js
import dayjs from "dayjs";
```

# 定义默认格式化后的格式

```js
const DATE_TIME_FORMAT = "YYYY-MM-DD HH:mm:ss";
const DATE_FORMAT = "YYYY-MM-DD";
```

# 格式化为年月日

```js
export function formatToDate(date, format = DATE_FORMAT): string {
  return dayjs(date).format(format);
}
```

# 格式化为年月日时分秒

```js
export function formatToDateTime(date, format = DATE_TIME_FORMAT): string {
  if (!date) {
    return "";
  }
  return dayjs(date).format(format);
}
```
# 使用
```js
formatToDate() // 2024-08-09
formatToDate(1723189969829) // 2024-08-09
formatToDateTime() // 2024-08-09 15:52:49
formatToDateTime(1723189969829) // 2024-08-09 15:52:49

```