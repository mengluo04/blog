---
layout: blog
title: 使用uptime-kuma监听网站状态
date: 2024-10-12 13:47:09
categories: 
- 运维
tags:
- 网站监控
---
> 使用`uptime-kuma`监控网站状态
 
项目地址：https://github.com/louislam/uptime-kuma
## 安装
### docker
  `docker run -d --restart=always -p 3001:3001 -v uptime-kuma:/app/data --name uptime-kuma louislam/uptime-kuma:1`
### nodejs
  > nodejs版本要求：18 / 20.4

  1.下载代码
   ```bash
    git clone https://github.com/louislam/uptime-kuma.git
   ```
  2.进入项目文件夹
  `cd uptime-kuma`
  3.安装
  `npm run setup`

## 启动
- 方法1：node server/server.js
- 方法2：pm2 start server/server.js --name uptime-kuma 
> 需要安装pm2 
> npm install pm2 -g && pm2 install pm2-logrotate

## 访问
浏览器访问ip:3001,第一次需要设置管理员信息，登录后进入首页
## 配置
### 添加监控项
![](https://file.mengluo.vip/blog/20241012135709.png)
可选监控类型
![](https://file.mengluo.vip/blog/20241012135745.png)
![](https://file.mengluo.vip/blog/20241012135804.png)
### 添加通知类型
![](https://file.mengluo.vip/blog/20241012135921.png)
