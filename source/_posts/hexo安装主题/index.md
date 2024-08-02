---
title: hexo安装主题
date: 2024-08-02 13:37:28
categories: 
- 教程
tags: 
- hexo
---
# 主题名称：fluid
## 地址：https://github.com/fluid-dev/hexo-theme-fluid
# 安装
## 方法1：使用npm
适合Hexo 5.0.0 版本以上使用
- 安装
```bash
npm install --save hexo-theme-fluid
```
- 配置
在博客目录下创建 _config.fluid.yml，将主题的 _config.yml 内容复制进去
## 方法2：使用源码安装
- 下载源码到themes目录
- 重命名文件夹名称为fluid（如果是下载的zip文件，git clone的不需要）
# 配置
修改博客目录下的_config.yml
```bash
theme: fluid  # 指定主题
language: zh-CN  # 指定语言，会影响主题显示的语言，按需修改
```
# 创建关于页
```bash
hexo new page about
```
```markdown
---
title: about
layout: about
---

这里写关于页的正文，支持 Markdown, HTML
```