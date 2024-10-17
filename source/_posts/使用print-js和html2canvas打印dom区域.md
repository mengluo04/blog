---
layout: blog
title: 使用print-js和html2canvas打印dom区域
date: 2024-10-17 11:12:28
categories:
  - 前端
tags:
  - vue
  - 打印
---

1、安装依赖

```bash
yarn add html2canvas print-js
```

2、页面使用

```js
import print from "print-js";
import html2canvas from "html2canvas";

const element = document.querySelector("#box");

if (element) {
  // 使用 html2canvas 将 DOM 转换为图片
  html2canvas(element).then((canvas) => {
    const imgData = canvas.toDataURL("image/png");
    console.log(dayjs().format("YYYY-MM-DD HH:mm:ss"));
    createMessage.success("生成完成，请点击页面的打印");
    // 直接将图片传递给 print-js 打印
    print({
      printable: imgData,
      type: "image",
      base64: true, // 指定 base64 格式
    });
  });
}
```

```html
 <div id="box">任意内容，比如文本，dom</div>
```
