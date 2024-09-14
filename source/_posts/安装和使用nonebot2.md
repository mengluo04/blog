---
layout: blog
title: 安装和使用nonebot2
date: 2024-08-12 16:24:28
tags:
- 机器人框架
categories:
- 教程
---
# 介绍
NoneBot2 是一个现代、跨平台、可扩展的 Python 聊天机器人框架（下称 NoneBot），它基于 Python 的类型注解和异步优先特性（兼容同步），能够为你的需求实现提供便捷灵活的支持。同时，NoneBot 拥有大量的开发者为其开发插件，用户无需编写任何代码，仅需完成环境配置及插件安装，就可以正常使用 NoneBot。
# 安装
**前提条件：安装了python3.9以上版本**
```bash
pip install nb-cli
```
# 创建项目
1、打开cmd
```bash
nb create
```
2、选择创建项目还是插件
![](https://file.mengluo.vip/blog/20240812163041.png)
3、选择bootstrap回车，要求输入项目名称，已英文字符开头
![](https://file.mengluo.vip/blog/20240812163152.png)
4、选择要安装的适配器，使用方向键移动，使用空格选中，选择onebot v11即可
![](https://file.mengluo.vip/blog/20240812163224.png)
5、选择要安装的驱动器，默认是fastapi，额外选择httpx和websockets
![](https://file.mengluo.vip/blog/20240812163352.png)
6、是否立即安装依赖，直接回车
7、是否创建虚拟环境，直接回车
8、程序会自动创建虚拟环境并安装依赖
9、选择默认插件，这里我们选择 echo 插件作为示例。这是一个简单的复读回显插件，可以用于测试你的机器人是否正常运行。
![](https://file.mengluo.vip/blog/20240812163704.png)
# 启动
在项目文件夹使用`nb run`启动程序，默认监听8080端口
 # 连接
 使用支持onebot协议的客户端连接到`IP:PORT/onebot/v11/ws`

 # 测试
 使用客户端给机器人qq所在群或者私聊发送`/echo hello`，能收到回复`hello`说明成功
