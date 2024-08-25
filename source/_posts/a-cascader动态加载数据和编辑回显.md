---
layout: blog
title: a-cascader动态加载数据和编辑回显
date: 2024-08-21 09:07:53
tags:
  - vue
categories:
  - 前端
---

## template

```html
<a-ascader
  v-model:value="value"
  :options="options"
  :load-data="loadData"
  change-on-select />
```

## script

### 动态加载数据

```js
const options = ref([]);
const value = rf("");
// 加兹数据方法
const loadQylbData = (selectedOptions) => {
  const targetOption = selectedOptions[selectedOptions.length - 1];
  targetOption.loading = true;

  fetchData({ pid: targetOption.id }).then((res) => {
    //  有下级，添加到children
    if (res.length) {
      targetOption.loading = false;
      targetOption.children = res.map((item) => {
        return { ...item, children: [], isLeaf: false };
      });
      options.value = [...options.value];
    } else {
      // 没有下级了，标记为最后一级
      targetOption.isLeaf = true;
      options.value = [...options.value];
    }
  });
};
```

### 编辑回显

```js
// 循环遍历将每个的请求添加到数组中
const promisesArr = value.value.map((id) => fetchData({ pid: id }));
// 依次执行每个promise
Promise.all(promises)
  .then((results) => {
    // results 是一个数组，每个元素对应一个请求的结果
    options.value = list2tree([].concat(...results));
  })
  .catch((error) => {
    console.error(error);
  });
```

### 将数组转为 tree 结构

```js
function list2tree(
  data: any[],
  id = "id",
  parentId = "pid",
  children = "children"
) {
  const map: any = {};
  const tree: any = [];
  data.forEach((item: any) => {
    map[item[id]] = item;
  });
  /**
   * 以原数据量循环拼装父，子级
   */
  data.forEach((item: any) => {
    const parent = map[item[parentId]];

    if (parent) {
      (parent[children] || (parent[children] = [])).push(item);
    } else {
      tree.push(item);
    }
  });

  return tree;
}
```
