---
layout: blog
title: python创建和使用虚拟环境
date: 2024-08-12 11:05:49
tags: 
- python
categories:
- 教程
---
**前置条件：已安装python3并配置了环境变量**
windows系统
1、在目标文件夹打开cmd或者通过cmd进入目标文件夹
2、使用`python -m venv venv`创建虚拟环境文件夹,第一个venv为python的模块，第二个venv为创建的文件夹名称
3、激活虚拟环境
```bash
venv\Scripts\activate
```
激活成功后路径前面会出现(venv) 表示处在虚拟环境
4、安装依赖
```bash
pip install xxx
```
5、也可以直接通过`venv\Scripts\pip`来使用虚拟环境的python来执行命令

linux/ubuntu系统
linux系统一般都自带python，如果没有，使用apt install python3来安装
1、`cd`到目标为止
2、使用`Python3 -m venv venv`创建虚拟环境
创建过程可能报错，绝大多数时候都是没有安装`python3-venv`模块，使用`apt install python3-venv`安装即可
3、激活虚拟环境
```sh
source venv/bin/activate
```
4、退出虚拟环境
```sh
deactivate
```