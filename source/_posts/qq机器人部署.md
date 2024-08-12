---
layout: blog
title: qq机器人部署
date: 2024-08-12 15:56:13
tags:
- qq
categories:
- 教程
---
# qq官方机器人
## 地址
https://bot.q.qq.com/
## 使用方法：
  1、注册账号
  2、创建机器人
## 限制：
  1、个人只能在频道以及私聊使用，不能在q群使用
  2、限制很多

# Lagrange.OneBot
## 项目文档
https://lagrangedev.github.io/Lagrange.Doc/Lagrange.OneBot/
## 下载
从github的release页面 https://github.com/LagrangeDev/Lagrange.Core/releases 下载对应平台的可执行文件
## 运行
## 修改自动生成的配置文件`appsettings.json`
## 示例配置内容
  实际使用中多使用反向ws，作为服务端让客户端连接
  一般情况下只需要修改`Implementations`
```js
{
  "Logging": {
    "LogLevel": {
      "Default": "Information",  // 提 Issue 时请切换到 Trace
      "Microsoft": "Warning",
      "Microsoft.Hosting.Lifetime": "Information",
    },
  },
  "SignServerUrl": "https://sign.lagrangecore.org/api/sign/25765",
  "MusicSignServerUrl": "",
  "Account": {
    "Uin": 0,  // Uin 填写 0 以使用扫码连接
    "Password": "",  // 不填写密码以使用扫码连接
    "Protocol": "Linux",  // 使用 Linux 协议
    "AutoReconnect": true,
    "GetOptimumServer": true,
  },
  "Message": {
    "IgnoreSelf": true,  // 忽略 Bot 自身的消息
    "StringPost": false,
  },
  "QrCode": {
    "ConsoleCompatibilityMode": false,
  },
  "Implementations": [  // 服务实现 支持多链接
    // 反向websocket
    {
      "Type": "ReverseWebSocket",
      "Host": "127.0.0.1",
      "Port": 8080,
      "Suffix": "/onebot/v11/ws",
      "ReconnectInterval": 5000,
      "HeartBeatInterval": 5000,
      "HeartBeatEnable": true,
      "AccessToken": "",
    },
    // 正向websocket
    {
      "Type": "ForwardWebSocket",
      "Host": "127.0.0.1",
      "Port": 8081,
      "HeartBeatInterval": 5000,
      "HeartBeatEnable": true,
      "AccessToken": "",
    },
    // http post
    {
    "Type": "HttpPost",
    "Host": "127.0.0.1", // 可以填写前缀协议, 例如 `https://`
    "Port": 8082,
    "Suffix": "/",
    "HeartBeatInterval": 5000,
    "HeartBeatEnable": true,
    "AccessToken": "",
    "Secret": ""
    },
    // 正向http
    {
        Type: "Http",
        Host: "*",
        Port: 8083,
        AccessToken: "",
    }
  ],
}
```
# OpenShamrock
## 介绍
运行在安卓手机上，需要root，安装面具和lsposed
## 项目地址：https://whitechi73.github.io/OpenShamrock/guide/getting##started.html
## 下载
前往https://github.com/whitechi73/OpenShamrock/actions/workflows/build-apk.yml 下载开发板版本的apk文件
## 使用方法：参考https://whitechi73.github.io/OpenShamrock/guide/configuration.html#%E9%85%8D%E7%BD%AE%E6%96%87%E4%BB%B6 进行配置

# LLOneBot
## 介绍
作为ntqq的插件运行
## 文档地址
https://llonebot.github.io/zh-CN/guide/getting-started
## 安装
前往https://github.com/super1207/install_llob/releases 下载 exe
## 启动
双击运行即可，之后打开 QQ 的设置，看到了 LLOneBot 就代表安装成功了。

# go-cqhttp*
不推荐